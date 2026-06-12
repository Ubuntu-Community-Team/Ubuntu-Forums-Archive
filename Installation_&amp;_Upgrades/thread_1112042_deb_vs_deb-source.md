---
title: "deb vs deb-source?"
date: 2009-03-31
forum: Installation &amp; Upgrades
---

### Post by Kareeser on 2009-03-31
Hey all,

When adding repositories to the "Software Sources" (i.e. WINE, or Transmission), the instructions ask to add two lines... a deb, and a deb-source.

What would the latter be used for? Do I need it?

---

### Post by lykwydchykyn on 2009-03-31
You only need it if you plan to download source code and compile things manually.  If you only plan to install binary (pre-compiled .deb) packages from that repository, then you don't need it.

To make a long story short, if you don't know what it is, you don't need it.

EDIT: basically, if you have deb-src repos enabled, you can use the apt-src or apt-get source commands to download the sourcecode of packages.

---

### Post by Kareeser on 2009-04-03
Ah. Fair enough. Thanks!

---

