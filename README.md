# Pesticide Chemical Toxicity Dataset (SMILES)

This dataset contains structured information on agricultural chemicals, including their English names, toxicity ratings, and SMILES representations for molecular structure. It is based on stable pesticide metrics derived from LC50 and LD50, improving on prior half-life-based methods.

## Reference Work for Citation

The dataset `stable_pesticide_data.csv` was curated and utilized for training in our paper:  
[Pesti-Gen: Unleashing a Generative Molecule Approach for Toxicity Aware Pesticide Design](https://arxiv.org/abs/2501.14469)  
by Taehan Kim and Wonduk Seo

The dataset improves upon previous half-life based toxicity datasets - having multiple toxicity metrics, with separate (1) livestock toxicity and (2) aqua toxicity based on LD50 (Lethal Dose 50) and LC50 (Lethal Concentration 50).
The dataset is curated and SMILES-extracted from [Gyeonggi Province Data](https://data.gg.go.kr/portal/data/service/selectServicePage.do?&infId=XM0L7AK0UL00KYARRMU929751298&infSeq=1#none).


The older dataset using half-life-based toxicity information, with SMILES extracted from the data provided by Shen, is available as `half_life_pesticide.csv`. This data is described in [Yike Shen's paper](https://www.sciencedirect.com/science/article/abs/pii/S0304389422009670?via%3Dihub).

## Available Files

- `stable_pesticide_data.csv`: Final curated dataset with toxicity scores, metadata, and SMILES.
- `half_life_pesticide.csv`: Older dataset based on half-life scores and structure extraction, based on Yike Shen’s data.



## Toxicity Label Mapping

Toxicity classes were translated and assigned raw severity scores based on regulatory interpretation. These were scaled using min-max normalization to preserve the relative severity relationship between categories. You may freely adjust the score assignments based on your application.

### Livestock Toxicity

| Label                | Raw Score |
|---------------------|-----------|
| High Toxicity (II)  | 1000      |
| Avg Toxicity (III)  | 100       |
| Low Toxicity (IV)   | 10        |
| Unclassified        | 1         |

### Ecological Toxicity

| Label     | Raw Score |
|-----------|-----------|
| Rank I    | 16        |
| Rank II   | 4         |
| Rank III  | 1         |
| Exempt    | 0         |

## Key Columns

| Column Name              | Description |
|--------------------------|-------------|
| `AGCHM_ENG_NM`           | English chemical name. |
| `LIVESTCK_PISN_RATG_ENG` | Livestock toxicity class: `Low Toxicity (IV)`, `Avg Toxicity (III)`, `High Toxicity (II)`, `Unclassified`. |
| `ECOLGY_PISN_RATG_ENG`   | Ecological toxicity rank: `Rank I`, `Rank II`, `Rank III`, `Exempt`. |
| `SMILES`                 | Canonical SMILES string. |
| `is_valid`               | Boolean indicating SMILES validity. |
| `REGIST_ID`              | Chemical registration ID. |
| `REFINE_WGS84_LAT` / `REFINE_WGS84_LOGT` | Geolocation coordinates. |
| `AGCHM_NM`               | Original Korean chemical name. |
| `PURPOS_NM`, `DEASEINS_DTLS`, `CROPS_DTLS` | Usage context (purpose, diseases, crops). |
