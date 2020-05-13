---
layout: post
categories: [tutorial, jupyter]
title: Blogging with jupyter notebooks
---

{::nomarkdown}<sub>{:/}
This is a guide for self-hosting notebooks. If you have no problem with putting your content behind someone else's paywall, you can try [embeding jupyter notebooks in medium](https://medium.com/ai-in-plain-english/how-to-embed-code-or-jupyter-notebook-in-medium-7464411217e7).
{::nomarkdown}</sub>{:/}

It started the other day when I had this idea of making my personal website render programming notebooks.

{::nomarkdown}<sub>{:/}
**programming notebook:** a type of document where you can experiment with code and see the result next to it visuallized as graphs or tables. This is one of the ways scientists and data analysts use the power of programming to tell stories. [Jupyter](https://jupyter.org) is the most widely used notebook format and [Observable](https://observablehq.com/explore) is another example.
{::nomarkdown}</sub>{:/}

Anyhow, the tasks were: dockerizing the render script, setting up continuous delivery and lastly come up with a way to make it play with my nextjs[^1]/webpack/mdx pipeline which has not been done by anyone before... Playing with `knitr` then a bunch of similar tools for `jupyter`, I realized it's just not worth doing myself. My original motivation for this was to write more and explore data more, not goofing around with these tools.

So I looked up *"blogging with jupyter notebooks"*[^2]. Luckily, this is not a novel concept. Two projects for exactly it showed up: [Jupyter Book](https://jupyterbook.org) and [fastpages](https://github.com/fastai/fastpages)

![]({{site.baseurl}}/images/diagram.png)

**Jupyter Book** has a clean layout that is also suitable for book publishing and a git-friendly format. On the other hand, **fastpages** is built for blogging. Although none of them is clearly better than the other, `fastpages` comes with github `actions` that are super easy to set up, so I went with it.

### `Fastai/fastpages` setup

One thing that I love about `fastpages` is how easy it is to get started. It takes you about 5 steps in 10 minutes to get a website deployed on github pages **with continuous delivery**. The fact that you don't need separate services for hosting, CMS, CI/CD or even a domain makes this a perfect fit for aspiring learners of data science/dataviz, who aren't always from an IT background, to start blogging. All they need is a github account.

The process starts with [one click](https://github.com/fastai/fastpages#setup-instructions), essentially `fork`ing the project into your github account, a bot then opens a pull request (`PR`) for you to configure with easy instructions. "easy" but obviously not like wordpress or wix. After all, this is for those who are at least interested in programming so you need to familiarize yourself with the concept of a github `repository`, opening and merging a PR, then later `commit` & `push`ing blog posts.

Once setup is done your site looks like this:

{::nomarkdown}
<iframe style=width:100%;height:50%;min-height:315px src=//fastpages.fast.ai/fastpages/jupyter/2020/02/21/introducing-fastpages.html></iframe>
{:/}

At this point you can start writing. Fastpages supports 3 formats: `md`, `ipynb` and `docx`. Perhaps the coolest feature is its built-in badges for instantly spinning up an execution environment for any `ipynb` script on binder and Google Colab, so you don't even need to install jupyter locally:

![]({{site.baseurl}}/images/binder_colab.png)

Supporting docx is also an interesting choice and I believe this is to make it more friendly to people who aren't geeks. If you have a CV in docx format and are using fastpages to showcase your works you can just chuck it in along side with the rest of your writting. Even as a web developer I have no shame in saying that I'm sometimes more comfortable with MS Word's borderless tables than css layout.

The folks at fastai published a tutorial on how to [blog using nothing more than github UI](https://www.fast.ai/2020/01/16/fast_template/).

There are a lot more to fastpages which you can have a look at the [README](https://github.com/fastai/fastpages) to find out. Out of the box, you can embed code, youtube videos & tweets. They are all powered by [Jekyll plugins](https://github.com/planetjekyll/awesome-jekyll-plugins) so if you are familiar with that ecosystem you can start tweaking the theme and adding plugins. For comments you can either use [disqus (needs set up)](https://desiredpersona.com/disqus-comments-jekyll/) or just host all the comments in your github repo to make your site self-contained.

**That's basically it about how I set up this site, stay tuned for my future notes**

[^1]: After writing this I found out [someone wrote a Jupyter plugin for Gatsby](https://gatsby-contrib.github.io/gatsby-transformer-ipynb/Three-Body%20Problem), I personally prefer nextjs but those who already have a site made with Gatsby can look into it.

[^2]: There is also [blogdown](https://bookdown.org/yihui/blogdown) if you are interest in using `Rmd` instead.
