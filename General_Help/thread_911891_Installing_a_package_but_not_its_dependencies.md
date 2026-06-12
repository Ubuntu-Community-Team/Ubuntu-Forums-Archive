---
title: "Installing a package but not its dependencies"
date: 2008-09-06
forum: General Help
---

### Post by meho_r on 2008-09-06
Hi,

I recently had this problem. I want to install a package (specifically kdegraphics which contains kdvi I need) but I don't want to install some of its dependencies (texlive and its "relatives" -- this because I've already installed newer version of it from DVD and don't want old one replace/mess up the new one). So, how can I do it? How to avoid dependencies install?

---

### Post by brian_p on 2008-09-06
> **meho_r said:**
> Hi,

I recently had this problem. I want to install a package (specifically kdegraphics which contains kdvi I need) but I don't want to install some of its dependencies (texlive and its "relatives" -- this because I've already installed newer version of it from DVD and don't want old one replace/mess up the new one). So, how can I do it? How to avoid dependencies install?

```
man dpkg
```

```
man apt-get
```

Search for 'force'.

Wouldn't xdvi in texlive be suitable and less fraught route than breaking dependencies?

---

### Post by meho_r on 2008-09-07
No, it wouldn't. I use Kile and Kdvi is perfect match for viewing .dvi files. And still no success in installing. Even force option doesn't help (I'm installing from Ubuntu repos) it still tries to install all dependencies.

---

