# Exploring Convolutional Layers – Lab 3

Laboratory 3 – Arquitectura Empresarial (AREP)

---

## 1. Introduction

This laboratory explores **Convolutional Neural Networks (CNNs)** as architectural components rather than black-box models.  
The goal is to understand how **convolutional layers introduce inductive bias** and why they are better suited than fully connected networks for image-based problems.

The work follows a structured process:
- Exploratory Data Analysis (EDA)
- Baseline non-convolutional model
- CNN architecture design
- Controlled experiments on convolutional layers
- Interpretation of results

---

## 2. Dataset Description

**Dataset:** Traffic Sign Images  
**Type:** RGB images  
**Image size (after preprocessing):** 64 × 64 × 3  
**Number of classes:** 52  
**Total images:** 5,683  
### Dataset Source

The dataset used in this project was obtained from Kaggle:

**Road Sign Detection Dataset**  
Source link: https://www.kaggle.com/datasets/andrewmvd/road-sign-detection/data

This dataset contains labeled images of road and traffic signs in various categories.  
It was downloaded locally and used for training and evaluation in this lab.

Because of size constraints, the full dataset is **not included** in this repository.  
Instructions to download the dataset are included here so the reviewer can obtain it if needed.

---

### Why this dataset is suitable for CNNs

This dataset is appropriate for convolutional neural networks because:

- It is image-based (2D spatial data)
- Local patterns such as edges, shapes, and symbols are important for classification
- Similar visual features appear at different spatial locations
- CNNs can exploit spatial locality and weight sharing effectively

This dataset is suitable for CNNs because:
- It is image-based (2D spatial data)
- Local patterns such as edges and shapes are important
- Similar features appear at different spatial locations
  <img width="1408" height="845" alt="image" src="https://github.com/user-attachments/assets/03f26701-4fc6-451c-a901-7a7a929ab5a4" />

---

## 3. Exploratory Data Analysis (EDA)

The EDA focuses on understanding the structure of the dataset.

### Main observations:
- The dataset presents class imbalance
- Images have different original resolutions
- RGB information is relevant for classification
- Visual patterns are consistent across classes

### Preprocessing steps:
- Resize images to 64×64
- Normalize pixel values to the range [0, 1]
- Convert images to tensors




---

## 4. Baseline Model (Non-Convolutional)

### Architecture:
- Flatten image into a 1D vector
- Fully connected (Dense) layers
- ReLU activation
- Softmax output layer

### Results:
- Training accuracy: ~65%
- Validation accuracy: ~63%

### Observed limitations:
- No spatial structure preservation
- No locality bias
- High number of parameters
- Weak robustness to small translations

This model serves as a reference point for comparison.

---

## 5. Convolutional Neural Network Design

A CNN was designed from scratch with intentional architectural decisions.

### Architecture:



### Design rationale:
- Small kernels capture local features
- Weight sharing reduces parameter count
- Pooling adds translation robustness
- ReLU introduces non-linearity

---

## 6. Controlled Experiment: Kernel Size

A controlled experiment was performed by modifying **only the kernel size**, keeping all other components fixed.

### Configurations tested:
- 3×3 kernels
- 5×5 kernels

### Final results:

| Kernel Size | Validation Accuracy | Parameters |
|------------|---------------------|------------|
| 3×3        | 0.0026              | 1,060,500  |
| 5×5        | 0.0096              | 1,069,460  |

### Interpretation:
- Larger kernels slightly improve performance
- They increase computational cost
- Smaller kernels remain more parameter-efficient

---

## 7. Interpretation and Architectural Reasoning

- **Why CNNs outperform dense models:** CNNs preserve spatial structure and learn local patterns.
- **Inductive bias introduced by convolution:** locality, weight sharing, and translation invariance.
- **When CNNs are not appropriate:** non-spatial data, very small feature vectors, or problems without local correlations.

---

## 8. Repository Structure

```text
ExploringConvolutionalLayers_lab3/
│
├── notebooks/
│   └── 01_lab.ipynb        
│
├── signals/
│   ├── DATA/
│   ├── TEST/
│   └── labels.csv
│
└── README.md


---

## 9. Conclusion

This laboratory demonstrates that convolutional layers are a **fundamental architectural choice**.  
Through comparison with a baseline model and controlled experiments, the benefits of inductive bias in CNNs become clear.

---

## Author Information

**Author:** Samuel Antonio Gil  
**University:** Escuela Colombiana de Ingeniería Julio Garavito  
**Course:** Arquitecturas Empresariales (AREP)  
**Laboratory:** Lab 3 – Exploring Convolutional Layers  
**Date:** February 2026

