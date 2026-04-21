# Assignment10B-DATA-607

## Overview

This repository contains the complete work for **Assignment 10B – More JSON Practice** for **DATA 607**.

The objective of this assignment is to:

* Retrieve **JSON data from the Nobel Prize API**
* Transform nested API data into **tidy data frames in R**
* Answer four **data-driven analytical questions**
* Demonstrate working with **real-world API data and nested structures**

---

## Repository Structure

```

Assignment10B-DATA-607/
│
├── 10B_Approach.qmd            # Assignment approach and planning
├── 10B_Codebase.qmd           # Main API retrieval, transformation, and analysis
├── 10B_LLM_Transcript.pdf     # ChatGPT interaction transcript
├── 10B_Video_Explainer.mp4    # 5-minute video presentation
├── README.md                  # Project documentation
└── LICENSE

```

---

## Technologies Used

* **R**
* **Quarto (.qmd)**
* **tidyverse**
* **httr2**
* **jsonlite**
* **ggplot2**
* **knitr**

---

## Data Source — Nobel Prize API

This assignment uses the official **Nobel Prize API** from the Developer Zone.

Main endpoints used:

* `https://api.nobelprize.org/2.1/nobelPrizes`
* `https://api.nobelprize.org/2.1/laureates`

### Key Challenge:

The API is **paginated**, meaning it returns limited records per request.  
A custom loop was implemented to retrieve **all pages**, ensuring the analysis uses the full dataset (~1000+ laureates).

---

## Data Preparation & Transformation

Since the API returns **nested JSON**, the data was transformed into tidy format using:

* `map_dfr()` to flatten nested structures
* extraction of relevant fields:
  * award year
  * category
  * birth country
  * affiliation country
* creation of derived variables:
  * **decade** for time-based analysis

### Final datasets created:

* `prizes_tbl` → prize-level data  
* `laureates_tbl` → individual-level data  
* `laureate_prizes_tbl` → linking laureates to prizes  
* `affiliations_tbl` → affiliation country data  

---

## Questions Answered

### Question 1 — Category Frequency
Which Nobel Prize categories have been awarded most frequently?

**Insight:**
The original five categories each have 125 awards, while Economic Sciences has fewer because it was introduced later.

---

### Question 2 — Awards Over Time
Which decades have had the highest number of Nobel Prize awards?

**Insight:**
Modern decades (1970s–2010s) show a stable pattern with ~60 awards per decade, while earlier decades have slightly fewer awards.

---

### Question 3 — Top Birth Countries
Which birth countries have produced the most Nobel laureates?

**Insight:**
The United States dominates with 296 laureates, followed by the United Kingdom and Germany.

---

### Question 4 — Cross-Country Movement (Analytical)
Which countries appear to lose the most Nobel laureates?

**Approach:**
Compared:
* **birth_country_now**
* **affiliation_country**

Cases where they differ represent cross-country movement.

**Insight:**
Countries like Germany, the UK, and Poland show the highest counts, while the **United States appears as the most common destination**, acting as a major hub for Nobel-level research.

---

## Validation & Reliability

To ensure accuracy, the following checks were performed:

* verified full dataset retrieval (pagination)
* checked row counts across datasets
* validated year ranges (1901–present)
* inspected missing values in key fields
* confirmed category consistency

---

## Key Insights

* Nobel Prize distribution is **highly structured and stable over time**
* A small number of countries dominate laureate production
* The **United States acts as a major global attractor** for Nobel-level talent
* JSON-based API data requires careful handling of:
  * nesting
  * missing fields
  * cross-field comparisons

---

## Reproducibility

The analysis is fully reproducible:

* Data is retrieved directly from the **live API**
* No external dataset files required
* All transformations and analysis are included in the `.qmd` codebase

---

## Links

* **GitHub Repository:**
  https://github.com/suffyankhan77/Assignment10B-DATA-607

* **RPubs Report:**
  https://rpubs.com/suffyankhan77/1423920

---

## Video Presentation

A 5-minute explanation of the assignment is included:

* `10B_Video_Explainer.mp4`

---

## LLM Usage

ChatGPT was used to:

* handle API pagination logic
* debug JSON parsing issues
* transform nested data into tidy format
* refine analytical questions and interpretations

Full transcript available in:

* `10B_LLM_Transcript.pdf`

---

## References

* Nobel Prize API Documentation: https://www.nobelprize.org/about/developer-zone-2/
* R Packages: tidyverse, httr2, jsonlite
```

