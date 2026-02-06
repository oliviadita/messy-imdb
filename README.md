# IMDB Dataset Cleaning Project

## Overview
This project focuses on cleaning a real-world messy IMDB dataset containing encoding issues, inconsistent delimiters, malformed dates, noisy categorical values, and mixed numeric formats.

The goal is to transform raw movie data into clean, reliable, and analysis-ready datasets.

**Data Source:**  
https://www.kaggle.com/datasets/davidfuenteherraiz/messy-imdb-dataset

---

## Raw Dataset Summary
- Original shape: **(101, 12)**
- Expected: 100 movies, 11 columns
- Issues found:
  - Non-UTF8 encoding
  - Semicolon (`;`) delimiter
  - Messy and inconsistent headers
  - One empty column
  - One fully empty row

---

## Cleaning Steps

### Structural Fixes
- Handled non-UTF8 encoding and semicolon delimiters
- Standardized column names to `snake_case`
- Dropped empty column (`Unnamed: 8`)
- Removed one completely empty row

---

### Column-Level Cleaning

**`imdb_title_id`**
- Validated format (`tt` + 7 digits)
- No outliers or missing values

**`original_title`**
- Fixed encoding issues (e.g., Léon, WALL·E, Amélie)
- Validated unusual titles (e.g., *1917*)

**`release_year` & `release_date`**
- Separated year and full release date
- Fixed malformed dates
- Translated non-English month names
- Standardized to `YYYY-MM-DD`
- Manually corrected invalid dates using external verification

**`genre`**
- Normalized genre names
- Removed duplicates
- Applied One-Hot Encoding for analysis output

**`duration`**
- Filled one missing value using rounded mean

**`country`**
- Standardized country names
- Fixed typos and historical references
- Ensured consistent naming

**`content_rating`**
- Unified `Not Rated`, `Unrated`, and `Approved`
- Finalized as a single category: `Not Rated`

**`director`**
- Fixed mojibake and encoding issues
- Standardized name formatting

**Numeric Columns (`income`, `votes`, `score`)**
- Cleaned formatting and typos
- Converted to proper numeric types
  - Integer: income, votes
  - Float: score

---

## Outputs

Two final datasets are provided:

### 1. `cleaned_for_report.csv`
- Human-readable
- Accents preserved
- Country names in Title Case
- Suitable for reports and presentations

### 2. `cleaned_for_analysis.csv`
- Fully standardized `snake_case`
- No encoding artifacts
- Genre One-Hot Encoded
- Ready for analysis and machine learning

---

## Conclusion
This project demonstrates practical data cleaning techniques applied to real-world messy data, producing high-quality datasets suitable for both reporting and analytical workflows.
