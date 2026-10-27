# Comparison method

Use one comparison group to answer one question about a makeup detail. A group might compare two lip colors or two eyeliner shapes. Avoid combining a new pose, a new photo and a new look into a single comparison.

## 1. Fix the input and viewing setup

- Keep an unchanged local copy of the input. Give it an identifier such as `portrait-01`. Reuse the exact file for every preview in the group; a fresh selfie is a different input even if it looks similar.
- Assign a group identifier such as `lip-placement-01`. Record the input identifier on every row.
- Record whether the tool uses your input or a prepared sample. With sample previews, compare only outputs of the same sample model. If you cannot verify the underlying input, use `unknown` for `same_input_confirmed`.
- View the original and each output side by side at a comparable size. Keep the display and viewing light the same while taking notes. Record any crop, filter or automatic enhancement you cannot control.
- Choose the single setting to vary. If a preset changes several makeup areas at once, record that bundle explicitly; do not attribute the result to one color alone.

Write the question and setup in `controlled_setup`, then keep that text consistent across the group. The optional photo guidance linked in the README can help plan a future input; this notebook does not take or upload photos.

## 2. Record what you can actually see

Write one row per output. Use concrete descriptions such as "color extends slightly beyond the outer lip edge" or "the liner ends before the brow tail." Avoid a general score such as "90% realistic."

Check each output against the original input, not only against the other preview:

| Check | Look for | Do not infer |
| --- | --- | --- |
| Face shape | Apparent changes to the jaw outline, nose width, eye spacing, eyelid shape or lip boundary. Distinguish a shadow or outline from an uncertain shape change. | That facial geometry is preserved exactly because it looks familiar. |
| Lighting | Brighter exposure, a warmer/cooler cast, changed shadows or new highlights across the face or background. | That a warmer-looking complexion came from the makeup alone. |
| Texture | Broad smoothing, lost detail, added shine or sharpening beyond the area being compared. | A change in actual skin condition or a product's real finish. |
| Artifacts | Broken liner, displaced lashes, color bleeding, asymmetry or edges crossing hair, glasses or fingers. | That an artifact is a recreatable makeup step. |

For the three check columns, `consistent` means **no obvious change noticed in this comparison**. It is a visual observation, not proof of identity preservation. Use `uncertain` if the crop, resolution or overlap prevents a useful check. Use `not_checked` until you have looked.

## 3. Decide whether to use the comparison

Use these rules before choosing a practice detail:

| Status | When to use it | Next action |
| --- | --- | --- |
| `usable` | The exact input is confirmed and all three checks are `consistent`. Any artifact is recorded and does not affect the particular detail being compared. | Choose `practice_one_detail` or leave the decision `undecided`. |
| `retest` | The same input is confirmed, but a check is uncertain or incomplete, or a repeat may resolve an artifact. | Choose `retest`. State the exact change needed to make a comparison possible. |
| `not_comparable` | The input changed or is unknown, or a visible face/lighting/texture change confounds the comparison. | Choose `set_aside` or `retest`. Do not use this row to prefer a makeup look. |

If the tool has relevant controls, a retest might turn off a separate skin-smoothing or relighting option. If those changes cannot be controlled, set that output aside. Do not claim to have isolated an effect when you cannot.

Keep excluded rows in your private worksheet so you remember why they were excluded. Do not pool groups with different input images into an accuracy or preference score.

## 4. Turn one visible detail into a practice plan

For a usable row, describe a small action you can attempt with products already available. Name the area, placement, amount and order when you can. For example: "Place a small amount of lip color at the center; blend toward the edges; compare the outline with the original target."

Record gaps honestly: an image may not reveal the brush, product, shade or layer order. Do not invent those details. Treat the plan as an idea to try, not a reconstruction of how the image was made.

After physical practice, make a separate note of what you actually applied and observed. An AI image is not evidence of wear time, comfort, foundation shade match or an achievable result. Keep those observations separate from the preview row.

## CSV field guide

The blank worksheet and fictional example use the same 20 columns. A row is one output, not one person. There are no required numeric scores.

| Column | What to enter |
| --- | --- |
| `record_kind` | `observation` for your own notes; the example uses `illustrative`. |
| `comparison_id` | A local identifier for the question and controlled setup. |
| `input_id` | Identifier of the unchanged input file or confirmed sample model. Use `unknown` if it cannot be established. |
| `preview_id` | Unique local identifier for this output. Keep any file mapping privately. |
| `tool_label` | Tool name and visible version, if known. Write `version unknown` when needed; do not guess. |
| `preview_mode` | `own_input`, `sample` or `unknown`. |
| `preset_or_prompt` | The preset or exact instruction used, without personal information. |
| `same_input_confirmed` | `yes`, `no` or `unknown`, relative to the group's intended input. |
| `controlled_setup` | The question, crop/display setup and unchanged controls. |
| `changed_setting` | The one intended change, or the full preset bundle if it changes multiple things. |
| `visible_makeup_changes` | Specific visible changes to makeup color, placement or shape. Do not include unexplained facial changes as makeup effects. |
| `face_shape_check` | `consistent`, `changed`, `uncertain` or `not_checked`. |
| `lighting_check` | The same four values, for apparent exposure, color cast and shadows. |
| `texture_check` | The same four values, for apparent smoothing, detail and shine. |
| `artifacts` | Describe issues and whether they affect the chosen detail. Write `none noticed` if checked; `not checked` otherwise. |
| `comparison_status` | `usable`, `retest` or `not_comparable`, using the rules above. |
| `decision` | `practice_one_detail`, `retest`, `set_aside` or `undecided`. |
| `practice_steps` | Concrete proposed steps only for `practice_one_detail`. Otherwise leave blank. |
| `confidence` | `low`, `medium` or `high`: your confidence in the recorded observation, not in the model's accuracy. |
| `limits_or_next_check` | What remains unknown and the next useful check. This can be "No fair comparison available." |

Fill each column except `practice_steps`, which stays blank unless you choose to practice a detail. Use the explicit unknown/not-checked options instead of filling gaps with guesses. If writing raw CSV, quote cells containing commas, quotes or line breaks; a spreadsheet's CSV export normally handles this.

## Read the fictional example

- `fictional-a` illustrates an apparently stable output with one lip-placement detail to practice. The row is still not a real observation.
- `fictional-b` illustrates an output with changed face shape, lighting and texture. Its makeup cannot be compared fairly with the first row.
- `fictional-c` illustrates an unconfirmed sample input. It belongs in the record of the attempted comparison, but it must be excluded from selecting a look until the input can be controlled.

The labels, descriptions and outcomes in these rows were written solely to teach the format. There are no corresponding portraits or generated images.
