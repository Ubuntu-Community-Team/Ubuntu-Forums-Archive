---
title: "Where is libmudflap.a?"
date: 2008-07-30
forum: General Help
---

### Post by mmmmhack on 2008-07-30
Hi, I have installed Ubuntu server 8.04.1 on an AMD Sempron model 8 (32 bit?) and I want to compile C++ programs with the mudflap bounds checker ([http://packages.debian.org/etch/libmudflap0]("http://packages.debian.org/etch/libmudflap0")). I need the file libmudflap.a, which is listed the Debian package libmudflap0-dev. However, when I install this package using apt-get, the file 'libmudflap.a' is not there.  Here are the only files that were installed:

$ dpkg -L libmudflap0-dev
/.
/usr
/usr/share
/usr/share/doc
/usr/share/doc/gcc-4.1-base
/usr/share/doc/gcc-4.1-base/mudflap
/usr/share/doc/gcc-4.1-base/mudflap/changelog.gz
/usr/include
/usr/include/mf-runtime.h
/usr/lib
/usr/lib/gcc
/usr/lib/gcc/i486-linux-gnu
/usr/lib/gcc/i486-linux-gnu/4.1
/usr/share/doc/libmudflap0-dev
/usr/lib/gcc/i486-linux-gnu/4.1/libmudflapth.so
/usr/lib/gcc/i486-linux-gnu/4.1/libmudflap.so

---

### Post by LaVache on 2009-03-03
I had this problem too.  The package **libmudflap0-dev** does not contain the static libraries as one might expect; however they can be found in package **libmudflap0-4.2-dev**.

So to get the static mudflap libs, install **libmudflap0-4.2-dev**.

---

