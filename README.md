# TakeMeter

## Community Choice and Reasoning

I chose r/indieheads because it is a large music discussion community where users discuss albums, artists, songs, and music news. The community contains a mix of detailed analysis, personal opinions, and emotional reactions, making it a good fit for a text classification task.

---

## Label Taxonomy

### Analysis

Definition: A comment that supports an opinion using evidence, comparisons, production details, lyrics, or specific reasoning.

Examples:

* "Compared to their previous album, the songwriting is much more focused."
* "The production helps the vocals stand out more clearly."

### Opinion

Definition: A personal judgment or preference with little supporting evidence.

Examples:

* "This album is overrated."
* "I think this is the band's weakest project."

### Reaction

Definition: An emotional response, joke, meme, or immediate reaction with little reasoning.

Examples:

* "Holy shit this track is incredible."
* "I can't believe they finally released new music."

---

## Data Collection and Labeling Process

I collected 200 comments from r/indieheads. Each comment was manually labeled as Analysis, Opinion, or Reaction according to the definitions above.

Label Distribution:

* Analysis: [fill in count]
* Opinion: [fill in count]
* Reaction: [fill in count]

### Difficult Examples

Example 1:
"This album is overrated because the production sounds flat."
Decision: Opinion. The comment contains a reason, but the reasoning is brief and mainly expresses a personal judgment.

Example 2:
"This song is amazing because the chorus hits so hard."
Decision: Reaction. The comment is mostly an emotional response.

Example 3:
"This is their best album because every song is memorable."
Decision: Opinion. The comment provides little evidence beyond personal preference.

---

## Fine-Tuning Approach

Base Model:

* distilbert-base-uncased

Training Setup:

* HuggingFace Transformers
* Google Colab T4 GPU

Hyperparameter Decision:

* I used the default learning rate and training settings provided in the starter notebook because the dataset size was relatively small.

---

## Baseline Description

The baseline model used Groq's llama-3.3-70b-versatile in a zero-shot setting.

The prompt included:

* Community description
* Label definitions
* Example comments for each label

The model was asked to output only one label:

* analysis
* opinion
* reaction

---

## Evaluation Report

### Overall Accuracy

| Model                 | Accuracy |
| --------------------- | -------- |
| Zero-Shot Baseline    | 0.60     |
| Fine-Tuned DistilBERT | 0.60     |

Improvement: 0.00

### Per-Class Metrics

[Paste notebook output here]

### Confusion Matrix

| True \ Pred | Analysis | Opinion | Reaction |
| ----------- | -------- | ------- | -------- |
| Analysis    | ?        | ?       | ?        |
| Opinion     | ?        | ?       | ?        |
| Reaction    | ?        | ?       | ?        |

### Wrong Prediction Analysis

Example 1:
[Paste example]

Why it failed:
The comment contains both an opinion and a small amount of reasoning, making the boundary difficult.

Example 2:
[Paste example]

Why it failed:
The comment is short and lacks enough context.

Example 3:
[Paste example]

Why it failed:
The model confused emotional language with evidence-based discussion.

### Sample Classifications

| Comment   | Prediction | Confidence |
| --------- | ---------- | ---------- |
| [example] | Analysis   | 0.xx       |
| [example] | Opinion    | 0.xx       |
| [example] | Reaction   | 0.xx       |

Correct Example Explanation:

The prediction is reasonable because the comment includes specific evidence and discussion rather than only personal preference.

---

## Reflection

I intended the model to learn the difference between evidence-based discussion, personal opinions, and emotional reactions. However, the model often focused on keywords and sentence length rather than the deeper reasoning structure of the comment.

---

## Spec Reflection

One way the spec helped me was by forcing me to clearly define my labels before collecting data.

One way my implementation differed from the original plan was that some comments were more ambiguous than expected, so I had to create additional decision rules while labeling.

---

## AI Usage

### Example 1

I used ChatGPT to help refine my label definitions and identify ambiguous edge cases. I revised the suggested labels to better fit r/indieheads discussions.

### Example 2

I used ChatGPT to help analyze model errors and identify common confusion patterns between Opinion and Analysis. I reviewed the examples myself before including the conclusions in my report.

### Annotation Assistance

I used AI assistance only as a labeling aid and manually reviewed all assigned labels before adding them to the dataset.
