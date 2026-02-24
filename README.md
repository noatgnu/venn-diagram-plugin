# Venn Diagram


## Installation

**[⬇️ Click here to install in Cauldron](http://localhost:50060/install?repo=https%3A%2F%2Fgithub.com%2Fnoatgnu%2Fvenn-diagram-plugin)** _(requires Cauldron to be running)_

> **Repository**: `https://github.com/noatgnu/venn-diagram-plugin`

**Manual installation:**

1. Open Cauldron
2. Go to **Plugins** → **Install from Repository**
3. Paste: `https://github.com/noatgnu/venn-diagram-plugin`
4. Click **Install**

**ID**: `venn-diagram`  
**Version**: 1.0.0  
**Category**: visualization  
**Author**: CauldronGO Team

## Description

Generate Venn diagrams for set comparison

## Runtime

- **Environments**: `r`

- **Entrypoint**: `venn_diagram.R`

## Inputs

| Name | Label | Type | Required | Default | Visibility |
|------|-------|------|----------|---------|------------|
| `input_file` | Input File | file | Yes | - | Always visible |
| `sample_cols` | Sample Columns | column-selector (multiple) | Yes | - | Always visible |
| `set_names` | Set Names | text | No | - | Always visible |
| `threshold` | Threshold | number (min: 0, max: 100) | No | 0 | Always visible |
| `use_presence` | Use Presence/Absence | boolean | No | true | Always visible |
| `fill_colors` | Fill Colors | text | No | - | Always visible |
| `alpha` | Transparency (Alpha) | number (min: 0, max: 1, step: 0) | No | 0.5 | Always visible |

### Input Details

#### Input File (`input_file`)

Data file containing sets to compare


#### Sample Columns (`sample_cols`)

Columns representing different sets (max 5)

- **Column Source**: `input_file`

#### Set Names (`set_names`)

Comma-separated names for the sets (optional)


#### Threshold (`threshold`)

Minimum value threshold for presence


#### Use Presence/Absence (`use_presence`)

Use binary presence/absence instead of values


#### Fill Colors (`fill_colors`)

Comma-separated hex colors for each set

- **Placeholder**: `#FF0000,#00FF00,#0000FF`

#### Transparency (Alpha) (`alpha`)

Transparency of overlapping regions (0=transparent, 1=opaque)


## Outputs

| Name | File | Type | Format | Description |
|------|------|------|--------|-------------|
| `venn_diagram_svg` | `venn_diagram.svg` | image | svg | Venn diagram visualization (SVG) |
| `venn_diagram_pdf` | `venn_diagram.pdf` | image | pdf | Venn diagram visualization (PDF) |
| `venn_summary` | `venn_summary.txt` | data | tsv | Summary of overlaps between sets |
| `venn_presence` | `venn_presence.txt` | data | tsv | Presence/absence matrix for each set |

## Visualizations

This plugin generates 1 plot(s):

### Venn Diagram (`venn_diagram`)

- **Type**: image-grid
- **Data Source**: `venn_diagram_svg`
- **Image Pattern**: `*.svg`

## Requirements

- **R Version**: >=4.0

### Package Dependencies (Inline)

Packages are defined inline in the plugin configuration:

- `VennDiagram`
- `grid`

> **Note**: When you create a custom environment for this plugin, these dependencies will be automatically installed.

## Example Data

This plugin includes example data for testing:

```yaml
  input_file: venn_diagram/venn_example.txt
  sample_cols_source: venn_diagram/venn_example.txt
  sample_cols: [Control Treatment_A Treatment_B]
  set_names: Control,Treatment A,Treatment B
  threshold: 0
  use_presence: true
  alpha: 0.5
```

Load example data by clicking the **Load Example** button in the UI.

## Usage

### Via UI

1. Navigate to **visualization** → **Venn Diagram**
2. Fill in the required inputs
3. Click **Run Analysis**

### Via Plugin System

```typescript
const jobId = await pluginService.executePlugin('venn-diagram', {
  // Add parameters here
});
```
