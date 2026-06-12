---
title: "IPW 2200 monitor mode"
date: 2005-12-24
forum: Hardware &amp; Laptops
---

### Post by khateeb on 2005-12-24
Hi all

I am trying to put my Intel Pro wireless card into monitor mode. It keeps telling me the mode is not supported. I looked around for a driver using synaptic but found none. I found the driver at ipw2200.sourceforge.net downloaded it and it's dependancy 80211 driver (ieee80211.sf.net). Niether of them compile correctly.

I know I need to correct something in the "make" file to make the driver work in monitor mode. Can anyone tell me where I can find a package that is already customized.

Thanks in advance.

---

### Post by Rollmops on 2005-12-24
They do both compile. Check the subdirectories of /lib/modules and delete all ieee80211 and ipw2200 related files. Also unload both modules with
```
sudo modprobe -r ipw2200
```
and
```
sudo modprobe -r ieee80211
```
Then follow the instructions of the README. And don't forget to copy the firmware-files.
Perhaps you also need gcc version 3.4 to compile. Do you have the build-essential package and linux-headers installed?

---

### Post by khateeb on 2005-12-24
I have the nessesary linux headers installed (2.6.10-6-386) and I have GCC version 4.0 (at least this is what synaptic says) . IEEE80211 still does not compile. I m listing the error message below.

----------

[email]tareq@ubuntu:~/Desktop/ieee80211-1.1.6.tgz[/email]_FILES/ieee80211-1.1.6$ make IEEE80211 _INC=/usr/include
Checking in /lib/modules/2.6.10-6-386/build/ for ieee80211 components...

make -C /lib/modules/2.6.10-6-386/build M=/home/tareq/Desktop/ieee80211-1.1.6.tg z_FILES/ieee80211-1.1.6 MODVERDIR=/home/tareq/Desktop/ieee80211-1.1.6.tgz_FILES/ ieee80211-1.1.6 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.10-6-386'
  CC [M]  /home/tareq/Desktop/ieee80211-1.1.6.tgz_FILES/ieee80211-1.1.6/ieee8021 1_tx.o
/home/tareq/Desktop/ieee80211-1.1.6.tgz_FILES/ieee80211-1.1.6/ieee80211_tx.c:193 : error: syntax error before "gfp_mask"
/home/tareq/Desktop/ieee80211-1.1.6.tgz_FILES/ieee80211-1.1.6/ieee80211_tx.c:194 : warning: function declaration isn't a prototype
/home/tareq/Desktop/ieee80211-1.1.6.tgz_FILES/ieee80211-1.1.6/ieee80211_tx.c: In  function `ieee80211_alloc_txb':
/home/tareq/Desktop/ieee80211-1.1.6.tgz_FILES/ieee80211-1.1.6/ieee80211_tx.c:197 : error: `nr_frags' undeclared (first use in this function)
/home/tareq/Desktop/ieee80211-1.1.6.tgz_FILES/ieee80211-1.1.6/ieee80211_tx.c:197 : error: (Each undeclared identifier is reported only once
/home/tareq/Desktop/ieee80211-1.1.6.tgz_FILES/ieee80211-1.1.6/ieee80211_tx.c:197 : error: for each function it appears in.)
/home/tareq/Desktop/ieee80211-1.1.6.tgz_FILES/ieee80211-1.1.6/ieee80211_tx.c:198 : error: `gfp_mask' undeclared (first use in this function)
/home/tareq/Desktop/ieee80211-1.1.6.tgz_FILES/ieee80211-1.1.6/ieee80211_tx.c:204 : error: `txb_size' undeclared (first use in this function)
make[2]: *** [/home/tareq/Desktop/ieee80211-1.1.6.tgz_FILES/ieee80211-1.1.6/ieee 80211_tx.o] Error 1
make[1]: *** [_module_/home/tareq/Desktop/ieee80211-1.1.6.tgz_FILES/ieee80211-1. 1.6] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.10-6-386'
make: *** [modules] Error 2
[email]tareq@ubuntu:~/Desktop/ieee80211-1.1.6.tgz[/email]_FILES/ieee80211-1.1.6$ make IEEE80211 _INC=/usr/include
Checking in /lib/modules/2.6.10-6-386/build/ for ieee80211 components...

make -C /lib/modules/2.6.10-6-386/build M=/home/tareq/Desktop/ieee80211-1.1.6.tg z_FILES/ieee80211-1.1.6 MODVERDIR=/home/tareq/Desktop/ieee80211-1.1.6.tgz_FILES/ ieee80211-1.1.6 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.10-6-386'
  CC [M]  /home/tareq/Desktop/ieee80211-1.1.6.tgz_FILES/ieee80211-1.1.6/ieee8021 1_tx.o
/home/tareq/Desktop/ieee80211-1.1.6.tgz_FILES/ieee80211-1.1.6/ieee80211_tx.c:193 : error: syntax error before "gfp_mask"
/home/tareq/Desktop/ieee80211-1.1.6.tgz_FILES/ieee80211-1.1.6/ieee80211_tx.c:194 : warning: function declaration isn't a prototype
/home/tareq/Desktop/ieee80211-1.1.6.tgz_FILES/ieee80211-1.1.6/ieee80211_tx.c: In  function `ieee80211_alloc_txb':
/home/tareq/Desktop/ieee80211-1.1.6.tgz_FILES/ieee80211-1.1.6/ieee80211_tx.c:197 : error: `nr_frags' undeclared (first use in this function)
/home/tareq/Desktop/ieee80211-1.1.6.tgz_FILES/ieee80211-1.1.6/ieee80211_tx.c:197 : error: (Each undeclared identifier is reported only once
/home/tareq/Desktop/ieee80211-1.1.6.tgz_FILES/ieee80211-1.1.6/ieee80211_tx.c:197 : error: for each function it appears in.)
/home/tareq/Desktop/ieee80211-1.1.6.tgz_FILES/ieee80211-1.1.6/ieee80211_tx.c:198 : error: `gfp_mask' undeclared (first use in this function)
/home/tareq/Desktop/ieee80211-1.1.6.tgz_FILES/ieee80211-1.1.6/ieee80211_tx.c:204 : error: `txb_size' undeclared (first use in this function)
make[2]: *** [/home/tareq/Desktop/ieee80211-1.1.6.tgz_FILES/ieee80211-1.1.6/ieee 80211_tx.o] Error 1
make[1]: *** [_module_/home/tareq/Desktop/ieee80211-1.1.6.tgz_FILES/ieee80211-1. 1.6] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.10-6-386'
make: *** [modules] Error 2
------------------

Do I need to install some special library for it to compile or something?

---

