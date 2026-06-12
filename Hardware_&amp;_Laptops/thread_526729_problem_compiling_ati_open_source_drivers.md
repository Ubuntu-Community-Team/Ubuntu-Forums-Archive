---
title: "problem compiling ati open source drivers"
date: 2007-08-15
forum: Hardware &amp; Laptops
---

### Post by lynndylan on 2007-08-15
I'm using [this]("http://www.phoronix.com/scan.php?page=article&item=806&num=1") guide to build and install the ati driver with tv-out enabled.  I can compile it without errors, but when i use the "make" command it gives me this:

```
make  all-recursive
make[1]: Entering directory `/home/lynn/Desktop/xf86-video-ati'
Making all in src
make[2]: Entering directory `/home/lynn/Desktop/xf86-video-ati/src'
/bin/bash ../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I..    -I/usr/include/xorg   -I/usr/include/drm -I/usr/include/X11/dri   -g -O2 -MT ati.lo -MD -MP -MF .deps/ati.Tpo -c -o ati.lo ati.c
 gcc -DHAVE_CONFIG_H -I. -I.. -I/usr/include/xorg -I/usr/include/drm -I/usr/include/X11/dri -g -O2 -MT ati.lo -MD -MP -MF .deps/ati.Tpo -c ati.c  -fPIC -DPIC -o .libs/ati.o
In file included from ati.c:65:
radeon_probe.h:46:22: error: xf86Crtc.h: No such file or directory
In file included from ati.c:65:
radeon_probe.h:225: error: expected specifier-qualifier-list before 'xf86CrtcPtr'
ati.c:228: error: 'PACKAGE_VERSION_MAJOR' undeclared here (not in a function)
ati.c:228: error: 'PACKAGE_VERSION_MINOR' undeclared here (not in a function)
ati.c:228: error: 'PACKAGE_VERSION_PATCHLEVEL' undeclared here (not in a function)
make[2]: *** [ati.lo] Error 1
make[2]: Leaving directory `/home/lynn/Desktop/xf86-video-ati/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/lynn/Desktop/xf86-video-ati'
make: *** [all] Error 2
```
 
I think I'm missing a dev package, but I can't figure out which one.  Can any one help?

Thanks,
Lynn

---

### Post by PaulFr on 2007-08-16
Maybe this will help: xf86Crtc.h is AFAIK defined only in the 1.3 version of the X.org Server, whereas the default version in 7.04 is version 1.2.

---

### Post by lynndylan on 2007-08-17
Thanks Paul!  I upgraded to gutsy and was able to compile everything.

---

