# Bitcoin Trading Optimisation

> Searching for more robust moving-average trading rules with the Whale Optimisation Algorithm (WOA) and Particle Swarm Optimisation (PSO).

This experimental trading-bot project uses daily Bitcoin prices. It optimises a weighted moving-average crossover strategy and evaluates whether the parameters found during the training period remain effective on an unseen test period.

| At a glance | Details |
| --- | --- |
| Trading strategy | Buy and sell signals from HIGH / LOW weighted moving-average crossovers |
| Search methods | WOA, PSO, and Random Search |
| Baseline | Buy-and-Hold |
| Main search space | 14 parameters: SMA, LMA, and EMA weights, window lengths, and EMA decay factors |
| Evaluation | Five random seeds using the same 5,000-fitness-evaluation budget |

## What is explored

The main bot combines SMA, LMA, and EMA filters into a more responsive HIGH signal and a smoother LOW signal. A simplified version with only two SMA window parameters is also implemented to compare a low-dimensional search space with the 14-dimensional composite strategy. The project additionally examines the effect of different PSO population sizes under a fixed evaluation budget.

Each candidate strategy is backtested with an initial balance of USD 1,000, all-in buy/sell decisions, a 3% transaction fee, and forced liquidation at the end of the test period. Data before 2020 is used for optimisation; later data is used only for final evaluation.

## Repository contents

[`bitcoin-trading-optimization.ipynb`](bitcoin-trading-optimization.ipynb) contains the complete workflow: data preparation, signal construction, backtesting, optimiser implementation, experiments, and figure generation.

- [`data/BTC-Daily.csv`](data/BTC-Daily.csv): daily Bitcoin price data used in the experiments.
- [`outputs/experiment_summary.csv`](outputs/experiment_summary.csv): summary results for the experiment runs.
- [`outputs/figures/`](outputs/figures/): convergence, comparison, parameter-analysis, and trading-detail charts.
- [`bitcoin-trading-optimization-report.pdf`](bitcoin-trading-optimization-report.pdf): analysis report.
