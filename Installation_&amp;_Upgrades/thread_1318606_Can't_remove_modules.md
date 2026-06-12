---
title: "Can't remove modules"
date: 2009-11-07
forum: Installation &amp; Upgrades
---

### Post by billcauley on 2009-11-07
My upgrade to 9.10 isn't completing; getting the following error msgs:

E: linux-restricted-modules-2.6.28-13-generic: subprocess installed post-removal script returned error exit status 1
E: linux-restricted-modules-2.6.28-14-generic: subprocess installed post-removal script returned error exit status 1

Synaptic shows these module "ready for removal", but they don't get removed.  What should I do?

---

### Post by stlsaint on 2009-11-07
try in terminal:
```
sudo apt-get autoremove
```

or manual remove those packages

---

### Post by billcauley on 2009-11-08
No joy with autoremove! How do you manually remove packages?

---

