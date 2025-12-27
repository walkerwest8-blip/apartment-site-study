"""
# Apartment Site Study
## Effort-Based Walkability & Amenity Reach (QGIS)
**🔗 Portfolio hub: https://walkerwest8-blip.github.io**

### Project Overview
This project evaluates **pedestrian walkability from a single residential origin** by modeling **physical walking effort** rather than simple distance. Using a pedestrian-capable network combined with **terrain-derived slope**, the analysis identifies which nearby amenities are reasonably reachable on foot and where **access gaps** exist despite geographic proximity.

The primary outputs are **effort-minimizing walking routes** to nearby amenities and activity centers, supported by an effort-weighted reach surface that illustrates how terrain reshapes practical pedestrian access.

This is a learning-focused GIS project intended to demonstrate spatial reasoning, network analysis, raster–vector integration, and clear methodological documentation using **QGIS**.

---

## Core Question
**Which nearby amenities and activity centers are reasonably reachable on foot from the apartment complex when walking effort is constrained by slope and distance, and where do access gaps emerge?**

---

## Scope and Assumptions

### Origin
- **Single origin** representing the apartment complex (one start point for all routes and accessibility modeling).

### Effort Model (Physical Effort Only)
Effort is modeled as a function of:
- **Distance traveled**
- **Slope (grade)** derived from a DEM

This project intentionally does **not** model:
- safety, crime, lighting, traffic stress
- sidewalk quality or ADA compliance (unless explicitly mapped later)
- weather, heat, shade, noise, aesthetics, or perceived comfort

### “Reasonable Walking” Threshold
- Target one-way walking range: **15–25 minutes**
- Rough distance intuition (pre-terrain): **~2–3 km straight-line**
- Final reach is determined by the **effort-weighted** network, not Euclidean distance.

---

## Amenity Types Evaluated
Point amenities evaluated for reachability:
- **Grocery**
- **Gym**
- **Restaurants**
- **Parks**
- **Malls**

---

## Market Districts (Activity Cluster Definition)
In addition to point amenities, this project defines **Market Districts** as walkable activity clusters.

### Operational Definition
A **Market District** is any area where:
- **≥ 15 food/retail/service amenities** occur within a **300 m** neighborhood.

### Inputs
- Restaurants + retail/service POIs (OpenStreetMap-derived)

### Outputs
- **District polygons** (for mapping the cluster footprint)
- **Representative district points** (centroid/representative point) used as routing destinations

---

## Key Outputs (End Results)
1. **Effort-minimizing routes** from the origin to:
   - each amenity point
   - each Market District representative point
2. **Effort-weighted reach map** (isochrones or cost surface) showing:
   - areas reachable within the 15–25 minute effort threshold
3. **Gap identification**
   - amenities/districts that are nearby by distance but **not reachable** within effort threshold

---

## Method Summary (High-Level)
1. Build a pedestrian-capable network from OSM road/path classes.
2. Generate a DEM-derived slope raster.
3. Create an effort cost model that increases with slope and distance.
4. Compute:
   - effort-based accessibility (reach surface / isochrones)
   - effort-minimizing routes to amenities and Market Districts
5. Compare:
   - distance intuition vs effort reality
   - reachable vs not reachable amenities

---

## Data Sources (Planned / Typical)
- OpenStreetMap (roads/paths + amenities POIs)
- DEM for terrain (e.g., USGS 3DEP or equivalent)
- Optional: local boundary/reference layers as needed

---

## Repository Structure (Suggested)
- `data_raw/` — downloaded source data (OSM extracts, DEM tiles)
- `data_processed/` — cleaned layers (network, amenities, slope products)
- `qgis/` — QGIS project file(s) and styles
- `outputs/`
  - `maps/`
  - `routes/`
  - `tables/`
- `docs/` — methodology notes and figures

---

## Status
- [✅] Data acquisition
- [✅] Network build (walkable classes)
- [ ] DEM + slope generation
- [ ] Market District clustering
- [ ] Effort cost model
- [ ] Routes + reach outputs
- [ ] Final maps + writeup
updated 12-26-2025
---

## Notes
This project is designed to be reproducible and iterative: thresholds (e.g., slope penalties, Market District clustering radius/count) will be documented and can be tuned in later versions.
"""
if __name__ == "__main__":
    print(__doc__.strip())



