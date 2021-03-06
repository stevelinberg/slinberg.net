---
title: Adding "Edit this page" links
author: R package build
date: '2021-05-27'
slug: adding-edit-this-page-links
categories: []
tags: [hugo, github, wowchemy]
subtitle: ''
summary: ''
authors: []
lastmod: '2021-05-27T20:34:46-04:00'
featured: no
image:
  caption: ''
  focal_point: ''
  preview_only: no
projects: []
---

Here's how the cool Hugo/[Wowchemy](https://wowchemy.com/) kids add those groovy "Edit this page" elements to their pages in the [academic-starter](https://github.com/wowchemy/starter-hugo-academic) theme:

In `config/_default/params.yaml`, find the section `edit_page` and:

☞︎ Set `repo_url` to the URL of your repository (here, github)  
☞︎ Set `content_dir` to the directory of your site's content, `content` by default)  
☞︎ Set `repo_branch` to your repo's published branch; I use `master` rather than `main`)  

Then set the `editable` fields as needed for the types of content you want these links to be present in.

Here's the code from this site:

```yaml
edit_page:
  repo_url: 'https://github.com/slinberg-umass/slinberg.net'
  content_dir: 'content'
  repo_branch: master
  editable:
    page: true
    post: true
    book: true
```

That's all you need to do; when you rebuild, if the `edit_page` parameters are not empty, Hugo will insert the link as directed by the templates. This is the bit of triggering code:

```hugo
{{ partial "page_edit" . }}
```

It is contained in various inherited templates such as `themes/github.com/wowchemy/wowchemy-hugo-modules/wowchemy/layouts/partials/page_footer.html`, and the code is in  `themes/github.com/wowchemy/wowchemy-hugo-modules/wowchemy/layouts/partials/page_edit.html`.

Look at the code to see, among other things, that it can be overridden on a specific page or post by adding `editable: false` to its `yaml` header.

But we're not doing that in this case, so falling off the bottom of the content here, we get the groovy link to the page source below (note, you'll need to fork the repo to actually see it, it's more for me than for you):
