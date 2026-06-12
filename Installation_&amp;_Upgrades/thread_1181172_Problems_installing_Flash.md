---
title: "Problems installing Flash"
date: 2009-06-07
forum: Installation &amp; Upgrades
---

### Post by Barryes123 on 2009-06-07
I just installed Ubuntu 9 on my x86 desktop, when I go to install flash on a debian package it says DEPENDENCY IS NOT SATISFACTORY-LIBCURL6. Could someone help me please?

---

### Post by zvacet on 2009-06-08
Go to the system>admin>software sources and check all under Ubuntu software and first two under updates tab.Reload.Then go to the applications>accessories>terminal and type

```
sudo apt-get install ubuntu-restricted-extras
```

---

