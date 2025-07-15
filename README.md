# SmartClip Learner – Tag-Based Recommendation Engine

This is part of the Lumin AI prototype suite. It recommends gaming clips based on a user’s **past likes and watches**, using a **tag-based content filtering approach** powered by NLP.

---

## What It Does

- Takes user interaction history:  
  - Clips they liked (`🔥`)  
  - Clips they fully watched but didn’t like (`⏱️`)  

- Converts clip tags into vectors using **CountVectorizer**
- Builds a **user preference vector** weighted by interaction type
- Computes **cosine similarity** between user preferences and all clips
- Recommends **top 3 unseen clips** based on similarity

---

## Example Tags Used

- `clutch`, `headshot`, `fail`, `comedy`, `highlight`, `rage`, `voice`

---

## Technologies Used

- Python  
- Pandas  
- scikit-learn (`CountVectorizer`, `cosine_similarity`)  
- NumPy

---

## How It Works (Step-by-Step)

1. **Dataset Setup:**  
   A small dataset of gaming clips is created, each labeled with 1–3 tags.

2. **User History:**  
   The user’s liked and watched clip IDs are defined separately.

3. **Tag Vectorization:**  
   All tags are converted into a sparse matrix using `CountVectorizer`.

4. **User Vector Calculation:**  
   - Likes = 2.0 weight  
   - Watches = 1.0 weight  
   Combined to form the user’s tag preference profile.

5. **Similarity Calculation:**  
   Cosine similarity is used to match the user vector with each clip.

6. **Recommendation Output:**  
   Clips already seen are filtered out, and the top 3 unseen clips are recommended.

---

## Why It Matters for Lumin

This model simulates a **real recommendation engine** Lumin could use when:
- Clip tags are available (via AI or user annotation)
- Interaction data is collected (likes, full watches)

It is simple, interpretable, and can be extended to use:
- TF-IDF tag weighting  
- Actual tag embeddings (e.g. using CLIP or GloVe)  
- Collaborative signals (in future models)
