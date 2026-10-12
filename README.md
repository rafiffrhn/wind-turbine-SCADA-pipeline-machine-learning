# End-to-End Wind Turbine SCADA Pipeline & Machine Learning

## Project Description
This project is a comprehensive **Full-Stack Data** portfolio integrating **Data Engineering** and **Data Science**. Utilizing wind turbine IoT sensor data (SCADA), this project architects an automated end-to-end data pipeline: from raw data extraction, anomaly cleansing, and Data Warehouse storage, to Business Intelligence visualization and the development of predictive Machine Learning models.

## Tech Stack & Tools
- **Programming Language:** Python 3
- **Data Engineering & ETL:** Prefect (Orchestration), DuckDB (Data Warehouse), PyArrow (Parquet)
- **Data Science & ML:** Scikit-Learn (Random Forest Regressor & Classifier), Pandas, NumPy
- **Visualization:** Matplotlib, Seaborn, Power BI Desktop
- **Version Control:** Git & GitHub

## Struktur Repositori
```text
├── data/                    # Data storage (Processed / Parquet)
├── images/                  # Image assets for documentation & dashboards
├── notebooks/               # Data Science experimentation & modeling
│    ├── prediksi_daya.ipynb         # Regression Model (Active Power Prediction)
│    └── predictive_maintenance.ipynb # Classification Model (Machine Status Detection)
├── Perfect.py               # Automated ETL pipeline orchestration script
├── transform.py             # Transformation logic & anomaly handling
├── load.py                  # Data loading script to DuckDB
└── README.md
```
## Part 1: Data Engineering (Automated Pipeline)
The pipeline is orchestrated using Prefect with the following stages:
- **Extract & Clean:** Ingests CSV data, cleanses anomalous values (e.g., negative power output), and applies time-partitioning.
- **Feature Engineering:** Generates a turbine_status feature (Normal vs. Maintenance/Error) based on wind speed and active power business logic.
- **Load:** Automatically loads the structured data into Parquet formats and DuckDB for optimized storage.

## Part 2: Data Sciennce & Machine Learning
In this phase, the cleaned data is explored further using Jupyter Notebooks located in the notebooks/ directory:
- **Regression Model (regression_daya.ipynb):** Builds a RandomForestRegressor to predict active power output (active_power_kw) based on wind speed. This model achieved an outstanding $R^2$ accuracy score of 96.15%.
- **Classification Model (classification_predmaintenance.ipynb):** MDevelops a RandomForestClassifier to detect machine anomaly status (Predictive Maintenance) and analyzes Data Leakage mitigation to ensure robust real-world model performance.

## Visualization & Dashboard
- **Power BI:** Utilized for interactive monitoring of wind turbine operational performance.
- **Matplotlib & Seaborn:** Employed for Machine Learning model evaluation (e.g., actual vs. predicted scatter plots and Feature Importance analysis).

## Cara Menjalankan Proyek
**1. Clone this repository:**
```bash
git clone https://github.com/rafiffrhn/end-to-end-data-pipeline-1.git
cd end-to-end-data-pipeline-1
```
**2. Install requirements**
```bash
pip install -r requirements.txt
```
**3. Start the Prefect server:**
```bash
python -m prefect server start
```
The Prefect Dashboard can be accessed via http://127.0.0.1:4200

**4. Run the Automated Pipeline (Open a second terminal):**
```bash
python Prefect.py
```
This script will execute the automated ETL pipeline (Transform & Load) based on the scheduled configuration in the code. You can also open the Jupyter Notebooks inside the notebooks/ folder to view the AI model experiments.
