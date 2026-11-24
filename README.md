# AnchorCast

Official repository for **AnchorCast: Data-Scarce Time Series Forecasting via a Closed-Form Anchor and Evidence-Gated Structural Priors**.

> **Status:** The full source code, training scripts, and reproduction instructions will be released shortly.

## Overview

Forecasting under scarce training data often relies on heavy pretrained language or vision–language models, or on structural priors applied uniformly across every window. **AnchorCast** takes a lightweight, pretraining-free approach:

- **Closed-form ridge anchor:** Fits a channel-shared linear forecaster in closed form on instance-normalized windows and freezes it as a deterministic base forecast.
- **Evidence-gated structural priors:** Adds lightweight structural priors (calendar prior, continuation memory, nonlinear MLP residual, and cross-variable attention) as zero-initialized corrections, each scaled per window by a parameter-free evidence statistic.
- **Anchor fallback:** Registers the untrained anchor as epoch zero in early stopping so that trained priors are retained only if they improve validation error.

## Main Results

Averaged MSE / MAE across standard horizons ($H \in \{96, 192, 336, 720\}$, and $H \in \{96, 192, 336\}$ for ETTh1, ETTh2, and Traffic at 5% data):

| Dataset | 5% MSE | 5% MAE | 10% MSE | 10% MAE | Full MSE | Full MAE |
|---|---:|---:|---:|---:|---:|---:|
| ETTh1 | 0.415 | 0.428 | 0.418 | 0.433 | 0.408 | 0.424 |
| ETTh2 | 0.341 | 0.385 | 0.358 | 0.398 | 0.332 | 0.381 |
| ETTm1 | 0.358 | 0.382 | 0.355 | 0.380 | 0.353 | 0.379 |
| ETTm2 | 0.263 | 0.321 | 0.256 | 0.315 | 0.252 | 0.311 |
| Weather | 0.237 | 0.276 | 0.235 | 0.274 | 0.221 | 0.263 |
| ECL | 0.163 | 0.256 | 0.161 | 0.253 | 0.157 | 0.249 |
| Traffic | 0.408 | 0.281 | 0.414 | 0.282 | 0.402 | 0.277 |

## License

This project will be released under the MIT License.
