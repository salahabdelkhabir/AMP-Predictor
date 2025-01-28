## 📑 Table of Contents
- [Abstract](#amp-predictor-project)
- [Project Repository Structure](#project-structure)
- [Detailed Methodology Steps](#detailed-methodology-steps)
  - [1. Data Collection](#1-data-collection)
  - [2. Data Preprocessing](#2-data-preprocessing)
  - [3. Feature Engineering](#3-feature-engineering)
  - [4. Model Development](#4-model-development)
  - [5. Model Evaluation](#5-model-evaluation)
  - [6. Model Selection](#6-model-selection)
  - [7. Model Deployment](#7-model-deployment)
- [📬 Contact](#contact)

## AMP Predictor Project
The AMP Predictor Project was developed as part of the course " BIO316 - Work-based Professional Project in Bioinformatics (I) ", conducted during the Fall 2024 semester in the Bioinformatics Department. This project aims to leverage machine learning techniques to predict Antimicrobial Peptides (AMPs), a critical tool in combating multidrug-resistant pathogens.

Integrating diverse bioinformatics datasets, the project applies rigorous preprocessing methods and advanced feature engineering to optimize model performance. A comprehensive evaluation of 26 machine learning algorithms identified LightGBM (LGBM) as the most efficient and accurate model, achieving a balanced performance across key metrics such as accuracy, MCC, and AUC. The project concludes with a user-friendly deployment interface using Gradio, enabling seamless prediction of AMP potential from peptide sequences.

<p align="center">
  <img src="https://github.com/user-attachments/assets/72188d48-0667-4fa9-a1e2-e91cad07bce3" width="300"/>
</p>

## Project Structure


## Project Structure

```

AMP-Predictor/

├── Dataset/

│   ├── AMP.fasta          # FASTA file with AMP sequences

│   └── Non-AMP.fasta      # FASTA file with Non-AMP sequences

│

├── Documentation/

│   ├── Final AMP Book.pdf # Comprehensive project book

│   ├── Preprint.pdf       # PDF version of the manuscript

│   └── Rollup.pdf         # Concise summary of key findings

│

├── Notebook/

│   └── AMP Predictor.ipynb # Jupyter notebook for analysis and prediction

│

└── README.md              # Project documentation (this file)

```


## Detailed Methodology Steps

<p align="center">
  <img src="https://github.com/user-attachments/assets/8ce285eb-9cf8-4ea1-b7cf-134e4ca30497" width="300"/>
</p>

### 1. Data Collection
- **Sources**: 
  - APD3: 2,619 AMPs
  - LAMP: 5,547 AMPs
  - CAMPR3: 10,247 sequences
  - DRAMP: 22,528 entries
- **Initial Processing**:
  - Combined datasets
  - Removed duplicates
  - Final dataset: 6,623 sequences

### 2. Data Preprocessing
1. **Sequence Filtering**:
   - Removed sequences < 10 amino acids
   - Eliminated sequences with unusual amino acids (B, Z, U, X, J, O, I, n, "-")

2. **Dataset Balancing**:
   - Equal distribution between AMP and non-AMP classes
   - Non-AMP dataset created from:
     - Real peptides from UniProt
     - Artificially generated sequences

3. **Quality Control**:
   - CD-Hit clustering with 99% threshold
   - Applied to both AMP and non-AMP classes separately

4. **Data Split**:
   - Training set: 80%
   - Testing set: 20%

### 3. Feature Engineering

1. **Amino Acid Analysis**:
   - Extracted information for 20 specific amino acids
   - Analyzed frequency and distribution
   
2. **Feature Selection**:
   - Applied Variance Threshold method
   - Threshold value: 0.1
   - Removed low-variance features

3. **Feature Importance**:

<p align="center">
  <img src="https://github.com/user-attachments/assets/0ef9d7db-e750-450c-963b-12651b150858" width="300"/>
</p>

   - Ranked amino acids by significance
   - Created unified data frame for both classes

### 4. Model Development
1. **Algorithm Selection**:
   - Tested 26 ML algorithms
   - Key models:
     - LightGBM
     - Extra Trees
     - Random Forest
     - KNN
     - SVC

2. **Model Parameters**:
   - LGBM Configuration:
     ```python
     params = {
         'boosting_type': 'gbdt',
         'num_leaves': 31,
         'learning_rate': 0.1,
         'min_child_samples': 20,
         'min_child_weight': 0.001
     }
     ```

### 5. Model Evaluation
1. **Performance Metrics**:
   - Accuracy
   - MCC (Matthews Correlation Coefficient)
   - Recall
   - AUC (Area Under Curve)
   - Precision
   - F1-score

| Classifier     | Accuracy | Balanced Accuracy | MCC  | Recall | AUC   | Precision | F1-score |
|----------------|----------|-------------------|------|--------|-------|-----------|----------|
| LGBM           | 0.92     | 0.92              | 0.83 | 90%    | 0.97  | 91%       | 0.92     |
| Extra Trees    | 0.92     | 0.91              | 0.84 | 88%    | 0.97  | 93%       | 0.92     |
| RF             | 0.91     | 0.90              | 0.81 | 87%    | 0.97  | 92%       | 0.91     |
| KNN            | 0.88     | 0.89              | 0.77 | 92%    | 0.94  | 81%       | 0.88     |
| SVC            | 0.89     | 0.89              | 0.77 | 87%    | 0.95  | 87%       | 0.89     |

2. **Results Analysis**:
   - **LGBM Performance**:
     - Accuracy: 92%
     - MCC: 0.83
     - Recall: 90%
     - AUC: 97%
     - Precision: 91%
     - F1-score: 92%

### 6. Model Selection

<p align="center">
  <img src="https://github.com/user-attachments/assets/f077f520-66e1-45cb-8139-b3c8b66a0bab" width="300"/>
</p>

1. **Comparison Criteria**:
   - Speed of prediction
   - Accuracy metrics
   - Computational efficiency

2. **Final Selection**:
   - **LGBM** selected as the best performer
   - Balanced performance across all metrics
   - Efficient computation time (0.51 seconds)

### 7. Model Deployment

**User Interface**:
   - Gradio API implementation
   - Simple sequence input interface
   - Direct AMP/non-AMP prediction output

<p align="center">
  <img src="https://github.com/user-attachments/assets/7891013a-1186-41f7-86e5-381be8a58c1c" width="650"/>
</p>

## 📬 Contact

For any questions or inquiries, feel free to reach out to the project leader:

**Salah Gamal Abdelkhabir**  
✉️ **Email**: [salahabdelkhabir@gmail.com](mailto:salahabdelkhabir@gmail.com)  
🔗 **LinkedIn**: [**Salah Gamal Abdelkhabir**](https://www.linkedin.com/in/sala7abdelkhabir/)

If you have any issues, bugs, or suggestions, please create an issue on the repository, and I will address it as soon as possible.
