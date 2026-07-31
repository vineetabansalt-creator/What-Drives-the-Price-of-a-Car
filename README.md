# What Drives the Price of a Car?

## Summary of Findings

We analyzed ~346,000 cleaned used-vehicle listings (from an original 426,880-row Kaggle dataset) to identify what drives resale price for a used car dealership fine-tuning its inventory.

**Top drivers of price, in order of impact:**

1. **Age and mileage dominate.** These two factors alone explain most of the predictable variation in price — every additional year and every additional mile steadily erodes value.
2. **Diesel fuel and higher cylinder counts add value** — these vehicles (often trucks/larger SUVs) command a real premium.
3. **Drivetrain matters** — 4WD and FWD vehicles tend to outsell RWD equivalents.
4. **Brand reputation carries a premium or discount** beyond specs alone — Tesla, Porsche, Lexus, and Audi sell for more; Fiat, Mitsubishi, Kia, and Hyundai sell for less, holding other factors constant.
5. **Condition and title status matter, but less than expected**, likely due to inconsistent self-reporting across sellers.

**Modeling approach:** We compared Linear Regression, Ridge, and Lasso (all regularization-tuned via `GridSearchCV`) against a Random Forest. All three linear models perform almost identically (R² ≈ 0.70, MAE ≈ $5,500), while the Random Forest clearly outperforms them (R² ≈ 0.82, MAE ≈ $3,700), indicating meaningful non-linear effects and feature interactions in what drives price.

**Recommendations for inventory strategy:**
- Prioritize newer, lower-mileage vehicles — the single strongest lever on resale value.
- Favor diesel and higher-cylinder trucks/SUVs with 4WD.
- Weight brand reputation into acquisition costs — pay more for brands that resell at a premium.
- Use the model as a pricing sanity-check, not a replacement for expert judgment.

## Repository Contents

- [`prompt_II.ipynb`](./prompt_II.ipynb) — full analysis notebook, following the CRISP-DM framework (Business Understanding → Data Understanding → Data Preparation → Modeling → Evaluation → Deployment).
- `data/vehicles.csv` — the raw dataset (Kaggle used-car listings, ~426K rows).
- `images/` — supporting images used in the notebook (CRISP-DM diagram, etc.).

## Data

Sourced from the [Kaggle Used Cars Dataset](https://www.kaggle.com/austinreese/craigslist-carstrucks-data), reduced to 426,880 rows for tractability.
