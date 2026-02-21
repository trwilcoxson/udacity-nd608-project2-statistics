# Statistical Analysis of Animal Longevity Across Vertebrate Classes

A comprehensive statistical analysis of the [AnAge database](https://genomics.senescence.info/species/) investigating whether maximum lifespan differs significantly across five major vertebrate classes (Mammalia, Aves, Teleostei, Reptilia, Amphibia), with a secondary analysis quantifying the allometric relationship between body size and longevity.

| | |
|---|---|
| **Author** | Tim Wilcoxson |
| **Course** | Project 2 — Data and Statistical Reasoning |
| **Date** | February 2026 |

## Key Findings

- **Kruskal-Wallis H-test:** H(4) = 193.5, p = 9.33 x 10^-41 -- longevity distributions differ significantly across vertebrate classes (n = 3,909 species)
- **Effect size:** epsilon-squared = 0.050 (small) -- class membership explains ~5% of variance in ranked longevity
- **ANOVA baseline comparison:** F(4, 3904) = 12.67, p = 3.03 x 10^-10, eta-squared = 0.013 -- same conclusion, but the non-parametric test detects ~4x more signal because rank-based analysis is robust to the extreme skewness
- **Post-hoc comparisons:** 9 of 10 class pairs differ significantly after Bonferroni correction; the exception is Aves vs. Mammalia (adjusted p = 0.275)
- **Allometric scaling:** Pearson r = 0.568 between log(body weight) and log(longevity) across 3,131 species

## Project Structure

```
project2_statistics/
├── analysis.ipynb                  # Complete Jupyter notebook with all analysis
├── generate_report.py              # Script to regenerate the PDF report
├── module_summary.pdf              # Statistical analysis report (PDF)
├── Statistical_Analysis_Report.pdf # Statistical analysis report (identical copy)
├── requirements.txt                # Python dependencies (pip freeze)
├── README.md                       # This file
├── .gitignore
├── data/
│   ├── anage_data.csv              # Original dataset (4,645 species x 31 variables)
│   ├── anage_data.txt              # Original TSV format
│   └── anage_cleaned.csv           # Cleaned dataset with derived columns
└── figures/
    ├── fig1_longevity_distribution.png  # Raw vs. log-transformed histograms
    ├── fig2_longevity_by_class.png      # Box plots by vertebrate class
    ├── fig3_weight_vs_longevity.png     # Allometric scatter plot with OLS
    ├── fig4_top_orders.png              # Top 10 taxonomic orders (sampling bias)
    └── fig5_qq_plots.png                # Q-Q normality plots
```

## Setup and Reproduction

```bash
git clone https://github.com/trwilcoxson/udacity-nd608-project2-statistics.git
cd project2_statistics
python -m venv venv
source venv/bin/activate
pip install -r requirements.txt

# Run the notebook
jupyter notebook analysis.ipynb

# Regenerate the PDF report
python generate_report.py
```

## Technologies

- **Python 3.12** -- NumPy, Pandas, SciPy, Matplotlib, Seaborn
- **Statistical methods** -- One-way ANOVA, Kruskal-Wallis H-test, Mann-Whitney U (post-hoc), Bonferroni correction, Levene's test, OLS regression, Pearson correlation
- **Report generation** -- fpdf2
- **Environment** -- Jupyter Notebook, venv

## Dataset Citation

de Magalhaes, J. P., & Costa, J. (2009). A database of vertebrate longevity records and their relation to other life-history traits. *Journal of Evolutionary Biology*, 22(8), 1770-1774. Data sourced from [HAGR AnAge Database](https://genomics.senescence.info/species/).

## References

- Lusa, L., et al. (2024). Initial data analysis for longitudinal studies to build a solid foundation for reproducible analysis. *PLoS ONE*, 19(5), e0295726.
- Midway, S. R. (2020). Principles of effective data visualization. *Patterns*, 1(9), 100141.
- Kruskal, W. H., & Wallis, W. A. (1952). Use of ranks in one-criterion variance analysis. *JASA*, 47(260), 583-621.
