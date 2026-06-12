---
title: "Missing i2c-isa.h, hwmon.h and hwmon-vid.h"
date: 2006-02-10
forum: Hardware &amp; Laptops
---

### Post by ihristov on 2006-02-10
I have a VIA EPIA board and I need the vt1211 module to read the temperature.

I have a problem compiling vt1211.c

It can't find the header files i2c-isa.h, hwmon.h and hwmon-vid.h

Where do I find these?

I have installed the kernel-headers package and the lm-sensors package. Even tried the source package of lm-sensors, but these headers are nowhere to be found. One would think they are supposed to be in the kernel (since 2.6 now includes the i2c stuff in the kernel itself)

~/vt1211/vt1211.c:52:27: linux/i2c-isa.h: No such file or directory
~/vt1211/vt1211.c:53:25: linux/hwmon.h: No such file or directory
~/vt1211/vt1211.c:54:29: linux/hwmon-vid.h: No such file or directory

---

### Post by ihristov on 2006-02-14
To answer my own ?

It turned out I was trying to compile the driver for a more recent kernel.

The correct source [vt1211.c]("http://debian.jox.be/vt1211-source_20050319.orig.tar.gz") compiles and runs just fine with the default Breezy kernel (2.6.12-9-386)

I got help here.
[http://forums.viaarena.com/messageview.aspx?catid=28&threadid=70518&enterthread=y]("http://forums.viaarena.com/messageview.aspx?catid=28&threadid=70518&enterthread=y")

---

