# Aspect-Based Sentiment Analysis with Small Language Models

This repo contains the capstone work for the SMU MSDS program.  
The goal is to measure whether coordinated small language model (SLM) agents
can perform aspect-based sentiment analysis (ABSA) on product reviews at low cost.

## What’s in this repo
- `notebooks/capstone_pipeline_review.ipynb`  
  End-to-end pipeline:
  - chunk reviews
  - extract aspects
  - score sentiment per aspect
  - aggregate to review-level
  - compute latency, cost, and error metrics

- `datasets/electronics_sample.csv`  
  200-review sample (Amazon Electronics domain).

- `datasets/electronics_chunks.csv`  
  Same reviews split into ~700-char chunks for model input.

- `notebooks/outputs/*.csv`  
  Model outputs and evaluation summaries:
  - extracted aspects per review
  - sentiment per aspect
  - MAE vs. star ratings
  - latency and cost summaries

- `requirements.txt`  
  Minimal Python deps to rerun the notebook.

## Reproducing results
1. Create a `.env` file (not checked in) with:
   - `HF_TOKEN`
   - `HF_ENDPOINT_URL`
   - `FEATURE_FINDER_MODEL`
   - `SENTIMENT_ENDPOINT_URL`
   - `SENTIMENT_MODEL_NAME`
2. Start the two Hugging Face Inference Endpoints (feature extractor / sentiment scorer).
3. Run `notebooks/capstone_pipeline_review.ipynb` top to bottom in VS Code / Jupyter.

The notebook writes all intermediate artifacts to `notebooks/outputs/`.

## Notes
- Raw 500MB+ source data and API credentials are intentionally excluded.
- This repo is prepared for faculty review, not public deployment.
