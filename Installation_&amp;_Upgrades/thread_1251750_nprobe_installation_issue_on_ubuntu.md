---
title: "nprobe installation issue on ubuntu"
date: 2009-08-28
forum: Installation &amp; Upgrades
---

### Post by frogger1 on 2009-08-28
Hallo everyone,

i am new here and i am not so familiar with ubuntu and thats why i need your help.

I try to install nprobe on ubuntu but i get the error message -when i use "sudo make":

libtool: Version mismatch error.  This is libtool 2.2, but the
libtool:  definition of this LT_INIT comes from an older release.
libtool: You should  recreate aclocal.m4 with macros from libtool 2.2
libtool: and run autoconf  again.
make[2]: *** [collect.lo] Fehler 63
make[2]: Verlasse Verzeichnis  '/home/kalle/nprobe'
make[1]: *** [all-recursive] Fehler 1
make[1]:  Verlasse Verzeichnis '/home/kalle/nprobe'
make: *** [all] Fehler 2

I use:
-ubuntu 8.04.3
-libtool-2.2
-m4 1.4.13
-autoconf 2.64
-automake 1.11
-flex 2.5.31
-libcap 1.0.0
-nprobe 5.2.9

Please, can anyone troubleshoot this with me.

regards
Hugo

---

### Post by frogger1 on 2009-08-30
found the fix.
[http://fi-blog.de/?p=123](http://fi-blog.de/?p=123)

---

