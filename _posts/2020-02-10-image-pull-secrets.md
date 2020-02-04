---
layout: post
title: imagePullPolicy and imagePullSecrets
categories: [Kubernetes, Docker]
---

# Drafty draft draft

Figured it's time I start actually blogging some stuff, so this is hopefully the first of a few blog posts covering some Docker/container notes. These will be more for my own reference than for public consumption, so typos are to be expected and corrections are more than welcome. 

Docker Registries are used to host Docker images, providing a centralised source for images to be stored. Anyone who wants to use the images can use `docker pull` to retrieve and run the images locally, or developers can make local changes and upload images through `docker push`. 

For testing, I've been using the basic Docker registry image from [the Docker hub](https://hub.docker.com/_/registry). 

```bash
docker pull registry
Using default tag: latest
latest: Pulling from library/registry
486039affc0a: Pull complete
<-- snip -->
Status: Downloaded newer image for registry:latest
docker.io/library/registry:latest
```

As a simple demo, let's create a Docker image from the [base nginx image](https://hub.docker.com/_/nginx) using the following Dockerfile.

```bash
FROM nginx:latest

COPY index.html /usr/share/nginx/html/index.html
COPY secret_file /usr/share/nginx/secret_file
```

We can build this image with the following command:

```bash
docker build -t nginx-secret-demo .
Sending build context to Docker daemon  4.608kB
Step 1/3 : FROM nginx
 ---> 2073e0bcb60e
Step 2/3 : COPY index.html /usr/share/nginx/html/index.html
 ---> 4c8a56b53c28
Step 3/3 : COPY secret_file /usr/share/nginx/secret_file
 ---> 6887da80f5e9
Successfully built 6887da80f5e9
Successfully tagged nginx-secret-demo:latest
```


[Reverie](https://github.com/amitmerchant1990/reverie) is a [Jekyll](https://jekyllrb.com/)-powered theme which is simple and opinionated. It's actually a fork of [jekyll-now](https://github.com/barryclark/jekyll-now) with some additional features and personal touches which I've implemented to suit my needs for my blog.

This is a plug-and-play Jekyll theme which you can use on GitHub Pages without even setting up a local environment.

![](/images/reverie-demo.png)

## Features overview

- Command-line free fork-first workflow, using GitHub.com to create, customize and post to your blog
- Fully responsive and mobile optimized base theme
- Sass/Coffeescript support using Jekyll 2.0
- Free hosting on your GitHub Pages user site
- All the SEO goodies comes in-built
- Markdown blogging
- Syntax highlighting using Pygments
    - [Dracula syntax theme](https://draculatheme.com/) included
- Disqus commenting
- Google Analytics integration
- Fuzzy search across blog posts
- Pagination of posts works out-of-the-box.
- Categorize posts out-of-the box
- RSS Feed
- In-built sitemap

<div style="text-align: center;">
 <script async type="text/javascript" src="//cdn.carbonads.com/carbon.js?serve=CE7D6KJY&placement=wwwamitmerchantcom" id="_carbonads_js"></script>
</div>

## Using Reverie on GitHub Pages

### Step 1) Fork Reverie to your User Repository

Fork [this repository](https://github.com/amitmerchant1990/reverie), then rename the repository to `yourgithubusername.github.io`.

Alternatively, you can use [Use this template](https://github.com/amitmerchant1990/reverie/generate) button if you want to create a repository with a clean commit history which will use Reverie as a template.

Your Jekyll blog will often be viewable immediately at <https://yourgithubusername.github.io> (if it's not, you can often force it to build by completing step 2)

### Step 2) Customize and view your site

Enter your site name, description, avatar and many other options by editing the `_config.yml` file. You can easily turn on Google Analytics tracking, Disqus commenting and social icons here.

Making a change to `_config.yml` (or any file in your repository) will force GitHub Pages to rebuild your site with jekyll. Your rebuilt site will be viewable a few seconds later at <https://yourgithubusername.github.io> - if not, give it ten minutes as GitHub suggests and it'll appear soon.

### Step 3) Publish your first blog post

Create a new file called `/_posts/2019-2-13-Hello-World.md` to publish your first blog post. That's all you need to do to publish your first blog post! This [Markdown Cheatsheet](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet) might come in handy while writing the posts.

> You can add additional posts in the browser on GitHub.com too! Just hit the <kbd>Create new file</kbd> button in `/_posts/` to create new content. Just make sure to include the [front-matter](http://jekyllrb.com/docs/frontmatter/) block at the top of each new blog post and make sure the post's filename is in this format: year-month-day-title.md

## Using Categories in Reverie

You can categorize your content based on `categories` in Reverie. For this, you just need to add `categories` in front matter like below:

For adding single category:

```md
categories: JavaScript
```

For adding multiple categories:

```md
categories: [PHP, Laravel]
```

The contegorized content can be shown over this URL: <https://yourgithubusername.github.io/categories/>




