# World Development Indicators (WDI) Exploratory Data Analysis

A comprehensive, reproducible data profiling and exploratory data analysis (EDA) pipeline utilizing Python and Pandas. This project processes world development indicators across three decades (1990–2020) to uncover global trends in health, wealth, education, and economic growth.

## 📌 Project Overview
This repository contains a structured workflow designed to clean, transform, aggregate, and analyze data from the World Development Indicators dataset. Using a student ID-derived pseudo-random seed, a personalized subset comprising 15% of the master dataset was generated to perform robust longitudinal data profiling.

## 🛠️ Technical Toolkit
* **Language:** Python 3.12+
* **Libraries:** Pandas, NumPy
* **Environment:** Jupyter Notebook (Conda Base Environment)
* **Dataset Focus:** Life Expectancy, GDP per Capita, Population Dynamics, School Enrollment, Internet Penetration, Health Expenditures, Literacy Rates, and Annual GDP Growth.

---

## 📂 Analysis Architecture & Pipeline Tasks

The analysis is broken down into 10 structured core tasks within the notebook:

### 📊 TASK 1: Dataset Overview & Structure
* **Dimensions:** Successfully validated the sample shape (1,232 rows × 10 columns).
* **Data Types:** Profiled attributes mapping `object`, `int64`, and `float64` schemas.
* **Temporal & Spatial Scope:** Identified a 31-year scope (1990–2020) spanning 261 unique sovereign nations and regional aggregates.

### 🔍 TASK 2: High-Threshold Filtering
* Isolated 21st-century observations ($\ge$ 2000), capturing 836 target rows.
* Extracted highly developed country-year cross-sections matching the strict criteria of $\text{LifeExpectancy} > 75$ and $\text{GDPperCapita} > \$30,000$.

### 🧮 TASK 3: Grouping & Chronological Aggregation
* Computed long-term static country averages for healthcare and economic indicators.
* Tracked global macroeconomic deceleration by computing average GDP growth rates grouped by decade (1990s: 2.65%, 2000s: 4.05%, 2010s: 3.01%).

### 🏔️ TASK 4: Statistical Extremes & Outliers
* **Max Health:** Identified San Marino (2018) as the maximum life expectancy threshold (85.095 years).
* **Min Wealth:** Captured Myanmar (1992) representing a severe historical economic collapse point ($58.89 GDP per capita).

### 📉 TASK 5: Distributional Consistency
* Validated observation volume per calendar year to ensure unskewed sampling.
* Tracked unique country representation across decades, confirming high contextual balance (~210 nations per decade).

### 🏷️ TASK 6: Feature Engineering & Discretization
* Transformed country scales by scaling population counts to millions (`PopulationMillions`).
* Built a custom multi-tier categorization feature (`GDPCategory`) split dynamically by the global median and 75th percentile thresholds (Low, Medium, High).

### 🕵️‍♂️ TASK 7: Sparsity & Missing Data Audits
* Profiled variable completeness, exposing significant missingness in `LiteracyRate` (76.14% missing) and `HealthExpenditure` (40.57% missing).
* Audited complete-case row consistency, revealing that only 158 rows possess zero missing values.

### 🧪 TASK 8: Dual-Condition Intersections
* Queried high-development subsets matching concurrent investments in health ($\text{HealthExpenditure} > 8\%$) and strong growth ($\text{GDPGrowth} > 3\%$).
* Linked these high-performing macroeconomic environments directly to elevated literacy baselines (~79.62%).

### 📐 TASK 9: Mathematical Multi-Dimensional Array Operations
* Leveraged native NumPy vectors to extract core descriptive statistics (IQR, boundaries, and metric ranges).
* Calculated a Pearson correlation coefficient ($r \approx 0.5744$), establishing a moderately strong, positive relationship between personal wealth and societal health outcomes.

### 🛑 TASK 10: Comparative Chronological Constraints
* Attempted a fixed, two-point chronological contrast between 1990 and 2020.
* Discovered a structural sampling constraint: because the stochastic selection process did not preserve matching dual-year records for identical nations, alternative analytical methods (such as moving averages or smooth interpolations) must be implemented for longitudinal tracking.

---

## 🚀 Quick Start & Installation

### Prerequisites
Ensure you have an active Conda or virtual Python environment established:
```bash
conda create -n wdi-env python=3.12 pandas numpy jupyter -y
conda activate wdi-env
