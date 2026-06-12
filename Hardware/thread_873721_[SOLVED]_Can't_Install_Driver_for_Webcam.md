---
title: "[SOLVED] Can't Install Driver for Webcam?"
date: 2008-07-29
forum: Hardware
---

### Post by VivaLaEva on 2008-07-29
I have a Sony Vaio VGN-FE890, with an embedded Motion Eye webcam by Riccoh.  The proper driver is called r5u870, and I've downloaded it from different places about 5 or 6 different times, all hoping it would work.

Unfortunately when I finally managed to point the terminal in the correct directory [even after adding 3rd party software, the Package Manager wouldn't detect it except for the "kernel source" which I tried installing, and did absolutely no good].

This is what happens when I try and run make:

> make -C /lib/modules/2.6.24-19-generic/build M=/home/eva/r5u870-0.10.0 V=0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /home/eva/r5u870-0.10.0/r5u870_md.o
In file included from /home/eva/r5u870-0.10.0/r5u870_md.c:55:
/home/eva/r5u870-0.10.0/usbcam.h:36:29: error: media/video-buf.h: No such file or directory
make[2]: *** [/home/eva/r5u870-0.10.0/r5u870_md.o] Error 1
make[1]: *** [_module_/home/eva/r5u870-0.10.0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [all] Error 2

Any ideas of what I did wrong or what I need to do?

---

### Post by phidia on 2008-07-29
Please take a look at [the thread here]("http://ubuntuforums.org/showthread.php?t=706530") on your webcam.

---

