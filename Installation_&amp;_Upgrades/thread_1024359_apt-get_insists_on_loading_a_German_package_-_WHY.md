---
title: "apt-get insists on loading a German package - WHY?"
date: 2008-12-28
forum: Installation &amp; Upgrades
---

### Post by celem on 2008-12-28
When using apt-get or Synaptic via GUI to install tesseract-ocr, it insists on also loading tesseract-ocr-deu, which is the German package. My system is setup for English so WHY is this happening?

---

### Post by kunixos on 2008-12-29
It's possible that the repository you are set up for does not have the English version of that package. Try downloading the package and doing a ```
dpkg -i packagename
```it should resolve dependencies on the fly.

Let me know how this works!

---

### Post by celem on 2008-12-29
I had successfully loaded tesseract and the english package. My issue is WHY does loading the main tesseract-ocr package insist on also loading the German package? I had to load the English package as an extra. I have attempted to upload an image of the Synaptic Package Manager window,

---

