# Random Survival Forest Risk Stratification for Pediatric Heart Transplantation

This repository contains the analysis code used in the study:

**“Risk Stratification for Graft Failure After Pediatric Heart Transplantation Using Random Survival Forests.”**

The project develops and evaluates a **Random Survival Forest (RSF)** model to predict graft failure among pediatric heart transplant recipients using **United Network for Organ Sharing (UNOS) / OPTN registry data**.

---

# Repository Structure

The analysis pipeline is organized into four Jupyter notebooks.

## HeartTX_1.ipynb  
**Data preprocessing and dataset preparation**

This notebook performs:

- Dataset loading
- Feature filtering  
  - removal of high-missingness variables  
  - removal of near-zero variance variables
- Feature engineering  
  - transplant center volume quartiles  
  - donor/recipient weight ratio
- Train–test split

---

## HeartTX_2.ipynb  
**Missing data imputation**

This notebook implements **Multiple Imputation by Chained Equations (MICE)** using the `miceforest` package.

Steps include:

- fitting imputation models on the training dataset
- applying the imputation model to the test dataset
- handling variables with extremely low missingness

---

## HeartTX_3.ipynb  
**Model development**

This notebook trains the prediction models.

### Models

- Random Survival Forest (primary model)
- Elastic-net Cox proportional hazards model (baseline comparison)

### Procedures

- hyperparameter optimization using **Optuna**
- cross-validation on the training set
- final model fitting on the full training dataset

---

## HeartTX_4.ipynb  
**Model evaluation and clinical analysis**

This notebook performs the evaluation analyses reported in the manuscript.

### Metrics

- Harrell's C-index
- IPCW C-index
- Time-dependent AUC (1 and 2 years)
- Brier scores
- Calibration curves

### Additional analyses

- Kaplan–Meier risk stratification
- Decision Curve Analysis (DCA)
- Permutation-based variable importance

### Figures generated

- calibration plots
- Kaplan–Meier curves
- decision curve analysis plots
- variable importance plots

---

# Data Availability

The dataset used in this study was obtained from the **UNOS/OPTN registry** under a Data Use Agreement.

Because of these restrictions, **patient-level data cannot be shared in this repository**.

Researchers may request access to the same dataset through the OPTN data request process:

https://optn.transplant.hrsa.gov/data/request-data/

Once access is granted, the provided code can be used to reproduce the analyses.

---

# Software Environment

The analysis was conducted in **Python**.

Main packages used include:

- pandas  
- numpy  
- scikit-learn  
- scikit-survival  
- lifelines  
- matplotlib  
- optuna  
- miceforest  
