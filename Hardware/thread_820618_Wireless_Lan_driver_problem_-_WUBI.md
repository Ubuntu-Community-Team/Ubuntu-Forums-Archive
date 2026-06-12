---
title: "Wireless Lan driver problem - WUBI"
date: 2008-06-06
forum: Hardware
---

### Post by Gordonbp531 on 2008-06-06
Installed WUBI 8.04 on a Toshiba Satellite L40 that uses the Realtek 8187 WLan chip. I went to this site 
[http://www.datanorth.net/~cuervo/rtl8187b/](http://www.datanorth.net/~cuervo/rtl8187b/) for the driver, followed the instructions there but ran into a problem.
On issuing the ./makedrv command, this happened:
 rm -fr *.mod.c *.mod *.o .*.cmd *.mod.* *.ko *.o *~
make -C /lib/modules/2.6.24-16-generic/build M=/home/gordon/rtl8187b-modified/ieee80211 CC=gcc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
scripts/Makefile.build:46: *** CFLAGS was changed in "/home/gordon/rtl8187b-modified/ieee80211/Makefile". Fix it to use EXTRA_CFLAGS. Stop.
make[1]: *** [_module_/home/gordon/rtl8187b-modified/ieee80211] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [modules] Error 2
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
make -C /lib/modules/2.6.24-16-generic/build M=/home/gordon/rtl8187b-modified/rtl8187 CC=gcc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
scripts/Makefile.build:46: *** CFLAGS was changed in "/home/gordon/rtl8187b-modified/rtl8187/Makefile". Fix it to use EXTRA_CFLAGS. Stop.
make[1]: *** [_module_/home/gordon/rtl8187b-modified/rtl8187] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [modules] Error 2

Then when trying the ./wlan0up command I got this:
./wlan0up
insmod: can't read 'ieee80211_crypt-rtl.ko': No such file or directory
insmod: can't read 'ieee80211_crypt_wep-rtl.ko': No such file or directory
insmod: can't read 'ieee80211_crypt_tkip-rtl.ko': No such file or directory
insmod: can't read 'ieee80211_crypt_ccmp-rtl.ko': No such file or directory
insmod: can't read 'ieee80211-rtl.ko': No such file or directory
insmod: can't read 'r8187.ko': No such file or directory


Can anyone divine from all that what has gone wrong and whether it's a problem caused by using WUBI instead of a proper install?

Thanks

---

