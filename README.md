# Food Inspections BI Project

## Overview
This repository contains an end-to-end Business Intelligence (BI) implementation for food inspections in **Chicago** and **Dallas**. The project involves data extraction, profiling, cleaning, transformation, dimensional modeling, and visualization to analyze food inspection data across these cities.

## Technologies Used

![ER/Studio](https://img.shields.io/badge/ER%2FStudio-3E5064?style=for-the-badge&logoColor=white)
![Navicat](https://img.shields.io/badge/Navicat-FF6F00?style=for-the-badge&logoColor=white)
![Talend](https://img.shields.io/badge/Talend-FF6D70?style=for-the-badge&logo=talend&logoColor=white)
![Alteryx](https://img.shields.io/badge/Alteryx-1c7b9e?style=for-the-badge&logo=alteryx&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![SQL Server](https://img.shields.io/badge/SQL%20Server-AE2921?style=for-the-badge&logo=microsoft-sql-server&logoColor=white)
![Azure SQL](https://img.shields.io/badge/Azure%20SQL-0078D4?style=for-the-badge&logo=microsoft-azure&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=for-the-badge&logo=mysql&logoColor=white)
![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?style=for-the-badge&logo=power-bi&logoColor=black)
![Tableau](https://img.shields.io/badge/Tableau-E97627?style=for-the-badge&logo=tableau&logoColor=white)



## Project Steps
### 1. Data Extraction
- Downloaded datasets from the following open data portals:
  - **[Food Inspections - Chicago Data Portal](https://data.cityofchicago.org/Health-Human-Services/Food-Inspections/4ijn-s7e5/data_preview)**
  - **[Restaurant and Food Establishment Inspections - Dallas OpenData](https://www.dallasopendata.com/Services/Restaurant-and-Food-Establishment-Inspections-Octo/dri5-wcct/data_preview)**

### 2. Data Profiling
- **Profiling Tools:** Alteryx, Python (YData profiling)
- Key insights from profiling:
  - **Chicago dataset:** Contains 17 variables and 274,206 observations. Minimal missing values (1.8%), no duplicate rows.
  - **Dallas dataset:** Contains 114 variables and 78,984 observations. High percentage of missing cells (72.2%) and 42 duplicate rows.
  - Significant differences between schemas, especially in how violations are structured and the presence of critical columns such as `Risk` and `Inspection Score`.

### 3. Data Staging
- **Stage Tables:** Data from both cities was loaded into SQL Server/Azure SQL/MySQL with stage tables prefixed as `stg_`.
- **Profiling & Cleaning:**
  - Applied transformations such as date conversions, trimming, and merging columns where required.
  - Merged and cleaned violation data, particularly in the Dallas dataset, where violation information was spread across multiple columns.
  - Ensured consistent data types across datasets (e.g., ensuring dates are stored as `datetime` types).

### 4. Dimensional Modeling
- **Dimensional Model:** Designed using **ER/Studio** or **Navicat**. 
- **Fact and Dimension Tables:**
  - **Fact Tables:**
    - `FACT_INSPECTION_INFO`
    - `FACT_INSPECTION_VIOLATION`
  - **Dimension Tables:**
    - `DIM_RESTAURANT`
    - `DIM_VIOLATION`
    - `DIM_RISK`
    - `DIM_RESULT`
    - `DIM_GEO`
    - `DIM_SOURCE`
  - Added a calculated `Inspection Score` to the fact tables.

### 5. Data Loading & Transformation (Talend)
- **Talend:** Used to load data into the **integration schema**.
- Applied surrogate keys to all dimension tables and ensured proper transformation and data consistency.
- Performed detailed logging, including job runtimes and row counts for each table.

### 6. Data Visualization
- Dashboards were created to analyze key metrics related to food inspections using **Power BI** and **Tableau**.
- **Key Visualizations:**
  - Inspection results by `Inspection Type`, `Risk Category`, `Facility Type`, `Violations`, and `Business Name`.
  - Distribution of inspection scores across different facilities and locations.
  - Year-over-year trends in food inspection outcomes for Chicago and Dallas.

## Important Links
- **Chicago Food Inspections Data:** [Food Inspections - Chicago Data Portal](https://data.cityofchicago.org/Health-Human-Services/Food-Inspections/4ijn-s7e5/data_preview)
- **Dallas Food Inspections Data:** [Restaurant and Food Establishment Inspections - Dallas OpenData](https://www.dallasopendata.com/Services/Restaurant-and-Food-Establishment-Inspections-Octo/dri5-wcct/data_preview)

## Conclusion
This project provides a comprehensive BI solution to analyze food inspection data from Chicago and Dallas. By leveraging various tools and technologies, we successfully integrated disparate datasets, created a dimensional model, and provided actionable insights through interactive visualizations.
