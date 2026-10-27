# U.S. Accident Severity: Weather, Time, and Road Conditions

An APMA 3150 team research project at the University of Virginia examining relationships between the U.S. Accidents dataset's severity score, weather, time, location, and road infrastructure.

**Authors:** David Antrobius, Zackary Holt, and Jeffrey Owusu  
**Course project:** Summer 2025

The saved notebook output records a cleaned dataset with **7,728,394 observations and 47 columns**, covering accidents from 2016 through March 2023. Several statistical analyses use random samples of up to one million observations.

## Analysis source

| File | What it contains |
| --- | --- |
| [pcatest.rmd](pcatest.rmd) | Data cleaning, feature preparation, standardization, principal component analysis, scree plots, variable contributions, loading heatmaps, and severity comparisons in PCA space. |
| [anova.rmd](anova.rmd) | One-way and two-way ANOVA, Tukey comparisons, confidence intervals, weather and time interactions, infrastructure comparisons, and diagnostic plots. |
| [montecarlo.rmd](montecarlo.rmd) | Bootstrap resampling of ANOVA statistics and weather-group mean differences. |
| [project.ipynb](project.ipynb) | An **R-kernel notebook** containing the shared preprocessing workflow and saved data summaries. |
| [figures/](figures/) | 33 saved analysis figures. |
| [tukey-results.csv](tukey-results.csv) | Exported Tukey comparison results. |
| [research-project.pdf](research-project.pdf) | The team's final research poster. |

## Scope of this archive

These are recovered original research files. The poster describes the team's broader work, including regression and random forest modeling. Standalone implementations of those models and the team's clustering work were not located in this recovery. They may be held by teammates. The available PCA, ANOVA, and bootstrap source is included here in full.

The analyses have not been rerun as part of recovery, and this archive does not claim to reproduce every result in the poster. The original source files are preserved byte for byte.

## Local data and saved work

The recovered local folder also contains the following large files, excluded from Git by `.gitignore`:

- `clean-accidents.rds` — approximately 603 MB of serialized cleaned R data.
- `full-pca-workspace.rdata` — approximately 744 MB of saved R workspace data.
- `06.25-final-presentationapma-3100.mkv` — approximately 68 MB of presentation video.

The raw input `US_Accidents_March23.csv` referenced by the preprocessing code was not located. The cleaned RDS file provides a saved input for continuing work without the raw CSV.

## Reproduction notes

The source reflects an interactive R research workflow and has not been verified to knit independently in a fresh session.

- The original R Markdown files refer to `clean_accidents.rds`, while the recovered data file is named `clean-accidents.rds`. Adjust the local filename or the input reference before execution.
- `pcatest.rmd` begins by reading the missing raw CSV. To continue from the recovered cleaned data, replace its preprocessing section through the cleaned-data save with `accidents <- readRDS("clean-accidents.rds")`, then continue at the PCA section.
- `montecarlo.rmd` expects the `df_grouped` object prepared in the grouped-weather section of `anova.rmd`.
- A plot in `anova.rmd` uses `summary_df`, which is not defined in that file. This is an outstanding dependency on the original interactive session.
- The workspace `save(...)` lines at the ends of the PCA and ANOVA documents sit outside R code fences; they are not executed when knitting.
- R package imports in the source include `tidyverse`, `janitor`, `lubridate`, `factoextra`, `ggforce`, `scales`, `pheatmap`, `hexbin`, `multcomp`, `multcompView`, `emmeans`, `reshape2`, `viridis`, and `fmsb`. Package versions were not pinned in the recovered files.

The duplicate `anovasss.rmd` and the original R console history are retained in the local recovery, but excluded from Git by default. Team authorship is preserved; no new license has been assigned during recovery.
