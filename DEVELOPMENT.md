Development docs
================

Set of scripts to easily build webfonts from SVG images

Installation
------------

```sh
yarn
```


Updating font to the newest ionicons version
------------------------------------------------

### Steps

1. `make getfont` to download an updated version from https://github.com/driftyco/ionicons/tree/3.0/dist/fonts to `src/original/ionicons.svg`
3. Run `yarn dump` to create the corresponding SVG glyph files in `src/svg`.
4. Any new glyph requiring an entry in `config.yml` will be found in a temporary `diff.yml` file.
5. Once `config.yml` has been updated with all new glyphs, run `make dump` again to make sure all temporary files (say `src/svg/glyph__f22d.svg`) are being replaced with properly named glyphs (say `src/svg/genderless.svg`).
6. Run `make`. Generated data will be placed in `./font`. You can rebuild css/html only by running `make html`.
7. Commit your changes, say, `git commit config.yml src/original -m "ionicons vX.Y.Z"`, and create a Pull Request.

### SVG image requirements

Any image will be proportionally scaled, to fit height in ascent-descent
It's convenient to make height = 1000px. Default font baseline will be 20% from
the bottom.

In most cases it's ok to visually align icons to middle line, not to baseline.
If you are not sure, how to start - make image with 10% top/bottom padding.
Then generate demo page and tune scale/offset.
