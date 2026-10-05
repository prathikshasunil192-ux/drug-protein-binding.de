# Predicting Drug–Protein Binding (DAVIS dataset)

## Goal
Predict how strongly a medicine binds to a protein, using machine learning.

## Data
DAVIS dataset: 68 medicines, 433 proteins, 29,444 pairs.
Binding strength is given as pKd (higher = stronger binding).

## Method
- Medicines → Morgan fingerprints (1024 numbers) or RDKit descriptors (~200 chemical properties)
- Proteins → amino acid composition (20 numbers)
- Model → Random Forest (100 trees)

## Results

| Test type | Medicine features | MSE ↓ | Pearson ↑ |
|---|---|---|---|
| Random split | Fingerprints | 0.33 | 0.76 |
| Unseen medicines | Fingerprints | 0.77 | 0.19 |
| Unseen medicines | Descriptors | 0.50 | 0.40 |

## Key finding
The model looks strong on a random split, but performance drops a lot
for medicines it has never seen. Using chemical descriptors instead of
fingerprints helped. Because the test set has only 14 medicines,
results vary between splits, so they should be read with care.

## Next steps
- Use better protein features (e.g. protein language models like ESM-2)
- Test on unseen proteins as well
- Try deep learning models
