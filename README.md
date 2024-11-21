# pdf-shrink.sh - shrink a PDF using ghostscript

When a PDF is generated, or scanned, the resolution and file size is often much too high.

There are many different options[^1], how to reduce PDF size, and depending on the concrete use case, 
the best option might be different.

For me, the [solution using ghostscript suggested by Michael D and others](https://askubuntu.com/a/256449/592751) worked really good in many cases, so I wrote this simple script I use, so I don't need to remember the parameters.

[^1]: e.g. https://askubuntu.com/q/113544/592751


## Usage

```bash
pdf-shrink.sh <settings>[:<dpi>] <input> [<output>]
```

<output> is optional, settings will be appended to filename

<settings> can be ghostscript's PDFSETTINGS options:

- screen   - lower quality, smaller size. (72 dpi)
- ebook    - for better quality, but slightly larger pdfs. (150 dpi)
- prepress - output similar to Acrobat Distiller "Prepress Optimized" setting (300 dpi)
- printer  - selects output similar to the Acrobat Distiller "Print Optimized" setting (300 dpi)
- default  - selects output intended to be useful across a wide variety of uses, possibly at the expense of a larger output file

 <dpi> is optional, e.g. 150 for 150 dpi

## Requirements

- ghostscript (`gs`) is used internally and must be installed


## Installation

I cloned this repo and created a symlink for `pdf-shrink.sh` in my bin, e.g. something like :

```bash
git clone ...
ln -s pdf-shrink.sh ~/bin
```


## Examples

```bash
pdf-shrink.sh ebook input.pdf
pdf-shrink.sh default:100 input.pdf
```

## Alternatives

There are many alternatives that are recommended.

For me, a PDF with libreoffice (draw) and exporting as PDF produced also quite good results in many cases.
