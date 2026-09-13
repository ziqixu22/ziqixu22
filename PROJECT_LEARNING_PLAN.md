# Flagship Project Learning & Interview Plan

This is the study path behind the portfolio. The goal is not to memorize a README. For every project, be able to explain: **the decision, the data, the baseline, the validation design, the result, the limitation, and what you would do next.**

## 1. E-commerce Product Analytics & Experimentation

**Core story:** Separate descriptive product-health analysis from causal treatment measurement; use each for the question it can actually answer.

Learn in this order:

1. Reproduce the data cleaning and define completed sales versus cancellations.
2. Write the SQL for monthly revenue, customer cohorts, retention, and repeat purchase.
3. Explain the experiment validity checks: allocation, sample-ratio mismatch, and guardrails.
4. Calculate absolute lift, relative lift, confidence intervals, and power from the stored results.
5. Explain why a 14M-row experiment can give a tiny but precise effect—and why the rollout decision still needs economics.
6. Explain why segment heterogeneity is a follow-up hypothesis, not an immediate targeting claim.

**Interview prompt:** “How would you decide whether to launch a checkout intervention?”  
**Strong answer:** start with a pre-specified primary metric and guardrails; validate assignment; report effect size and uncertainty; translate to economics; validate any exploratory segment finding in a new experiment.

## 2. Production Fraud Risk Decision System

**Core story:** Fraud is an operating decision under class imbalance and asymmetric cost, not an accuracy contest.

Learn in this order:

1. Explain why random splits leak future patterns and why the project uses chronological splits.
2. Compare logistic regression to LightGBM: interpretability baseline versus nonlinear tabular performance.
3. Explain PR-AUC, calibration/Brier score, precision, recall, and false-positive rate in plain language.
4. Derive the expected-cost threshold from false-negative and false-positive costs.
5. Walk through approve / manual review / decline and the customer-friction trade-off.
6. Explain PSI and what drift monitoring should trigger operationally.

**Interview prompt:** “Why not use 0.50 as the fraud threshold?”  
**Strong answer:** a probability threshold must reflect the cost of missed fraud, false declines, capacity for review, and calibration; 0.50 has no privileged business meaning.

## 3. LLM Evaluation & Release Platform

**Core story:** A model is releasable only when quality, reliability, risk slices, and cost fit the intended use case.

Learn in this order:

1. Define the release question and the quality/risk metrics that matter for it.
2. Distinguish human preference ground truth from LLM-as-a-judge evaluation.
3. Measure judge agreement/reliability and inspect disagreement cases.
4. Build failure slices and identify where aggregate metrics conceal risk.
5. Explain cost/quality routing and a release gate.
6. State the limitations: benchmark coverage, evaluator bias, and distribution shift.

**Interview prompt:** “How would you evaluate a new support-model release?”  
**Strong answer:** write a task-specific rubric, maintain a held-out benchmark with failure slices, check evaluator reliability against humans, define quality/safety/cost gates, then monitor post-launch.

## 4. U.S. Equity Cross-Sectional Research

**Core story:** Research credibility comes from point-in-time data and evaluation design before it comes from a complex model.

Learn in this order:

1. Explain the signal date, information-availability convention, and forward-return label timing.
2. Define momentum, reversal, volatility, and liquidity features.
3. Explain survivorship bias, look-ahead bias, overlapping labels, and why random K-fold is invalid.
4. Explain Rank IC and quintile-spread evaluation before portfolio metrics.
5. Derive turnover and transaction-cost adjustment.
6. Be explicit about current status: data and point-in-time research infrastructure are built; no final alpha/backtest result is claimed yet.

**Interview prompt:** “What would make a backtest untrustworthy?”  
**Strong answer:** information unavailable at the time, current constituents used historically, randomized temporal splitting, implicit delisting assumptions, and omitted costs can all create spurious performance.

## 5. NLP Customer Support Intent Routing

**Core story:** Automation should route high-confidence cases and deliberately escalate ambiguous cases to people.

Learn in this order:

1. Understand the BANKING77 task and fine-grained intent ambiguity.
2. Compare TF-IDF + logistic regression, BiLSTM, and DistilBERT as a cost/quality sequence.
3. Interpret macro-F1, per-class errors, confusion pairs, and calibration.
4. Define a confidence threshold that maximizes automation coverage subject to a quality constraint.
5. Explain the cost of a wrong auto-route versus a human-review queue.
6. Read the generated results only after the full reproducible workflow completes.

**Interview prompt:** “What would you do with low-confidence predictions?”  
**Strong answer:** use a validation-selected confidence policy, route uncertain examples to review, track review rate and routed-case accuracy, and examine recurring confusion pairs for taxonomy or training-data fixes.

## Weekly practice loop

For one project per week:

- **Day 1:** Read the README and draw the pipeline from memory.
- **Day 2:** Run one core script or test; explain its inputs and outputs.
- **Day 3:** Recreate one metric/formula without looking.
- **Day 4:** Answer the interview prompt aloud in two minutes.
- **Day 5:** Write a 3-bullet resume version and a 60-second STAR story.
- **Weekend:** Record one mock explanation; identify one unclear step and fix it in the project documentation.

## Universal two-minute answer

> I started with [business decision], using [dataset and scale]. I established [baseline] and used [validation design] to avoid [key risk]. The model/analysis achieved [verified result] on [metric], which led to [decision/recommendation]. The important limitation is [limitation], so my next production step would be [next step].

Never substitute a planned result for a verified one. That honesty is an advantage in technical interviews.