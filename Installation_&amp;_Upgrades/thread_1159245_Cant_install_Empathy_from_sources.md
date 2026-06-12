---
title: "Cant install Empathy from sources"
date: 2009-05-14
forum: Installation &amp; Upgrades
---

### Post by men28 on 2009-05-14
Hi!

I am trying install Empathy 2.26.1 from sources.
When I run command:
./autogen.sh --prefix=/usr

I receive next output:

```

...

Copying file po/Makefile.in.in

Please add the files
  codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
  progtest.m4
from the /aclocal directory to your autoconf macro directory
or directly to your aclocal.m4 file.
You will also need config.guess and config.sub, which you can get from
ftp://ftp.gnu.org/pub/gnu/config/.

Running intltoolize...
Running gtkdocize...
Running gnome-doc-common...
Running gnome-doc-prepare...
You should update your 'aclocal.m4' by running aclocal.
Putting files in AC_CONFIG_MACRO_DIR, 'm4'.
Running aclocal-1.10...
configure.ac:72: warning: macro `AM_GCONF_SOURCE_2' not found in library
Running autoconf...
configure.ac:72: error: possibly undefined macro: AM_GCONF_SOURCE_2
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.

```

Thanks for help.

---

