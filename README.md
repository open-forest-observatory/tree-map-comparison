Code to compare predicted tree map(s) vs. an observed tree map to assess tree detection accuracy

## Usage

The only script you need to run directly is `run-tree-map-comparison.R` in the repo root directory. Can be run either interactively in RStudio or from the command line.

If run from the command line, the command line arguments specify the locations of the relevant files. The call is in the format: `Rscript --vanilla /ofo-share/utils/tree-map-comparison/run-tree-map-comparison.R {observed tree points file path} {predicted tree points directory path} {perimeter of observed tree map file path} {temp directory path for intermediate files} {output directory path for eval stats}`

For example: `Rscript --vanilla /ofo-share/utils/tree-map-comparison/run-tree-map-comparison.R /ofo-share/cv-treedetection-eval_data/observed-trees/observed-trees.geojson /ofo-share/cv-treedetection-eval_data/predicted-trees/lmf/ /ofo-share/cv-treedetection-eval_data/perimeters/emerald-point-perimeter.geojson /ofo-share/tmp /ofo-share/cv-treedetection-eval_data/tree-detection-evals`

The observed tree map must have heights (in meters) in an attribute `Height` and its status as understory or overstory in the attribute `under_neighbor` (boolean). It must be a geospatial file (e.g. gpkg, geojson) with point geometry. The predicted tree maps must have heights in the attribute `height` and it must be a .gpkg file with point geometry.

Note that the predicted tree maps are provided as a directory. The assessment runs (parallelized) on all .gpkg files within the provided directory.
