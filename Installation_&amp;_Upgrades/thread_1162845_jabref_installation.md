---
title: "jabref installation"
date: 2009-05-18
forum: Installation &amp; Upgrades
---

### Post by two23 on 2009-05-18
I am new to linux and am having trouble installing jabref.  When I type jabref into the synaptic package manager, nothing comes out.  When I type:

sudo apt-get install jabref

i get this:

Package jabref is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package jabref has no installation candidate


not sure what to do.

---

### Post by Partyboi2 on 2009-05-18
Hi, open up Software Sources (System>Admin>Software Sources) and under the 1st tab make sure you have the mulitiverse repo enabled, then reload the package  list.
```
sudo apt-get update
```
```
sudo apt-get install jabref
```

---

