# STOR 390 Final Project: Balancing Innovation and Ethics in Heart Disease Diagnosis through Machine Learning

This README provides an overview of this repository which contains five files for the STOR 390 Final Project submission:
- Novel Analysis (RMD and HTML): Contains R code used to conduct the novel analysis portion of this project, which is to recreate/verify the author's methodology.
- Final Paper (RMD and PDF): Contains the final paper consisting of an analysis of methods and the normative consideration, as well as references.
- heart_data.csv: Also cited in the references section of my paper, this csv contains the dataset used in the novel analysis.

## Overview of Novel Analysis RMD Script
The R script performs a comprehensive analysis on the `heart_data.csv` dataset to predict heart disease presence using machine learning techniques like clustering, feature selection, and k-nearest neighbors (KNN). It evaluates the performance of standard and weighted KNN using metrics such as accuracy, precision, recall, and F1 score.

---

## Dataset: `heart_data.csv`
- **Description:**
  The dataset, located in the same directory as the R script, contains observations related to heart disease. It includes numeric features and a binary target variable `target` (0 or 1) indicating the absence or presence of heart disease.

- **Format:**
  The dataset is expected to be in CSV format with the following structure:
  - **Numeric features:** Various measurements such as cholesterol, blood pressure, etc.
  - **Target column:** A binary variable (`0` or `1`) indicating heart disease.

---

## Key Variables
- **`usePaperWeights`** (Boolean):
  - When `TRUE`, the script uses predefined feature weights from a referenced research paper.
  - When `FALSE`, the script calculates feature weights dynamically during analysis.

- **`usePaperKValues`** (Boolean):
  - When `TRUE`, the script uses optimal k values predefined in a referenced research paper.
  - When `FALSE`, the script calculates optimal k values dynamically through cross-validation.

---

## Prerequisites and Installation
Ensure R and the required packages are installed before running the script.

### Installing Required Packages
Uncomment and run the following lines in the script to install missing packages:
```r
# install.packages("caret", dependencies=TRUE)
# install.packages("ggplot2", dependencies=TRUE)
```
### Required Packages
- `caret`: For clustering and cross-validation.
- `ggplot2`: Sometimes needed as dependency to caret, may not be necessary

---

## Code Structure and Functionality
The script is divided into several sections:

### 1. Load Heart Data
- Loads the `heart_data.csv` dataset.
- Displays the first few rows to verify the structure.

### 2. Data Preprocessing
- Identifies and handles missing values.
- Removes outliers using the Interquartile Range (IQR) method.
- Converts the target column to a factor.
- Cleans the dataset for further analysis.

### 3. Clustering Features
- Computes a correlation matrix for numeric features.
- Groups features into clusters using k-means clustering.
- Maps each feature to a cluster.

### 4. Feature Selection Using Relief Algorithm
- Implements the Relief algorithm to calculate feature weights.
- Selects the best feature from each cluster based on weight.
- Normalizes calculated weights for interpretability.

### 5. Weighted KNN and Ten-Fold Cross-Validation
- Defines a custom weighted KNN function.
- Normalizes the dataset for distance-based methods.
- Performs ten-fold cross-validation to find the optimal k values for standard and weighted KNN.
- Allows using predefined k values or dynamically calculated ones.

### 6. Output Results
- Evaluates the models using an 80/20 train-test split.
- Generates confusion matrices for both standard and weighted KNN.
- Calculates and displays performance metrics:
  - Accuracy
  - Precision
  - Recall
  - F1 Score
  - Area Under Curve (AUC)

---

## Notes
- The Relief algorithm may take time (a few minutes at least) to run due to it iterating over each data point
