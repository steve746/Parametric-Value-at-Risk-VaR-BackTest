# Parametric VaR Backtesting

This repository contains the code, analysis, and results for a final project on **parametric Value at Risk (VaR) backtesting**. The project compares three volatility estimation methods for VaR calculation: **Simple Moving Average (SMA)**, **Exponentially Weighted Moving Average (EWMA)**, and **GARCH**. The study is carried out on a managed futures portfolio built from **WTI** and **Henry Hub** contracts with equal weights. :contentReference[oaicite:0]{index=0} :contentReference[oaicite:1]{index=1}

The main objective is to evaluate how these volatility models affect VaR estimation and backtesting performance. The analysis finds that **GARCH** performs best overall, followed by **EWMA**, while **SMA** tends to be less responsive to changing market conditions. :contentReference[oaicite:2]{index=2} :contentReference[oaicite:3]{index=3}

---

## Project Overview

Value at Risk (VaR) is one of the most common tools used in finance to measure downside risk. In this project, VaR is estimated for a portfolio with an initial value of **$10 million**, invested with equal weights in the second nearby contracts of **WTI crude oil** and **Henry Hub natural gas**. The study compares parametric VaR under three different volatility estimation approaches. :contentReference[oaicite:4]{index=4} :contentReference[oaicite:5]{index=5}

The project focuses only on the **parametric approach** to VaR. Under this framework, daily portfolio returns are assumed to be normally distributed, with one-day mean return taken as zero and volatility estimated using SMA, EWMA, or GARCH. :contentReference[oaicite:6]{index=6}

---

## Motivation

Correct estimation of VaR is important for financial institutions because it supports:

- capital requirement estimation
- risk management
- portfolio construction
- scenario analysis
- adaptation to market changes

These ideas are part of the motivation discussed in the report. :contentReference[oaicite:7]{index=7}

---

## Research Question

The main question studied in this project is:

**How do SMA, EWMA, and GARCH compare when used to estimate volatility for parametric VaR and VaR backtesting?** :contentReference[oaicite:8]{index=8}

---

## Methods

The project follows the standard parametric VaR procedure:

1. Mark the portfolio to market at time \(V_0\)
2. Assume one-day expected return is zero
3. Estimate one-day volatility \(\sigma_{1|0}\)
4. Compute parametric VaR using the normal approximation

The report uses the formula
\[
\hat r = -1.65 \sigma_{1|0} + \mu_{1|0},
\]
with \(\mu_{1|0} = 0\), and then calculates portfolio loss from the resulting one-day value forecast. :contentReference[oaicite:9]{index=9}

### Volatility Models

#### 1. Simple Moving Average (SMA)
SMA estimates volatility by equally weighting historical returns over a fixed window. The report notes that this approach can overestimate risk because all past returns are treated the same way. :contentReference[oaicite:10]{index=10} :contentReference[oaicite:11]{index=11}

#### 2. Exponentially Weighted Moving Average (EWMA)
EWMA assigns more weight to recent observations and less weight to older ones. In the report, EWMA is described as more responsive than SMA and better at adapting to recent volatility changes. :contentReference[oaicite:12]{index=12}

#### 3. GARCH
GARCH models conditional variance dynamically using past shocks and past variance. In this project, it gives the lowest volatility estimates among the three methods and the best overall performance in risk prediction and backtesting. :contentReference[oaicite:13]{index=13} :contentReference[oaicite:14]{index=14}

---

## Data

The project uses **WTI** and **Henry Hub** time series data from **Yahoo Finance**, with contract months taken in succession as an approximation to the second nearby rolling strategy. The portfolio is built with equal weights in the two assets. :contentReference[oaicite:15]{index=15}

The report also notes that this simplification was made because exact second nearby rolling data was not used directly. :contentReference[oaicite:16]{index=16}

---

## Results

The report shows that portfolio returns exhibit clear spikes, especially around 2020. The volatility plots for SMA, EWMA, and GARCH also show a strong spike during the 2020 oil market shock, when WTI moved dramatically. The discussion on page 11 notes that volatility estimates decrease from **SMA** to **EWMA** to **GARCH**. :contentReference[oaicite:17]{index=17}

### Main Findings

- **SMA** gives the highest volatility estimates and can overestimate risk
- **EWMA** is more responsive to recent price movements
- **GARCH** gives the lowest volatility estimates and the best predictive performance
- VaR for **WTI** is higher than for **Henry Hub** because WTI is more volatile
- Backtesting results are consistent with the RMSE comparison: **GARCH performs best**, followed by **EWMA**, then **SMA** :contentReference[oaicite:18]{index=18} :contentReference[oaicite:19]{index=19}

The report also states that a managed fund starting with **$10M** and staying long this portfolio would have declined by about **10%** over the period studied. This is illustrated by the compound portfolio return plot on page 15. :contentReference[oaicite:20]{index=20}

---

## Figures Included

The report includes the following visual outputs:

- snapshot of the WTI and NG data used
- portfolio daily returns
- volatility estimate using SMA
- volatility estimate using EWMA
- volatility estimate using GARCH
- VaR for individual assets
- portfolio VaR using SMA
- portfolio VaR using EWMA
- portfolio VaR using GARCH
- long portfolio performance :contentReference[oaicite:21]{index=21} :contentReference[oaicite:22]{index=22} :contentReference[oaicite:23]{index=23}

---

## Repository Structure

A clean structure for this repository could look like this:

```text
.
├── README.md
├── data/
├── R/
├── figures/
├── results/
└── report/
    └── STAT_649_Report.pdf
