---
title: "list packages"
date: 2009-08-13
forum: Installation &amp; Upgrades
---

### Post by doru001 on 2009-08-13
I know that 
```
dpkg --get-selections # and
dpkg -l
```list installed packages. 

Please tell me what uninstalled packages do the following two commands list, what is the difference between them?
```
dpkg -l \* | wc -l
852
apt-cache search . | wc -l
25211
```I suppose that
```
apt-cache pkgnames | wc -l
32633 
```includes some older versions packages.

---

