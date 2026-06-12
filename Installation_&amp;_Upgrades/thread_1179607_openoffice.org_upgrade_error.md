---
title: "openoffice.org upgrade error"
date: 2009-06-05
forum: Installation &amp; Upgrades
---

### Post by Matt26 on 2009-06-05
can anyone tell me what this means?  i've tried removing and reinstalltion openoffice and i get the same error.

E: /var/cache/apt/archives/openoffice.org-base-core_1%3a3.1.0-3ubuntu2~jaunty1_i386.deb: short read in buffer_copy (backend dpkg-deb during `./usr/lib/openoffice/basis3.1/program/libdbali.so')

---

### Post by Partyboi2 on 2009-06-05
Hi, try cleaning the cache first```
 sudo apt-get clean
``` before reinstalling the package if you have not already done so.

---

### Post by Matt26 on 2009-06-06
> **Partyboi2 said:**
> Hi, try cleaning the cache first```
 sudo apt-get clean
``` before reinstalling the package if you have not already done so.

thanks, that did the trick!

---

