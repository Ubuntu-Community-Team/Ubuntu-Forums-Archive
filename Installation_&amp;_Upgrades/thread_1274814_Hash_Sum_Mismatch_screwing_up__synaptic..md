---
title: "Hash Sum Mismatch screwing up  synaptic."
date: 2009-09-25
forum: Installation &amp; Upgrades
---

### Post by ucal on 2009-09-25
So I've tried to install 2 separate programs, Amarok and Flash.  Both times they've failed due to a hash sum mismatch preventing the installation or download (don't know which) of a crucial file.  I've switched from US to Main in software sources, but no luck.  Any ideas?

---

### Post by Partyboi2 on 2009-09-25
Try clearing out the cache first before installing the packages.
```
sudo apt-get clean
```

---

### Post by ucal on 2009-09-25
Thank you, that worked.

---

