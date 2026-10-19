# HI CAMERA — composition preset feed

Static, data-only JSON updates for the Galaxy [HI_CAMERA] app. This repository
does **not** contain the app source, any captured private photos, API keys, or
original Instagram/YouTube media.

## Data format
- File: `feed.json`
- Schema: `schema_version: 2`
- Active library: experimental composition presets with source/provenance.
- Numerical camera/framing values are **design estimates**, not extracted EXIF.
- Original referenced image/video copyright remains with the source creators.
- 100 visually reviewed reference examples are a future curation goal,
  not a completed collection.

## Safe update workflow
1. Update composition data in `G:\HI_CAMERA\updates\feed.json`.
2. Run `python tools/prepare_public_feed.py` in HI_CAMERA to validate and
   refresh this publish-only directory.
3. Commit `feed.json` and push to the public `main` branch.
4. Installed Android app fetches the raw HTTPS JSON feed on its next daily
   check (or via manual **업데이트 확인**).
5. If the network or validation fails, the app keeps its last good copy.

Publish **only the allowlisted data and guide files** (feed.json, README.md, .gitignore, guide_34_ko.md and guide_54_ko.md). Do not push the parent HI_CAMERA folder.

## Technical details
On-device camera/pose/scene inference sends zero frames to GitHub.
The feed is downloaded as a public static HTTPS document. App-code, UI and
camera-engine changes still require a signed APK release.

