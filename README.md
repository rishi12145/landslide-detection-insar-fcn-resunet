# Landslide Detection using InSAR Data with FCN and ResUNet Models

## Overview

This project focuses on detecting landslide-prone regions using multi-temporal InSAR (Interferometric Synthetic Aperture Radar) data. Two deep learning models, Fully Convolutional Network (FCN) and ResUNet, are implemented and compared for semantic segmentation.

The goal is to analyze model performance and identify the most suitable architecture for this task.

---

## Dataset

The dataset consists of multi-temporal InSAR interferograms, organized into:

- 6-day interval
- 12-day interval
- 18-day interval

Each sample includes:
- Coherence image
- Phase image
- Ground truth mask

### Input Representation

Phase values are transformed into:
- cos(phase)
- sin(phase)

Final input channels:
- Coherence
- cos(phase)
- sin(phase)

---

## Models

### Fully Convolutional Network (FCN)
- Backbone: ResNet50
- Modified output layer for binary segmentation
- Simple and efficient architecture

### ResUNet
- Encoder-decoder structure
- Residual connections
- Designed for deeper feature extraction

---

## Training Strategy

- Loss Function: BCEWithLogitsLoss
- Optimizer: Adam
- Learning Rate Scheduler: ReduceLROnPlateau
- Early Stopping applied
- Metrics tracked per epoch:
  - Loss
  - Accuracy
  - Precision
  - Recall

---

## Evaluation Metrics

The models are evaluated using:

- Accuracy
- Precision
- Recall
- F1 Score
- Dice Score
- Intersection over Union (IoU)

---

## Results

### FCN Performance
- Accuracy: ~0.99
- F1 Score: ~0.87
- Dice Score: ~0.87
- IoU: ~0.78

### ResUNet Performance
- Accuracy: ~0.98
- F1 Score: ~0.78
- Dice Score: ~0.78
- IoU: ~0.65

### Observation

FCN outperforms ResUNet across all metrics for this dataset.  
The simpler architecture of FCN allows better generalization, while ResUNet requires more data and tuning to reach optimal performance.

---

## Comparison with Paper

The implemented models achieve better performance than the baseline results reported in the reference paper.

Key improvements include:
- Improved phase representation using cosine and sine
- Combined multi-temporal data usage
- Optimized training strategy

---

## Visualization

The project includes visualization of:
- Input images
- Ground truth masks
- Predicted masks
- Heatmaps
- Overlay results

These help in qualitative evaluation of model performance.

---

## Conclusion

- FCN is more effective for this dataset
- Model complexity does not always guarantee better performance
- Proper data representation and training strategy significantly improve results

---

## Future Work

- Experiment with hybrid loss functions (Dice + BCE)
- Explore attention-based architectures
- Train on larger datasets for improved generalization

---

## Repository Structure

- ├── data/
- ├── notebooks/
- ├── models/
- ├── results/
- ├── README.md


---

## Requirements

- Python
- PyTorch
- NumPy
- Matplotlib
- scikit-learn

---

## Author

Rishikesh Gopal
