---
title: "canon MP150 &amp; gutenprint CVS"
date: 2006-11-04
forum: Hardware &amp; Laptops
---

### Post by cd-r80 on 2006-11-04
If someone could try to compile gutenprint CVS (5.10) & tell how to do it. Some people perhaps could start using their Canon MP150 printer before throwing it to the wall. Using Xubuntu 6.06

I got errors & problems and fixed some, but:
You should add the contents of `/usr/share/aclocal/libtool.m4' to `aclocal.m4'.
Putting files in AC_CONFIG_AUX_DIR, `scripts'.

src/gutenprintui2/Makefile.am:34: The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
src/gutenprintui2/Makefile.am:34: to `configure.ac' and run `aclocal' and `autoconf' again.
src/main/Makefile.am:82: Libtool library used but `LIBTOOL' is undefined

configure.ac:147: error: possibly undefined macro: AC_LIBTOOL_DLOPEN
      If this token and others are legitimate, please use m4_pattern_allow.

Is there ideas?

---

