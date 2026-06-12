---
title: "Crystal HD driver install in 12.04 Precise"
date: 2012-07-03
forum: Hardware
---

### Post by Issssy on 2012-07-03
Since every  release seems to have specific issues with the CrystalHD drivers (and I didn't see a 12.04-specific thread), I'll start one.

Anyone have the Crystal HD card working in 12.04? I was able to get it working in 11.04 with various edits to the source before building the drivers, but now in 12.04 I am seeing new errors.

I tried loading the[COLOR=Blue] ["crystal HD" driver package]("https://launchpad.net/ubuntu/precise/+source/crystalhd/")[/COLOR] to no joy. (where does this get installed in the hierarchy, btw?)

I have tried building the drivers from the git source with no joy. I added the "include delay.h" and still get errors at "make":

$ make CONFIG_DEBUG_SECTION_MISMATCH=y

..yields:

make -C /lib/modules/3.2.0-26-generic/build SUBDIRS=/home/bill/crystalhd/driver/linux modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-26-generic'
  CC [M]  /home/bill/crystalhd/driver/linux/crystalhd_lnx.o
  CC [M]  /home/bill/crystalhd/driver/linux/crystalhd_misc.o
  CC [M]  /home/bill/crystalhd/driver/linux/crystalhd_cmds.o
  CC [M]  /home/bill/crystalhd/driver/linux/crystalhd_hw.o
  CC [M]  /home/bill/crystalhd/driver/linux/crystalhd_linkfuncs.o
  CC [M]  /home/bill/crystalhd/driver/linux/crystalhd_fleafuncs.o
/home/bill/crystalhd/driver/linux/crystalhd_fleafuncs.c: In function ‘crystalhd_flea_runtime_power_dn’:
/home/bill/crystalhd/driver/linux/crystalhd_fleafuncs.c:619:14: error: ‘regVal’ may be used uninitialized in this function [-Werror=uninitialized]
cc1: all warnings being treated as errors
make[2]: *** [/home/bill/crystalhd/driver/linux/crystalhd_fleafuncs.o] Error 1
make[1]: *** [_module_/home/bill/crystalhd/driver/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-26-generic'
make: *** [all] Error 2

Anyone have it working, and if so, please post how you did it?

Thanks,

Bill

---

### Post by markosjal on 2012-12-22
I installed from repos for Apple TV and it works "most" of the time. I had previously tried to install from source and had some ssues I think it was with documetation of "patches" . 

Sometimes I ned to reboot to get CHD decoding . I also noticed that if I instll another package I most always have to reinstall all crystalHD

I actually installed into xbmcbuntu beta 1 which is ubuntu 12.04 and running on Apple TV Gen 1

It is not exactly perfect. If I do a cold boot it i almost a gven it will not work

---

### Post by wirelessjohn-r on 2013-08-17
> **markosjal said:**
> I installed from repos for Apple TV and it works "most" of the time. I had previously tried to install from source and had some ssues I think it was with documetation of "patches" . 

Sometimes I ned to reboot to get CHD decoding . I also noticed that if I instll another package I most always have to reinstall all crystalHD

I actually installed into xbmcbuntu beta 1 which is ubuntu 12.04 and running on Apple TV Gen 1

It is not exactly perfect. If I do a cold boot it i almost a gven it will not work

Any joy with this? I found that it was only under VLC that my Crystal HD gave trouble device sa Frtw eh?

---

