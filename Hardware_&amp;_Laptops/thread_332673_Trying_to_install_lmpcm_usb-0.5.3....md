---
title: "Trying to install lmpcm_usb-0.5.3..."
date: 2007-01-06
forum: Hardware &amp; Laptops
---

### Post by ubuntu-mike022465 on 2007-01-06
Hey folks, I'm wondering if I can have some of your help here.  I'm trying to get my Logitech Mediaplay wireless mouse going, and have downloaded the latest lmpcm_usb from Freshmeat.

After untarring it, I did changed to the lmpcm_usb-0.5.3 directory, and tried make and this is what I got:

michael@michael-laptop:~/lmpcm_usb-0.5.3$ sudo make
make -C /lib/modules/2.6.17-10-generic/build SUBDIRS=/home/michael/lmpcm_usb-0.5.3 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
  CC [M]  /home/michael/lmpcm_usb-0.5.3/lmpcm_usb.o
/home/michael/lmpcm_usb-0.5.3/lmpcm_usb.c:615: error: unknown field ‘owner’ specified in initializer
/home/michael/lmpcm_usb-0.5.3/lmpcm_usb.c:615: warning: initialization from incompatible pointer type
make[2]: *** [/home/michael/lmpcm_usb-0.5.3/lmpcm_usb.o] Error 1
make[1]: *** [_module_/home/michael/lmpcm_usb-0.5.3] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
make: *** [default] Error 2

I thought there might be the lmpcm package in the repositories, but no dice.  I've installed build-essentials and changed from gcc-4.1 back to gcc-3.4 with
CC=gcc-3.4
export CC

still nothing works.

Any advice is greatly appreciated.

Thanks in advance

M.

---

### Post by ubuntu-mike022465 on 2007-01-06
Bump? :rolleyes:

---

