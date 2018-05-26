---
layout: post
title:  "Building a blog using GitHub Pages and Jekyll"
date:   2018-05-25 20:00:03 -0700
categories: blogging github jekyll
---

## Caveats

This post is written with the assumption that you are working in a macOS
environment. These steps can be adapted to work in other operating systems but
the details will differ wildly depending on the exact environment.

## Getting Started

First, follow the instructions on [GitHub Pages](https://pages.github.com/) to
initialize and download your repository.

Then, install Jekyll (using the --force option because the folder is not empty):

```sh
gem install bundler jekyll
cd /path/to/repository
jekyll new . --force
```

To view the site, simply run Jekyll in live-reloading mode and navigate to
http://localhost:4000 in your browser:

```
bundle exec jekyll serve --livereload
```

## Importing the Theme

Jekyll’s default theme is [Minima](https://github.com/jekyll/minima). True to
its name, it’s a visually minimal theme with lots of white space. It’s fairly
attractive so we’ll use it as a starting point to customize later.

This next step is optional, but I recommend it for power users: Jekyll’s default
behavior is to use Minima as a “gem-based theme”, which means all of your site’s
layouts and stylesheets are being injected from a remote directory (the minima
gem’s installation folder). You can provide custom overrides, but I found it
much more straightforward to [convert the theme to a “regular
theme”][jekyll-converting-themes], which
essentially boils down to copying the theme’s assets into your site’s local
directory. With everything in one place, it became easier to navigate the site’s
source files and start stripping out useless conditionals and bits of HTML I
didn’t like.

[jekyll-converting-themes]: https://jekyllrb.com/docs/themes/#converting-gem-based-themes-to-regular-themes

```sh
for f in $HOME/.rbenv/versions/2.5.0/lib/ruby/gems/2.5.0/gems/minima-2.5.0/*; do
  [[ -d $f ]] && cp -r $f ./;
done
```
