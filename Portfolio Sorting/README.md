# Portfolio Sorting

#### Author: Rain Luo
---
## Table of Contents
1. Introduction & Motivation
2. What is Portfolio Sorting
3. Methodologies

---

## 1. Introduction & Motivation

This report provides an analysis of financial data for the **Dow Jones Industrial Average**.  
The data were obtained from **WRDS/FactSet**.

In my most recent semester, in my finance class, I was introduced to a finance paper that discusses [return anomalies](https://academic.oup.com/rfs/article-abstract/33/5/2019/5236964?login=false). The authors points out 453 different factors that disproportionately affects return. Many of the factors fails the T-stat test, however there are 18% of the factors that is statistically significant at the 95% significance level. I chose 6 factors from the paper and tried to explore them to form hedge portfolio. 

As well, I came across actively-managed ETFs like BlackRock's USMV, which trackes stocks listed on the US market with minimum volatility. I wanted to see if I create some sort of factors based ETF, what would the turnover rate, return, alpha, Sharpe ratio be. 

# 2. Portfolio Sorting in a nut shell
Portfolio sorting is a **non-parametric technique** that groups securities into portfolios based on one (or more) firm characteristics—size, value, momentum, beta, etc.—to study how those characteristics relate to future returns. It is the workhorse of modern empirical asset-pricing papers because it is intuitive, transparent, and easy to replicate. 

---

## Why Use Portfolio Sorts?

| Purpose                              | What the sort reveals                               |
| ------------------------------------ | --------------------------------------------------- |
| **Return‐predictive power**          | Whether a characteristic forecasts returns (e.g., size, book-to-market). |
| **Factor construction**              | Turning different spreads into a tradable risk factor. |
| **Robustness & visualization**       | Monotonic patterns across deciles are easy to see and explain. |
| **Model testing**                    | Compare CAPM or multi-factor alphas on sorted portfolios. |

---

## Factors Chosen

1. [High-minus-low](https://www.investopedia.com/terms/h/high_minus_low.asp): Long firms with high book-to-market ratio and short firms with low book to market ratio
2. Small-minus-big: Long firms with small size and short firms with larger size.
3. Momentum: Long firms with higher price momentum and short firms with low price momentum
4. Beta: Long firms with lower beta, and short firms with higher beta.
5. Idiosyncratic volatility (ivol): Long firms with higher ivol and short firms with low ivol.
6. Price to earning (ep): Long firms with low E/P and short firms with high E/P.

---

## 3. Methodologies

After getting data from WRDS/FactSet, I would perform some cleaning and merging them into a giant dataframe. From there, I would be sorting the dataframe into different quantiles, long/short the 1st/5th quantile and tracking the return over a 30 year period.

Here are some results:
| Variable | CAMP Alpha  | t-stat | FF-4 Alpha  | t-stat | Sharpe |
|----------|---------------|----------------|---------------|----------------| --------|
| ep    | 0.0039        | 0.85       | 0.0050        | 1.12         | 0.061|
| lnsize    | 0.0230        | 6.71         | 0.0237        | 6.85         |0.40|
| bk2mkt    | -0.0044       | -1.22        | -0.0050       | -1.37        |-0.077|
| MOM    | -0.0014       | -0.30        | -0.0012       | -0.27        | -0.011|
| beta    | -0.0118       | -2.33        | -0.0117       | -2.29        |-0.13|
| ivol    | 0.0163        | 3.43         | 0.0163        | 3.38         |0.20|

---
## 4. How it was made:
List of technologies used (Python libraries)
1. Pandas
2. Numpy
3. Seaborn
4. Matplotlib
5. Scipy

TODO: discuss fama macbeth model.

