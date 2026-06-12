---
title: "Problem with Conexant USB Modem ID 17EF:7000"
date: 2012-06-22
forum: Hardware
---

### Post by fox1t on 2012-06-22
I bought this modem from lenovo [http://www.ebay.it/itm/300673113130?ssPageName=STRK:MEWNX:IT&_trksid=p3984.m1439.l2649#ht_2847wt_1194](http://www.ebay.it/itm/300673113130?ssPageName=STRK:MEWNX:IT&_trksid=p3984.m1439.l2649#ht_2847wt_1194)
The drivers for this device are [http://www.linuxant.com/drivers/dgc/install.php](http://www.linuxant.com/drivers/dgc/install.php) , but when i install them and lunch dgcconfig i got this error that is preventing me to use it:
 
ERROR: Module build failed!
Please examine the log file "/tmp/dgcconfig-buildlog.txt" to determine why.
Here is the dump of buildlog.txt

(cd /lib/modules/3.2.0-23-generic/build && make "CNXT_KERNELSRC=/lib/modules/3.2.0-23-generic/build" "M=/usr/lib/dgcmodem/modules" "CC=gcc" clean)
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-23-generic'
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-23-generic'
rm -rf *.o GPL/*.o *.ko GPL/*.ko *.mod.c GPL/*.mod.c .*.cmd GPL/.*.cmd .tmp_versions .tmp_versions  /lib/modules/3.2.0-23-generic/build/.tmp_versions/dgcusbdcp.mod Modules.symvers GPL/hda/Modules.symvers Module.symvers GPL/hda/Module.symvers modules.order GPL/hda/modules.order Module.markers GPL/hda/Module.markers
(cd /lib/modules/3.2.0-23-generic/build && make "CNXT_KERNELSRC=/lib/modules/3.2.0-23-generic/build" "M=/usr/lib/dgcmodem/modules" "CC=gcc" modules)
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-23-generic'
  CC [M]  /usr/lib/dgcmodem/modules/mod_dgcusbdcp.o
/usr/lib/dgcmodem/modules/mod_dgcusbdcp.c: In function 'dgcUsbWrite':
/usr/lib/dgcmodem/modules/mod_dgcusbdcp.c:173:2: warning: format '%d' expects argument of type 'int', but argument 5 has type 'size_t' [-Wformat]
/usr/lib/dgcmodem/modules/mod_dgcusbdcp.c: At top level:
/usr/lib/dgcmodem/modules/mod_dgcusbdcp.c:263:36: error: 'SPIN_LOCK_UNLOCKED' undeclared here (not in a function)
make[2]: *** [/usr/lib/dgcmodem/modules/mod_dgcusbdcp.o] Error 1
make[1]: *** [_module_/usr/lib/dgcmodem/modules] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-23-generic'
make: *** [all] Error 2

What can i do to enable this modem to work on my laptop?

---

### Post by foresthill on 2012-06-22
You need to contact Linuxant, since it's their software you're trying to use, and they're charging you for it. I never liked that company and had nothing but trouble with their drivers. 

If you want a tried and true method for getting dial-up to work, get hold of a serial modem and a USB to serial adapter. That's what I used to use on all flavors of Linux and this setup was plug and play, no third party drivers needed and only basic configuration required.

---

### Post by fox1t on 2012-06-22
I am already trying to use their software but it doesnt work anyway... Do you have some tips about what modem i could buy?

---

### Post by fox1t on 2012-06-23
I solved it, mods you can close this. Here is the fix, it is fast and safe!
[http://forums.linuxmint.com/viewtopic.php?f=49&t=105696](http://forums.linuxmint.com/viewtopic.php?f=49&t=105696)

---

