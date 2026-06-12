---
title: "Dependency Get?"
date: 2009-02-06
forum: Installation &amp; Upgrades
---

### Post by dragos240 on 2009-02-06
I want to compile things at ease from source, but i have to spend hours trying to find the correct dependencies for it. Is there a program or place where i can find the dependencies for it.

---

### Post by Tibuda on 2009-02-06
If the program is in the repositories, you can call```
sudo apt-get build-dep package
```to install all dependencies needed to build that package. If it is not, you can try [auto-apt]("apt:auto-apt").

---

### Post by kk0sse54 on 2009-02-06
try out a sourced based distro

---

### Post by dragos240 on 2009-02-06
> **C!oud said:**
> try out a sourced based distro

Elaborate please?

---

### Post by kk0sse54 on 2009-02-06
Linux distros where all packages are installed through compiling them from source, best example would be Gentoo. Otherwise you can try Archlinux which through it's default package manager allows you to install binary packages but if you install yaourt you can compile away as much as you would like giving you a nice blend.

---

### Post by smartboyathome on 2009-02-06
> **C!oud said:**
> Linux distros where all packages are installed through compiling them from source, best example would be Gentoo. Otherwise you can try Archlinux which through it's default package manager allows you to install binary packages but if you install yaourt you can compile away as much as you would like giving you a nice blend.

Don't forget ABS in Arch Linux. CRUX is another honerable mention for source-based distros.

---

### Post by kk0sse54 on 2009-02-07
> **smartboyathome said:**
> Don't forget ABS in Arch Linux. CRUX is another honerable mention for source-based distros.

Gentoo, CRUX, Lunar, Sorcerer, Source Mage, ports & pkgsrc in *BSD, and Arch to a certain extent

---

### Post by dragos240 on 2009-02-07
Can these features be incorporated into my ubuntu?

---

### Post by urukrama on 2009-02-07
Most applications mention the dependencies you need to have installed before compiling from source. Check the website, or either the README or INSTALL file in the source code archive you've downloaded.

If you compile with ./configure make and make install, you should find out if you are missing any dependencies in the first step (./configure). It will display an error message, telling you "Couldn't find xyz" and end. Search the repositories for that package (often you need to add lib to it, ie. libxyz), install the package and rerun ./configure. In this way you should find out the lacking dependencies pretty quickly.

---

### Post by dragos240 on 2009-02-07
> **urukrama said:**
> Most applications mention the dependencies you need to have installed before compiling from source. Check the website, or either the README or INSTALL file in the source code archive you've downloaded.

If you compile with ./configure make and make install, you should find out if you are missing any dependencies in the first step (./configure). It will display an error message, telling you "Couldn't find xyz" and end. Search the repositories for that package (often you need to add lib to it, ie. libxyz), install the package and rerun ./configure. In this way you should find out the lacking dependencies pretty quickly.

Thanks :D

---

### Post by oldos2er on 2009-02-07
auto-apt

---

### Post by bapoumba on 2009-02-07
Moved to Installation & Upgrades.

---

