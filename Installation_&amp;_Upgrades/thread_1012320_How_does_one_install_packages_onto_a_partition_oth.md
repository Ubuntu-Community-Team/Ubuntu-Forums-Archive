---
title: "How does one install packages onto a partition other than the active directory?"
date: 2008-12-15
forum: Installation &amp; Upgrades
---

### Post by Joshamuffin on 2008-12-15
How does one install packages onto a partition other than the active directory?

In Windows, it was easy to install things to any directory. However, because of the nature of installation, I do not know how to do the same thing in Linux.

---

### Post by taurus on 2008-12-15
Are they .deb packages?

---

### Post by maybeway36 on 2008-12-15
You essentially have to install .deb packages to /usr/bin. Linux has a rigid directory structure, which means you can't install to another partition, unless you really know what you're doing (usually means compiling from source.)

---

