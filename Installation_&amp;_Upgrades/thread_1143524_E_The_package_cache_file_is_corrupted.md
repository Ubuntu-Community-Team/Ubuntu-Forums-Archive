---
title: "E: The package cache file is corrupted"
date: 2009-04-30
forum: Installation &amp; Upgrades
---

### Post by W2IBC on 2009-04-30
E: The package cache file is corrupted
E: _cache->open() failed, please report.

getting that when i check for security updates. 9.04 *buntu

---

### Post by Sef on 2009-04-30
Applications > Accessories > Terminal

the copy and paste this code:

```
sudo apt-get update && sudo apt-get upgrade
```

Copy and paste any error messages here.

---

### Post by W2IBC on 2009-04-30
no errors there. maybe it was just a 1 time bug?

---

### Post by angora on 2009-04-30
I'm getting the same thing, but I can still install the updates okay, and it seems that the error only occurs when updates are available. So we probably need to wait for more updates to appear before running apt-get.

---

