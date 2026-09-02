# Forecasting Atmospheric CO₂ with Gaussian Processes

A Gaussian Process regression project modeling and forecasting atmospheric CO₂ concentration using
NOAA's continuous in-situ measurement record from the Mauna Loa Observatory (1974–2025).

**Notebook:** [`CO2_Gaussian_Process_Forecasting.ipynb`](./CO2_Gaussian_Process_Forecasting.ipynb)

## What's inside

- Data cleaning of NOAA GML's raw monthly CO₂ product (`data.txt`)
- Kernel intuition building with `scikit-learn`'s Gaussian Process API (RBF, ExpSineSquared, WhiteKernel,
  RationalQuadratic)
- Progressive model building: single kernels → an additive trend + seasonal model → a fine-tuned four-component
  kernel (RBF + quasi-periodic + RationalQuadratic + noise), matching the classic Rasmussen & Williams treatment of
  this dataset
- Quantified forecast evaluation against held-out future data, including a multi-year-ahead accuracy benchmark
- A data-driven investigation of whether the 2020 COVID-19 emissions slowdown left a detectable signature in the
  atmospheric CO₂ record

## Key results

- The tuned four-component kernel cuts test-set RMSE by roughly two-thirds versus a naive additive kernel.
- Fit on data through 2019 only, the model's forecast stays accurate (MAE < 0.5 ppm) for at least six years beyond
  its training window when checked against real, subsequently-observed data.
- No detectable slowdown appears in the atmospheric CO₂ growth rate during 2020 — its year-over-year growth sits
  within the normal range seen in surrounding years.

## Data source

NOAA Global Monitoring Laboratory, continuous in-situ CO₂ measurements at Mauna Loa, Hawaii.
Pétron, G., et al. (2026). *Atmospheric Carbon Dioxide Dry Air Mole Fractions from continuous measurements at Mauna
Loa, Hawaii...* [https://doi.org/10.15138/yaf1-bk21](https://doi.org/10.15138/yaf1-bk21)

## Running it

```
pip install numpy pandas matplotlib scikit-learn jupyter
jupyter notebook CO2_Gaussian_Process_Forecasting.ipynb
```
