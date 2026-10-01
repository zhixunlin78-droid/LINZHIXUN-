---
title: PE6201 RAG Course Q&A Assistant
---

# PE6201 RAG Course Q\&A Assistant

This system answers revision questions using only authorised course materials.  
If the materials do not contain the answer, it says so instead of guessing.

## Files

- PE_RAG_Course_QA.ipynb: the full notebook, runnable in Google Colab.
- eval_set.csv: 55 evaluation questions across two courses.
- eval_results.csv: the model output and verdict for each question.

## Data

The corpus for this project is synthetic. I wrote the two course documents and the 55 evaluation questions by hand, as substitutes for real course materials that cannot be redistributed. Real NTU course materials are not licensed for public redistribution, and using them would raise copyright and PDPA concerns. No copyrighted material was copied. All answers were fixed in eval_set.csv before any model call.

Coverage of the evaluation set: 15 factual, 15 explanatory, 10 edge, 10 out-of-scope, 5 ambiguous.

## How to run

1. Open the notebook in Google Colab.
2. Set your OpenRouter API key as a Colab secret named OPENROUTER_API_KEY.
3. Run all cells from top to bottom.

## Evaluation

- RAG accuracy at threshold 0.20: 47.5 percent by string match, 82.5 percent after manual review.
- RAG abstention rate: 73.3 percent.
- Raw LLM accuracy: 37.5 percent.
- Raw LLM abstention rate: 0 percent.

The gap between string matching and manual review is itself a finding, because a correct answer can be phrased in different words.

## Limitations

The dataset is synthetic and cannot tell us how the system performs on real NTU course materials. Some answers sitting near a chunk boundary were not retrieved correctly, which is a chunking problem.
