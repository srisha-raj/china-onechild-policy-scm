# Did the One-Child Policy Actually Work?

### A Synthetic Control Analysis of China's 1979 Fertility Policy

**Author:** Srisha Raj\
**Method:** Synthetic Control Method (Abadie, Diamond & Hainmueller, 2010)\
**Data:** World Bank World Development Indicators

------------------------------------------------------------------------

## The Question

China's fertility rate was already falling sharply before 1979, from 6.1 births per woman in 1960 to 2.8 by the time the One-Child Policy launched. H**ow much of China's fertility decline was caused by the policy, versus economic and demographic forces already in motion?**

This project investigates that question along two outcomes:

1.  **Total Fertility Rate (TFR)**: did the policy dampen fertility below where structural development trends would have taken it anyway?
2.  **Sex Ratio at Birth**: did the policy change *how* families made fertility decisions, specifically by intensifying son preference under a one-child constraint?

TFR can fall for many structural reasons that have nothing to do with government policy. Sex ratio at birth, by contrast, holds close to a stable biological baseline (\~1.03–1.06) almost everywhere absent selective behavior. A sustained deviation would be stronger evidence of policy-driven change.

------------------------------------------------------------------------

## Method

The **Synthetic Control Method** (Abadie et al., 2010) constructs a counterfactual "Synthetic China" through a weighted blend of donor countries whose pre-1979 trajectory most closely matches China's across fertility, GDP, urbanization, and child mortality. After 1979, the gap between real China and Synthetic China estimates the policy's effect.

Donor pool: Thailand, South Korea, Turkey, Pakistan, Philippines, Sri Lanka, Morocco, Tunisia, Brazil, Mexico. Countries were excluded if their governments ran fertility campaigns beginning in the late 1970s.

Both outcomes use the identical predictor set and optimization window (1969–1978), so any difference in results reflects the outcome, not a different modeling choice. Placebo tests (Abadie et al. permutation inference) are run for both outcomes.

------------------------------------------------------------------------

## Findings

**Total Fertility Rate:**\
Synthetic China (76.8% Thailand, 21.4% South Korea) declines at nearly the same rate as real China after 1979. The average post-treatment gap is +0.054 TFR, which is essentially null and in the opposite direction of the hypothesis. In the placebo test, China ranks 11th of 11 units by post/pre RMSPE ratio (pseudo p ≈ 1.00). The fertility transition appears to have been largely structural.

**Sex Ratio at Birth:**\
Synthetic China (80.9% Thailand, 9.3% Philippines, 9.1% Pakistan) matches China's pre-1979 sex ratio almost exactly (RMSPE = 0.002). After 1979, real China diverges upward by an average of +0.073. China ranks 2nd of 11 in the placebo test (pseudo p ≈ 0.18), close to the ceiling of what an 11-unit permutation test can detect.

\
The One-Child Policy does not appear to have meaningfully accelerated China's fertility decline beyond what modernization was already producing. But it does appear to have changed the *terms* on which those births happened, particularly intensifying son-selective behavior in a way that structural development forces alone cannot explain.

------------------------------------------------------------------------

## Repo Structure

```         
china-onechild-policy-scm/
│
├── README.md
├── china_onechild_scm.ipynb     ← full analysis, runs top to bottom
│
├── data/
│   ├── fertility_rate.csv
│   ├── sex_ratio.csv
│   ├── gdp.csv
│   ├── urban_population_pct.csv
│   └── child_mortality.csv
│
└── figures/
    ├── scm_tfr_results.png
    ├── scm_sexratio_results.png
    └── placebo_comparison.png
```

------------------------------------------------------------------------

## How to Run

``` bash
pip install pysyncon statsmodels
jupyter notebook china_onechild_scm.ipynb
```

All data is included in `data/`. The notebook installs dependencies automatically if not present.

------------------------------------------------------------------------

## Next Steps

Province-level analysis would allow for a clearer isolation of the policy's implementation as China's provinces varied significantly in when and how strictly the policy was enforced.

Additional outcomes worth examining: female labor force participation, household size, and reported family conflict.

------------------------------------------------------------------------

*Data: World Bank WDI (accessed July 2025) · Indicators: SP.DYN.TFRT.IN, SP.POP.BRTH.MF, NY.GDP.MKTP.CD, SP.URB.TOTL.IN.ZS, SH.DYN.MORT*
