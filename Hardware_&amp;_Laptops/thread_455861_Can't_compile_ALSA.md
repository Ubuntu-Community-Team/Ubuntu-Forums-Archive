---
title: "Can't compile ALSA"
date: 2007-05-27
forum: Hardware &amp; Laptops
---

### Post by imrazor on 2007-05-27
I have an Echo Indigo IO. Since the driver for the Echo is not included with Ubuntu, it requires that I build the ALSA driver from source. After downloading and unpacking the ALSA 1.0.13 driver, I ran ./configure successfully. However, when I try "make", I get the following:

make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/usr/src/alsa-driver-1.0.13  CPP="gcc -E" CC="gcc" modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /usr/src/alsa-driver-1.0.13/acore/hwdep.o
In file included from /usr/src/alsa-driver-1.0.13/include/sound/driver.h:46,
                 from /usr/src/alsa-driver-1.0.13/acore/hwdep.c:22:
/usr/src/alsa-driver-1.0.13/include/adriver.h:742: error: redefinition of ‘jiffies_to_msecs’
include/linux/jiffies.h:268: error: previous definition of ‘jiffies_to_msecs’ was here
/usr/src/alsa-driver-1.0.13/include/adriver.h:761: error: redefinition of ‘msecs_to_jiffies’
include/linux/jiffies.h:290: error: previous definition of ‘msecs_to_jiffies’ was here
In file included from /usr/src/alsa-driver-1.0.13/include/adriver.h:858,
                 from /usr/src/alsa-driver-1.0.13/include/sound/driver.h:46,
                 from /usr/src/alsa-driver-1.0.13/acore/hwdep.c:22:
include/linux/pci.h:541: error: expected identifier or ‘(’ before numeric constant
In file included from /usr/src/alsa-driver-1.0.13/include/sound/driver.h:46,
                 from /usr/src/alsa-driver-1.0.13/acore/hwdep.c:22:
/usr/src/alsa-driver-1.0.13/include/adriver.h: In function ‘snd_pci_orig_save_state’:
/usr/src/alsa-driver-1.0.13/include/adriver.h:1099: error: too many arguments to function ‘pci_save_state’
/usr/src/alsa-driver-1.0.13/include/adriver.h: In function ‘snd_pci_orig_restore_state’:
/usr/src/alsa-driver-1.0.13/include/adriver.h:1103: error: too many arguments to function ‘pci_restore_state’
make[3]: *** [/usr/src/alsa-driver-1.0.13/acore/hwdep.o] Error 1
make[2]: *** [/usr/src/alsa-driver-1.0.13/acore] Error 2
make[1]: *** [_module_/usr/src/alsa-driver-1.0.13] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [compile] Error 2

Anyone know how to fix this?

---

