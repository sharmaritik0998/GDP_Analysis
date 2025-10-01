# GDP Analysis and Visualization (1960–2016)

This project explores global GDP levels and year‑over‑year GDP growth across countries from 1960 to 2016, and generates interactive Plotly visualizations at both country and multi‑country levels. It computes per‑country GDP growth percentages, surfaces top GDP aggregates, and exports interactive HTML charts for exploration.[1]

### Key features
- Cleans and prepares World Bank–style GDP time series for 256 entities from 1960–2016.[1]
- Computes per‑country year‑over‑year GDP growth percentages with vectorized logic.[1]
- Exports interactive Plotly line charts per country (“GDP Individual”) and for global comparisons (“Countries GDP.html”, “GDP Growth.html”).[1]
- Helper utilities to compare custom sets of countries by GDP level or by GDP growth.[1]

### Example insights
- “Cayman Islands” shows the highest average growth in the sample window; “South Sudan” exhibits a negative average growth in the computed series.[1]
- Peak GDP aggregates include “World”, “High income”, “OECD members”, “United States”, “China”, “India”, “Japan”, “Germany”, etc., reflecting expected scale.[1]

***

### Contents
- Project_GDP_Analysis.ipynb — main notebook for preprocessing, computation, and chart generation.[1]
- Generated outputs (created at runtime):
  - Countries GDP.html — all‑countries GDP comparison chart.[1]
  - GDP Growth.html — all‑countries GDP growth comparison chart.[1]
  - GDP Individual/ — directory of per‑country GDP level charts.[1]
  - GDP Growth Individual/ — directory of per‑country GDP growth charts.[1]
  - Custom multi‑country charts, e.g., INDCHN.html, INDITAUSACHN.html.[1]

***

### Data columns
The working dataframe includes:
- Country Name — country or aggregate region name.[1]
- Country Code — ISO or aggregate code (e.g., IND, CHN, WLD).[1]
- Year — observation year (1960–2016).[1]
- Value — GDP level (nominal, as provided in the dataset).[1]
- GDP — computed year‑over‑year growth percentage per country.[1]

GDP growth is computed per entity as:
- First available year: 0.00 by convention.[1]
- Subsequent years: GDP_t = round((Value_t − Value_{t−1}) / Value_{t−1} × 100, 2).[1]

***

### Setup

1) Environment
- Python 3.9+ recommended.[1]
- Install dependencies:
  - pandas
  - numpy
  - plotly (plotly and chart studio offline usage via plotly.offline as pyo)
  - Any runtime that supports Jupyter/Colab for .ipynb execution[1]

Example:
- pip install pandas numpy plotly[1]

2) Data
- The notebook expects a World Bank–style GDP time series with “Country Name”, “Country Code”, “Year”, “Value”.[1]
- Sample previews in the notebook confirm shape: 11,507 rows, 256 entities, 1960–2016 range.[1]

***

### How to run

1) Launch the notebook
- Open Project_GDP_Analysis.ipynb in Jupyter or Google Colab.[1]

2) Execute cells in order
- Load and preview the input data.[1]
- Compute per‑country GDP growth and concatenate per‑country frames.[1]
- Generate all interactive charts: per‑country GDP levels, per‑country growth, and all‑countries comparisons.[1]

3) Generated artifacts
- “GDP Individual/” and “GDP Growth Individual/” folders will be created if missing.[1]
- HTML files will be saved next to the notebook; open them in a browser to interact.[1]

***

### Notable notebook cells

- Growth computation across all entities
  - Builds a list of per‑country frames, computes growth, and concatenates to a master df with 11,507 rows and 5 columns.[1]

- Summary stats
  - Average GDP growth by “Country Name” to identify consistently high or low performers.[1]
  - Top “Value” (GDP level) per entity to rank peak output by country/aggregate.[1]

- Visualization blocks
  - Per‑country GDP lines saved to “GDP Individual/{country}.html”.[1]
  - All‑countries GDP line “Countries GDP.html”.[1]
  - All‑countries growth line “GDP Growth.html”.[1]
  - Custom compare helpers:
    - comaregdp([...], isOpen) — compare GDP levels for a selected list of country codes.[1]
    - comparegdp([...], isOpen) — compare GDP growth for a selected list of country codes.[1]
  - Examples created: INDCHN.html, INDITAUSACHN.html, WLDCHN.html.[1]

***

### Usage examples

- All‑countries GDP level chart
  - Produces an interactive line plot with color by country and time on the x‑axis.[1]

- Per‑country GDP level charts
  - Loops over unique Country Name and exports one HTML per entity to “GDP Individual/”.[1]

- Compare specific countries by GDP level
  - comaregdp(["IND","USA"], isOpen=True) creates and opens an HTML comparison.[1]

- Compare specific countries by GDP growth
  - comparegdp(["IND","USA","ITA","CHN"], True) outputs a growth comparison chart for selected countries.[1]

***

### Outputs preview

- df.head examples for “Arab World”, “China”, “India” confirm correct growth calculations and time alignment.[1]
- Aggregates like “World”, “United States”, “China”, “India”, “Japan”, “Germany” appear in “max Value” rankings.[1]

***

### Project structure

- Data prep: filtering by Country Name or Country Code, computing GDP growth percentage, concatenating results.[1]
- Analytics: groupby summaries for average growth and maxima by Value.[1]
- Visualization: Plotly line charts at entity and comparison levels with saved HTML.[1]

***

### Reproducibility notes

- Deterministic computations: growth uses previous year Value per entity with rounding to two decimals.[1]
- Outputs are filesystem‑dependent; ensure write permissions for the working directory.[1]
- Some aggregates (e.g., regions or income groups) are included alongside countries; interpret comparisons accordingly.[1]

***

### Roadmap
- Add CLI and config for headless generation of specific comparison sets.[1]
- Add caching for large render batches and progress logging.[1]
- Add statistical summaries (CAGR, volatility, drawdowns) per country and bundle as CSV exports.[1]
- Add robust data loader for raw World Bank CSV with schema validation.[1]

***

### License
Specify a license for reuse (e.g., MIT).[1]

***

### Acknowledgments
- Inspired by World Bank GDP time series conventions and public macro data formats for cross‑country analysis.[1]

[1](https://ppl-ai-file-upload.s3.amazonaws.com/web/direct-files/attachments/4704480/eddee497-94ec-48f4-b342-5f28499e3b4e/Project_GDP_Analysis.ipynb)
