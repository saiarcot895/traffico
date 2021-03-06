# traffico [![Build Status](https://travis-ci.org/mapillary/traffico.svg?branch=master)](https://travis-ci.org/floscher/traffico)
An Open Source Traffic Sign Font. Read more on [traffico.io](http://traffico.io/)

## Getting the dependencies

### OS X

To build traffico you need homebrew and ruby installed. These are dependencies of fontcustom gem.

Then run:

```shell
brew install fontforge --with-python
brew install eot-utils
brew install node
gem install fontcustom
```

### Linux

```shell
sudo apt-get install fontforge node
wget http://people.mozilla.com/~jkew/woff/woff-code-latest.zip
unzip woff-code-latest.zip -d sfnt2woff && cd sfnt2woff && make && sudo mv sfnt2woff /usr/local/bin/
gem install fontcustom
```

## Build
The build process is a simple gulp task.

First get the gulp dependencies: <code>npm install</code>.

To finally build the font run: <code>gulp</code>.

The resulting `build`-folder contains the following:
* `build/fonts/` contains the packaged font in different formats (woff, svg, eot, ttf)
* `build/fonts/traffico-preview.html` a collection of all available symbols for building custom signs
* `build/json` contains json-files with pre-built sign-definitions
* `build/sign-overview.html` an overview of all the pre-built signs from the `json`-folder
* `build/stylesheets/traffico.css` this file lets you simply use CSS-classes for constructing signs (see section "Usage")

To remove all the generated files run <code>gulp clean</code>.

## Usage

To use the font in HTML, simply include `traffico.css` (ensure, that the fonts reside in the directory `../fonts` relative to the CSS).

A sign consists of a `<span>`-tag with class `t`, that contains one or more `<i>`-tags which represent the various elements of the sign.

The `<i>`-tags have two classes: One is `t-ID` where `ID` is the ID of the symbol (see `build/fonts/traffico-preview.html` for available symbols).
The other one is `t-c-COLOR` where `COLOR` is the color of the symbol (one of `red`, `yellow`, `yellow-dark`, `green`, `blue` and `black`).

```html
<span class="t">
  <i class="t-square-bg t-c-blue"></i>
  <i class="t-tri-bg-in t-c-white"></i>
  <i class="t-pedestrian-crossing t-c-black"></i>
</span>
<span class="t">
  <i class="t-circle-bg t-c-white"></i>
  <i class="t-circle-o t-c-red"></i>
  <i class="t-content t-c-black">130</i>
</span>
```

## Status & Contributing
Traffico is under heavy development and the amount of shapes it contains will grow in the future. Contributions are welcome.


### Next steps
- finding a good naming convention for signs across countries
- finding a good taxonomy for traffic sign categories to make if more future proof
- publish binary .sketch file with predefined export settings and all current shapes to make life easier
- more shapes!
