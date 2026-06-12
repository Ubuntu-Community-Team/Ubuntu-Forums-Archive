---
title: "Override version selected by apt-get?"
date: 2009-05-16
forum: Installation &amp; Upgrades
---

### Post by pantherman007 on 2009-05-16
Sorry if this is posted in the wrong place - it may be a beginner question or belong elsewhere.

I think I need to override the version of a package that I'm trying to install with apt-get.  I'm typing:

sudo apt-get install libcurl4-dev

But instead of installing libcurl4-dev, Ubuntu overrides what I entered and instead goes with:

"Note, selecting libcurl4-gnutls-dev instead of libcurl4-dev"

Problem is, XBMC is specifically looking for libcurl4-dev and segfaults.

How can I force apt-get to install what I want it to instead of what it wants to?  I'm running 9.04.

Thanks -

---

### Post by x33a on 2009-05-16
is that package available in the repos?

try
```
aptitude show libcurl4-dev
```

if it shows up, then

```
sudo aptitude install libcurl4-dev
```

---

