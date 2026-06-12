---
title: "Webcam installation. Driver build problems."
date: 2009-04-09
forum: Hardware
---

### Post by Ahrim on 2009-04-09
Hello first post here so pardon if I have misposted.

I'm trying to get this webcam to work, lsusb lists it as:

Bus 005 Device 002: ID 0ac8:307b Z-Star Microelectronics Corp. USB 1.1 WebCam


Which if I'm not mistaken is supported by the GSPCA driver.
So I originally extracted that driver to /usr/src/ and ran make which led to this error:

make -C /lib/modules/`uname -r`/build SUBDIRS=/usr/src/gspcav1-20071224 CC=cc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
make[1]: *** No rule to make target `modules'. Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
make: *** [default] Error 2

Disappointed I ran:

sudo apt-get install build-essential linux-headers-$(uname -r)

To make sure everything was in order, it was. Though it does say I no longer need libindicate0.

So I tried the module-assistant. Prepare, selected the drivers, update drivers, tried to build and...:

&#9474; Bad luck, the kernel headers for the target kernel version could &#9618;
&#9474; not be found &#9618;
&#9474; and you did not specify other valid kernel headers to use.

And it recommends I prepare the headers which I did above.

So, can anyone help?

---

### Post by Ahrim on 2009-04-10
Bump

---

