# parse_2D.ipynb

## Purpose

This jupyter notebook is a helper tool for parsing **2D VdM scans**. During VdM scan program, we also record 2D scans. These scans cannot be processed directly in the VdM Framework. Therefore, they must be parsed and saved as separate parts, and each part must then be processed individually with the VdM Framework.

The workflow is:
1. take a 2D scan file from **EOS** or the **BRIL data area**,
2. copy it locally,
3. remove the original `/vdmscan` node from the copied file,
4. split the scan into cycles,
5. select one **SEPARATION** cycle and pair it with the main **CROSSING** cycle,
6. save the split hd5 files with suffixes _1, _2, ...,
7. modify the pair_index variable using an even number. For example, in 2024 we had 9 pairs from 2D scans, so the possible values of pair_index were 0, 2, 4, 6, 8, 10, 12, 14, and 16.
---

## Requirements

This notebook uses the `vdmtools` package.
### Install `vdmtools`

```bash
pip install "vdmtools @ git+https://gitlab.cern.ch/flpereir/vdmtools.git"