# Alzheimer-s-Disease-Detection
Multi Feature Based Alzheimer’s Disease Detection from MRI Images

This repository contains the official implementation of the hybrid deep learning framework proposed in the paper “Multi Feature-Based Alzheimer’s Disease Detection From MRI Images.”
The model fuses deep features (Custom CNN + ResNet50) with handcrafted features (GLCM texture, morphological, and histogram descriptors) for multi-class Alzheimer’s classification.


Dataset

The dataset used is the publicly available Alzheimer’s MRI Dataset (4 Classes) from Kaggle.

Class Distribution (Total: 6,400 MRI slices)
	•	Non-Demented: 3,200
	•	Very Mild Demented: 2,240
	•	Mild Demented: 896
	•	Moderate Demented: 64

Each image is:
	•	Grayscale MRI slice
	•	~176×208 px → resized to 224×224
	•	Stored in class-named folders

Training settings:
	•	Epochs: 50
	•	Batch size: 32
	•	Optimizer: Adam (lr = 5×10⁻⁵, clipnorm = 1.0)
	•	Loss: Sparse categorical cross-entropy
	•	Hardware: NVIDIA Tesla T4 (Google Colab)

Deep and handcrafted features are fused using simple concatenation, which preserves complementary information with minimal overhead.


Returns:
	•	Predicted class (4 categories)
	•	Confidence score
	•	Optional visualization

Handcrafted Features Used:
	•	GLCM Texture Features: contrast, dissimilarity, homogeneity, energy, correlation, ASM
	•	Morphological Features: area, perimeter, eccentricity, solidity
	•	Intensity Histogram: 32 bins normalized

All handcrafted features are standardized before fusion.
