---
title: "Using gift-wrap to package Mupen64 (version 0.5)"
date: 2009-07-25
forum: Installation &amp; Upgrades
---

### Post by afroman10496 on 2009-07-25
How do I do this- packaging Mupen64 from .tar.bz2 to .deb with GiftWrap? When I try, I get:

dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
dpkg-buildpackage: source package mupen64
dpkg-buildpackage: source version 0.5-1
dpkg-buildpackage: source changed by Joe Lawrence <joe@unknown>
dpkg-buildpackage: host architecture i386
dpkg-checkbuilddeps: Unmet build dependencies: autotools-dev
dpkg-buildpackage: warning: Build dependencies/conflicts unsatisfied; aborting.
dpkg-buildpackage: warning: (Use -d flag to override.)

Thanks in advance!

---

### Post by Partyboi2 on 2009-07-26
>  dpkg-checkbuilddeps: Unmet build dependencies: autotools-devHi, looks to me that you have unmet dependencies. Try installing the autotools-dev package
```
sudo apt-get install autotools-dev
```

---

### Post by afroman10496 on 2009-07-27
I already said thanks in advance... but, again, THANKS!:P

---

