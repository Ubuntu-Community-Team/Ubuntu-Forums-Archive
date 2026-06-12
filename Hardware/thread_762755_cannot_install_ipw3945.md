---
title: "cannot install ipw3945"
date: 2008-04-22
forum: Hardware
---

### Post by samuraiche on 2008-04-22
Hi, 

Just compiled a new 2.6.25 kernel to get working suspend/hibernate. And it works good,but have another problem: I cannot install IntelWireless 3945 network card. 

First, as i understood i had to install the ieee80211 subsystem,but when trying to compile i get this message: 

```
samurai@okinava:~/Desktop/wireless/ieee80211-1.2.18$ make
Makefile:17: 
Makefile:18: WARNING: $SHELL not set to bash.
Makefile:19: If you experience build errors, try
Makefile:20: 'make SHELL=/bin/bash'.
Makefile:21: 
Checking in /lib/modules/2.6.25-shama for ieee80211 components...
find: Symbolic link `/lib/modules/2.6.25-shama/source/debian/linux-image-2.6.25-shama/lib/modules/2.6.25-shama/source' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/lib/modules/2.6.25-shama/source/debian/linux-image-2.6.25-shama/lib/modules/2.6.25-shama/build' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/lib/modules/2.6.25-shama/build/debian/linux-image-2.6.25-shama/lib/modules/2.6.25-shama/source' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/lib/modules/2.6.25-shama/build/debian/linux-image-2.6.25-shama/lib/modules/2.6.25-shama/build' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/lib/modules/2.6.25-shama/build/debian/linux-image-2.6.25-shama/lib/modules/2.6.25-shama/source' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/lib/modules/2.6.25-shama/build/debian/linux-image-2.6.25-shama/lib/modules/2.6.25-shama/build' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
/lib/modules/2.6.25-shama/source/include/net/ieee80211_crypt.h
/lib/modules/2.6.25-shama/source/include/net/ieee80211_radiotap.h
/lib/modules/2.6.25-shama/source/include/net/ieee80211.h
/lib/modules/2.6.25-shama/source/.tmp_versions/ieee80211_crypt.mod
/lib/modules/2.6.25-shama/source/.tmp_versions/ieee80211_crypt_wep.mod
/lib/modules/2.6.25-shama/source/.tmp_versions/ieee80211_crypt_tkip.mod
/lib/modules/2.6.25-shama/source/.tmp_versions/ieee80211.mod
/lib/modules/2.6.25-shama/source/.tmp_versions/ieee80211_crypt_ccmp.mod
/lib/modules/2.6.25-shama/source/debian/linux-headers-2.6.25-shama/usr/src/linux-headers-2.6.25-shama/include/net/ieee80211_crypt.h
/lib/modules/2.6.25-shama/source/debian/linux-headers-2.6.25-shama/usr/src/linux-headers-2.6.25-shama/include/net/ieee80211_radiotap.h
/lib/modules/2.6.25-shama/source/debian/linux-headers-2.6.25-shama/usr/src/linux-headers-2.6.25-shama/include/net/ieee80211.h
/lib/modules/2.6.25-shama/source/debian/linux-image-2.6.25-shama/lib/modules/2.6.25-shama/kernel/net/ieee80211/ieee80211_crypt_ccmp.ko
/lib/modules/2.6.25-shama/source/debian/linux-image-2.6.25-shama/lib/modules/2.6.25-shama/kernel/net/ieee80211/ieee80211_crypt_wep.ko
/lib/modules/2.6.25-shama/source/debian/linux-image-2.6.25-shama/lib/modules/2.6.25-shama/kernel/net/ieee80211/ieee80211_crypt.ko
/lib/modules/2.6.25-shama/source/debian/linux-image-2.6.25-shama/lib/modules/2.6.25-shama/kernel/net/ieee80211/ieee80211_crypt_tkip.ko
/lib/modules/2.6.25-shama/source/debian/linux-image-2.6.25-shama/lib/modules/2.6.25-shama/kernel/net/ieee80211/ieee80211.ko
/lib/modules/2.6.25-shama/source/net/ieee80211/ieee80211_geo.c
/lib/modules/2.6.25-shama/source/net/ieee80211/ieee80211_crypt_wep.mod.o
/lib/modules/2.6.25-shama/source/net/ieee80211/ieee80211_crypt_wep.c
/lib/modules/2.6.25-shama/source/net/ieee80211/ieee80211_tx.c
/lib/modules/2.6.25-shama/source/net/ieee80211/ieee80211_crypt_ccmp.mod.o
/lib/modules/2.6.25-shama/source/net/ieee80211/ieee80211_crypt_tkip.mod.c
/lib/modules/2.6.25-shama/source/net/ieee80211/ieee80211_crypt_ccmp.ko
/lib/modules/2.6.25-shama/source/net/ieee80211/ieee80211_crypt_tkip.c
/lib/modules/2.6.25-shama/source/net/ieee80211/ieee80211_crypt.c
/lib/modules/2.6.25-shama/source/net/ieee80211/ieee80211_crypt_wep.mod.c
/lib/modules/2.6.25-shama/source/net/ieee80211/ieee80211_module.c
/lib/modules/2.6.25-shama/source/net/ieee80211/ieee80211_tx.o
/lib/modules/2.6.25-shama/source/net/ieee80211/ieee80211_rx.o
/lib/modules/2.6.25-shama/source/net/ieee80211/ieee80211.o
/lib/modules/2.6.25-shama/source/net/ieee80211/ieee80211_module.o
/lib/modules/2.6.25-shama/source/net/ieee80211/ieee80211_crypt_wep.ko
/lib/modules/2.6.25-shama/source/net/ieee80211/ieee80211_crypt_ccmp.mod.c
/lib/modules/2.6.25-shama/source/net/ieee80211/ieee80211_wx.c
/lib/modules/2.6.25-shama/source/net/ieee80211/ieee80211_crypt_tkip.o
/lib/modules/2.6.25-shama/source/net/ieee80211/ieee80211_crypt_wep.o
/lib/modules/2.6.25-shama/source/net/ieee80211/ieee80211_crypt_ccmp.c
/lib/modules/2.6.25-shama/source/net/ieee80211/ieee80211_crypt.mod.o
/lib/modules/2.6.25-shama/source/net/ieee80211/ieee80211_crypt_ccmp.o
/lib/modules/2.6.25-shama/source/net/ieee80211/ieee80211_crypt_tkip.mod.o
/lib/modules/2.6.25-shama/source/net/ieee80211/ieee80211.mod.o
/lib/modules/2.6.25-shama/source/net/ieee80211/ieee80211_crypt.mod.c
/lib/modules/2.6.25-shama/source/net/ieee80211/ieee80211_crypt.o
/lib/modules/2.6.25-shama/source/net/ieee80211/ieee80211_rx.c
/lib/modules/2.6.25-shama/source/net/ieee80211/ieee80211_crypt.ko
/lib/modules/2.6.25-shama/source/net/ieee80211/ieee80211.mod.c
/lib/modules/2.6.25-shama/source/net/ieee80211/ieee80211_geo.o
/lib/modules/2.6.25-shama/source/net/ieee80211/ieee80211_wx.o
/lib/modules/2.6.25-shama/source/net/ieee80211/ieee80211_crypt_tkip.ko
/lib/modules/2.6.25-shama/source/net/ieee80211/ieee80211.ko
/lib/modules/2.6.25-shama/kernel/net/ieee80211/ieee80211_crypt_ccmp.ko
/lib/modules/2.6.25-shama/kernel/net/ieee80211/ieee80211_crypt_wep.ko
/lib/modules/2.6.25-shama/kernel/net/ieee80211/ieee80211_crypt.ko
/lib/modules/2.6.25-shama/kernel/net/ieee80211/ieee80211_crypt_tkip.ko
/lib/modules/2.6.25-shama/kernel/net/ieee80211/ieee80211.ko
/lib/modules/2.6.25-shama/build/include/net/ieee80211_crypt.h
/lib/modules/2.6.25-shama/build/include/net/ieee80211_radiotap.h
/lib/modules/2.6.25-shama/build/include/net/ieee80211.h
/lib/modules/2.6.25-shama/build/.tmp_versions/ieee80211_crypt.mod
/lib/modules/2.6.25-shama/build/.tmp_versions/ieee80211_crypt_wep.mod
/lib/modules/2.6.25-shama/build/.tmp_versions/ieee80211_crypt_tkip.mod
/lib/modules/2.6.25-shama/build/.tmp_versions/ieee80211.mod
/lib/modules/2.6.25-shama/build/.tmp_versions/ieee80211_crypt_ccmp.mod
/lib/modules/2.6.25-shama/build/debian/linux-headers-2.6.25-shama/usr/src/linux-headers-2.6.25-shama/include/net/ieee80211_crypt.h
/lib/modules/2.6.25-shama/build/debian/linux-headers-2.6.25-shama/usr/src/linux-headers-2.6.25-shama/include/net/ieee80211_radiotap.h
/lib/modules/2.6.25-shama/build/debian/linux-headers-2.6.25-shama/usr/src/linux-headers-2.6.25-shama/include/net/ieee80211.h
/lib/modules/2.6.25-shama/build/debian/linux-image-2.6.25-shama/lib/modules/2.6.25-shama/kernel/net/ieee80211/ieee80211_crypt_ccmp.ko
/lib/modules/2.6.25-shama/build/debian/linux-image-2.6.25-shama/lib/modules/2.6.25-shama/kernel/net/ieee80211/ieee80211_crypt_wep.ko
/lib/modules/2.6.25-shama/build/debian/linux-image-2.6.25-shama/lib/modules/2.6.25-shama/kernel/net/ieee80211/ieee80211_crypt.ko
/lib/modules/2.6.25-shama/build/debian/linux-image-2.6.25-shama/lib/modules/2.6.25-shama/kernel/net/ieee80211/ieee80211_crypt_tkip.ko
/lib/modules/2.6.25-shama/build/debian/linux-image-2.6.25-shama/lib/modules/2.6.25-shama/kernel/net/ieee80211/ieee80211.ko
/lib/modules/2.6.25-shama/build/net/ieee80211/ieee80211_geo.c
/lib/modules/2.6.25-shama/build/net/ieee80211/ieee80211_crypt_wep.mod.o
/lib/modules/2.6.25-shama/build/net/ieee80211/ieee80211_crypt_wep.c
/lib/modules/2.6.25-shama/build/net/ieee80211/ieee80211_tx.c
/lib/modules/2.6.25-shama/build/net/ieee80211/ieee80211_crypt_ccmp.mod.o
/lib/modules/2.6.25-shama/build/net/ieee80211/ieee80211_crypt_tkip.mod.c
/lib/modules/2.6.25-shama/build/net/ieee80211/ieee80211_crypt_ccmp.ko
/lib/modules/2.6.25-shama/build/net/ieee80211/ieee80211_crypt_tkip.c
/lib/modules/2.6.25-shama/build/net/ieee80211/ieee80211_crypt.c
/lib/modules/2.6.25-shama/build/net/ieee80211/ieee80211_crypt_wep.mod.c
/lib/modules/2.6.25-shama/build/net/ieee80211/ieee80211_module.c
/lib/modules/2.6.25-shama/build/net/ieee80211/ieee80211_tx.o
/lib/modules/2.6.25-shama/build/net/ieee80211/ieee80211_rx.o
/lib/modules/2.6.25-shama/build/net/ieee80211/ieee80211.o
/lib/modules/2.6.25-shama/build/net/ieee80211/ieee80211_module.o
/lib/modules/2.6.25-shama/build/net/ieee80211/ieee80211_crypt_wep.ko
/lib/modules/2.6.25-shama/build/net/ieee80211/ieee80211_crypt_ccmp.mod.c
/lib/modules/2.6.25-shama/build/net/ieee80211/ieee80211_wx.c
/lib/modules/2.6.25-shama/build/net/ieee80211/ieee80211_crypt_tkip.o
/lib/modules/2.6.25-shama/build/net/ieee80211/ieee80211_crypt_wep.o
/lib/modules/2.6.25-shama/build/net/ieee80211/ieee80211_crypt_ccmp.c
/lib/modules/2.6.25-shama/build/net/ieee80211/ieee80211_crypt.mod.o
/lib/modules/2.6.25-shama/build/net/ieee80211/ieee80211_crypt_ccmp.o
/lib/modules/2.6.25-shama/build/net/ieee80211/ieee80211_crypt_tkip.mod.o
/lib/modules/2.6.25-shama/build/net/ieee80211/ieee80211.mod.o
/lib/modules/2.6.25-shama/build/net/ieee80211/ieee80211_crypt.mod.c
/lib/modules/2.6.25-shama/build/net/ieee80211/ieee80211_crypt.o
/lib/modules/2.6.25-shama/build/net/ieee80211/ieee80211_rx.c
/lib/modules/2.6.25-shama/build/net/ieee80211/ieee80211_crypt.ko
/lib/modules/2.6.25-shama/build/net/ieee80211/ieee80211.mod.c
/lib/modules/2.6.25-shama/build/net/ieee80211/ieee80211_geo.o
/lib/modules/2.6.25-shama/build/net/ieee80211/ieee80211_wx.o
/lib/modules/2.6.25-shama/build/net/ieee80211/ieee80211_crypt_tkip.ko
/lib/modules/2.6.25-shama/build/net/ieee80211/ieee80211.ko
/lib/modules/2.6.25-shama/build/include/net/ieee80211_crypt.h
/lib/modules/2.6.25-shama/build/include/net/ieee80211_radiotap.h
/lib/modules/2.6.25-shama/build/include/net/ieee80211.h
/lib/modules/2.6.25-shama/build/.tmp_versions/ieee80211_crypt.mod
/lib/modules/2.6.25-shama/build/.tmp_versions/ieee80211_crypt_wep.mod
/lib/modules/2.6.25-shama/build/.tmp_versions/ieee80211_crypt_tkip.mod
/lib/modules/2.6.25-shama/build/.tmp_versions/ieee80211.mod
/lib/modules/2.6.25-shama/build/.tmp_versions/ieee80211_crypt_ccmp.mod
/lib/modules/2.6.25-shama/build/debian/linux-headers-2.6.25-shama/usr/src/linux-headers-2.6.25-shama/include/net/ieee80211_crypt.h
/lib/modules/2.6.25-shama/build/debian/linux-headers-2.6.25-shama/usr/src/linux-headers-2.6.25-shama/include/net/ieee80211_radiotap.h
/lib/modules/2.6.25-shama/build/debian/linux-headers-2.6.25-shama/usr/src/linux-headers-2.6.25-shama/include/net/ieee80211.h
/lib/modules/2.6.25-shama/build/debian/linux-image-2.6.25-shama/lib/modules/2.6.25-shama/kernel/net/ieee80211/ieee80211_crypt_ccmp.ko
/lib/modules/2.6.25-shama/build/debian/linux-image-2.6.25-shama/lib/modules/2.6.25-shama/kernel/net/ieee80211/ieee80211_crypt_wep.ko
/lib/modules/2.6.25-shama/build/debian/linux-image-2.6.25-shama/lib/modules/2.6.25-shama/kernel/net/ieee80211/ieee80211_crypt.ko
/lib/modules/2.6.25-shama/build/debian/linux-image-2.6.25-shama/lib/modules/2.6.25-shama/kernel/net/ieee80211/ieee80211_crypt_tkip.ko
/lib/modules/2.6.25-shama/build/debian/linux-image-2.6.25-shama/lib/modules/2.6.25-shama/kernel/net/ieee80211/ieee80211.ko
/lib/modules/2.6.25-shama/build/net/ieee80211/ieee80211_geo.c
/lib/modules/2.6.25-shama/build/net/ieee80211/ieee80211_crypt_wep.mod.o
/lib/modules/2.6.25-shama/build/net/ieee80211/ieee80211_crypt_wep.c
/lib/modules/2.6.25-shama/build/net/ieee80211/ieee80211_tx.c
/lib/modules/2.6.25-shama/build/net/ieee80211/ieee80211_crypt_ccmp.mod.o
/lib/modules/2.6.25-shama/build/net/ieee80211/ieee80211_crypt_tkip.mod.c
/lib/modules/2.6.25-shama/build/net/ieee80211/ieee80211_crypt_ccmp.ko
/lib/modules/2.6.25-shama/build/net/ieee80211/ieee80211_crypt_tkip.c
/lib/modules/2.6.25-shama/build/net/ieee80211/ieee80211_crypt.c
/lib/modules/2.6.25-shama/build/net/ieee80211/ieee80211_crypt_wep.mod.c
/lib/modules/2.6.25-shama/build/net/ieee80211/ieee80211_module.c
/lib/modules/2.6.25-shama/build/net/ieee80211/ieee80211_tx.o

/lib/modules/2.6.25-shama/build/net/ieee80211/ieee80211_rx.o
/lib/modules/2.6.25-shama/build/net/ieee80211/ieee80211.o
/lib/modules/2.6.25-shama/build/net/ieee80211/ieee80211_module.o
/lib/modules/2.6.25-shama/build/net/ieee80211/ieee80211_crypt_wep.ko
/lib/modules/2.6.25-shama/build/net/ieee80211/ieee80211_crypt_ccmp.mod.c
/lib/modules/2.6.25-shama/build/net/ieee80211/ieee80211_wx.c
/lib/modules/2.6.25-shama/build/net/ieee80211/ieee80211_crypt_tkip.o
/lib/modules/2.6.25-shama/build/net/ieee80211/ieee80211_crypt_wep.o
/lib/modules/2.6.25-shama/build/net/ieee80211/ieee80211_crypt_ccmp.c
/lib/modules/2.6.25-shama/build/net/ieee80211/ieee80211_crypt.mod.o
/lib/modules/2.6.25-shama/build/net/ieee80211/ieee80211_crypt_ccmp.o
/lib/modules/2.6.25-shama/build/net/ieee80211/ieee80211_crypt_tkip.mod.o
/lib/modules/2.6.25-shama/build/net/ieee80211/ieee80211.mod.o
/lib/modules/2.6.25-shama/build/net/ieee80211/ieee80211_crypt.mod.c
/lib/modules/2.6.25-shama/build/net/ieee80211/ieee80211_crypt.o
/lib/modules/2.6.25-shama/build/net/ieee80211/ieee80211_rx.c
/lib/modules/2.6.25-shama/build/net/ieee80211/ieee80211_crypt.ko
/lib/modules/2.6.25-shama/build/net/ieee80211/ieee80211.mod.c
/lib/modules/2.6.25-shama/build/net/ieee80211/ieee80211_geo.o
/lib/modules/2.6.25-shama/build/net/ieee80211/ieee80211_wx.o
/lib/modules/2.6.25-shama/build/net/ieee80211/ieee80211_crypt_tkip.ko
/lib/modules/2.6.25-shama/build/net/ieee80211/ieee80211.ko
Above files found.  Remove? [y],n 
```

I've tried y and n options after pressing yes it deletes some files,but after i get another error...

And if i try to compile ipw3945 drivers without installing ieee80211 then i get this  one: 

```
samurai@okinava:~/Desktop/wireless/ipw3945-1.2.2$ make
Makefile:53: 
Makefile:54: WARNING: $SHELL not set to bash.
Makefile:55: If you experience build errors, try
Makefile:56: 'make SHELL=/bin/bash'.
Makefile:57: 
/bin/sh: Syntax error: "(" unexpected
/bin/sh: Syntax error: "(" unexpected
-e 
 WARNING: Your kernel contains ieee80211 symbol definitions and you
are not using the kernel's default ieee80211 subsystem.  (Perhaps you
used the out-of-tree ieee80211 subsystem's 'make install' or have
provided a path to the ieee80211 subsystem via IEEE80211_INC.)

If you wish to use the out-of-tree ieee80211 subsystem then it is
recommended to use that projects' "make patch_kernel" facility
and rebuild your kernel to update the Module symbol version information.

Failure to do this may result in build warnings and unexpected
behavior when running modules which rely on the ieee80211 subsystem.

 
-e  Aborting the build.  You can force the build to continue by adding:

	IEEE80211_IGNORE_DUPLICATE=y

to your make command line.


make: *** [check_inc] Error 1
samurai@okinava:~/Desktop/wireless/ipw3945-1.2.2$ 
```

I have also tried this commando : 
```
sudo make IEEE80211_INC=/lib/modules/2.6.25-shama/build/net/ieee80211/
```

but get the same error


So thought maybe there someone who knows how to solve this problem? 

thanks in advance

---

### Post by ctrlER on 2008-04-22
Have you tried the drivers from 
[http://linuxwireless.sipsolutions.net/](http://linuxwireless.sipsolutions.net/)

?

---

### Post by samuraiche on 2008-04-22
> **ctrlER said:**
> Have you tried the drivers from 
[http://linuxwireless.sipsolutions.net/](http://linuxwireless.sipsolutions.net/)

?

no i didn't yet but now i'll :) thanx 
i'm recompiling my kernel once again coz i tried debian iwlwifi package and after installation ubuntu didn't want to boot it just hangs..so i'll now be recompiling and after that i'll try to use iwlwife 

thnx :)

---

### Post by samuraiche on 2008-04-23
> **samuraiche said:**
> no i didn't yet but now i'll :) thanx 
i'm recompiling my kernel once again coz i tried debian iwlwifi package and after installation ubuntu didn't want to boot it just hangs..so i'll now be recompiling and after that i'll try to use iwlwife 

thnx :)

so, as you advised i tried to install iwlwife..and it seems that i do actually install the drivers but cannot load them via modprobe iwl3945 it says:FATAL module iwl3945 not found.

What i found strange is that when drivers were copied a never say iwl3945 in the list. There were ipw2200 boardcom,rt etc drivers but not iwp3945.

And I also have ieee80211 compiled in the kernel. Maybe it's the reason why i cannot properly install the drivers? 

I also tried installing mac80211 from the same site,but when make modules_etc I got an error dunno which one exactly

So maybe i shouldn't have installend the iee80211 module in the kernel? Maybe i have to try to compile without this module and then try to install mac80211 and iwlwifi ?Or maybe someone know how to install iwlwifi step by step?

---

