---
title: "libgtk2.0-dev: dependancies problem"
date: 2009-01-22
forum: Installation &amp; Upgrades
---

### Post by ANew on 2009-01-22
Seems like i can not install the package libgtk2.0-dev
and the problem is in dependant package libpango1.0-dev:
More precise, libpango requires package *libx11-dev*
which requires package xliv-dev, which itselt requires
*libx11-dev* again. This is like a loop or a circle.

Any suggestions how to resolve this?

---

### Post by taurus on 2009-01-22
Post your /etc/apt/sources.list.

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```

---

