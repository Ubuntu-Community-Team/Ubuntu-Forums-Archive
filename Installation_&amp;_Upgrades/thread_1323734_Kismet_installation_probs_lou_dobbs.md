---
title: "Kismet installation probs lou dobbs"
date: 2009-11-12
forum: Installation &amp; Upgrades
---

### Post by sawick61 on 2009-11-12
When compiling Kismet I get the following error messages

**configure: error: Neither uclibc uClibc++ or standard gcc stdc++ libraries found**

i assume its because i need a c++ compiler.  so i tried gcc but when executing "make" go the following 
[B]
95.1/gcc/ch/runtime/" "CHILL_LIB=-lchill" "GNUCHILL_VERSION=1.5.2" ../cc1chill
make[2]: Entering directory `/etc/gcc-2.95.1/gcc/ch'
gcc -c  -DIN_GCC   -g -O2     -I. -I.. -I. -I./.. -I./../config -I./../../include decl.c
decl.c: In function ‘start_struct’:
decl.c:4451: error: argument ‘code’ doesn’t match prototype
ch-tree.h:736: error: prototype declaration
make[2]: *** [decl.o] Error 1
make[2]: Leaving directory `/etc/gcc-2.95.1/gcc/ch'
make[1]: *** [cc1chill] Error 2
make[1]: Leaving directory `/etc/gcc-2.95.1/gcc'
make: *** [all-gcc] Error 2
[/B]

any suggestions would be much appreciated.  i saw other posts but resolve via command line would be much appreciated.

---

