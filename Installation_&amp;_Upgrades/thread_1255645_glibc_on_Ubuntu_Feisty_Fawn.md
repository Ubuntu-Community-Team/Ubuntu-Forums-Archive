---
title: "glibc on Ubuntu Feisty Fawn"
date: 2009-09-01
forum: Installation &amp; Upgrades
---

### Post by Enertia on 2009-09-01
I am new to linux and this is a bit long, so please bare with me.

I am using an older version of Ubuntu, Feisty Fawn, i know its old i will be upgrading it soon but i have a few questions anyway.

Also since there are no repositories available for Feisty hence i have been dowloading tar.gz files.

I want to install glibc.
Initially i was having problems with "/configure" i was getting the message "configure: error: you must configure in a separate build directory" even though my path was "/usr/src/gnu/glibc-build$", a user in a different forum suggested using the command

"sr/src/glibc-build#> /usr/src/glibc-*.*/configure"

My first question is **i don't understand this, why do i need to type "/usr/src/glibc-*.*" before configure when i already am in that folder**


This worked in getting rid of that error, but now i am getting
"checking how to run the C preprocessor... /lib/cpp
configure: error: C preprocessor "/lib/cpp" fails sanity check"
Below is a portion of the config.log

## ----------- ##
## Core tests. ##
## ----------- ##

configure:2182: checking build system type
configure:2200: result: i686-pc-linux-gnulibc1
configure:2222: checking host system type
configure:2237: result: i686-pc-linux-gnulibc1
configure:2417: running configure fragment for add-on nptl
configure:2554: checking sysdep dirs
configure:2790: result: sysdeps/generic/elf sysdeps/generic
configure:2868: checking for a BSD-compatible install
configure:2924: result: /usr/bin/install -c
configure:2939: checking whether ln -s works
configure:2943: result: yes
configure:2999: checking for gcc
configure:3015: found /usr/bin/gcc
configure:3026: result: gcc
configure:3264: checking for C compiler version
configure:3271: gcc --version >&5
gcc (GCC) 4.1.2 (Ubuntu 4.1.2-0ubuntu4)
Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions. There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

configure:3274: $? = 0
configure:3281: gcc -v >&5
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,fortran,objc,obj-c++,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --program-suffix=-4.1 --enable-__cxa_atexit --enable-clocale=gnu --enable-libstdcxx-debug --enable-mpfr --enable-checking=release i486-linux-gnu
Thread model: posix
gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)
configure:3284: $? = 0
configure:3291: gcc -V >&5
gcc: '-V' option must have argument
configure:3294: $? = 1
configure:3298: checking for suffix of object files
configure:3324: gcc -c conftest.c >&5
configure:3327: $? = 0
configure:3350: result: o
configure:3354: checking whether we are using the GNU C compiler
configure:3383: gcc -c conftest.c >&5
configure:3389: $? = 0
configure:3406: result: yes
configure:3411: checking whether gcc accepts -g
configure:3441: gcc -c -g conftest.c >&5
configure:3447: $? = 0
configure:3546: result: yes
configure:3563: checking for gcc option to accept ISO C89
configure:3637: gcc -c -g -O2 conftest.c >&5
conftest.c:10:19: error: stdio.h: No such file or directory
conftest.c:11:23: error: sys/types.h: No such file or directory
conftest.c:12:22: error: sys/stat.h: No such file or directory
conftest.c:15: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
conftest.c:49: error: expected declaration specifiers or '...' before 'FILE'
configure:3643: $? = 1


After a bit of googling i found someone having a similar problem not with glibc but a similar error with a different application, a few readers responded him by suggesting installing GCC. I accessed the synatic Package manager searched for GCC and shows in status as installed. I have to GCC files in my usr/bin namely "gcc-4.1" of type executable. so my second question is **do i have GCC?, if so what am i doing wrong?**

Thanks

---

### Post by Enertia on 2009-09-02
anyone?

---

