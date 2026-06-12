---
title: "AGN100 wireless card driver compiler error"
date: 2014-01-27
forum: Hardware
---

### Post by michael99 on 2014-01-27
Hello all!
I got an old computer inside the house and I decided to install Xubuntu 13.10 on it. Unfortunately, linux doesn't have the drivers of my wireless card (Airgo AGN100) so I'm trying to make the card work. I tried ndiswrapper but it makes my computer extremely unstable (it freezes during startup or a few minutes after login at best). I found the source of my card's driver [here]("http://sourceforge.net/projects/agnx80211driver/") and I'm trying to compile it but unfortunately, the compiling stops due to some errors. Note that I have the headers package installed, I don't have internet access but I can transfer files using USB drive. 

After I run make I get these errors:

> neofyta@neofytapc:~/Desktop/agnx$ sudo make make -C  /lib/modules/3.11.0-12-generic/build M=/home/neofyta/Desktop/agnx  modules make[1]: Entering directory  `/usr/src/linux-headers-3.11.0-12-generic'   CC [M]   /home/neofyta/Desktop/agnx/rf.o In file included from  /home/neofyta/Desktop/agnx/rf.c:17:0:  /home/neofyta/Desktop/agnx/debug.h: In function ‘dump_ieee80211_hdr’:  /home/neofyta/Desktop/agnx/debug.h:315:2: error: implicit declaration of  function ‘DECLARE_MAC_BUF’ [-Werror=implicit-function-declaration]    DECLARE_MAC_BUF(mac);   ^ /home/neofyta/Desktop/agnx/debug.h:315:18:  error: ‘mac’ undeclared (first use in this function)    DECLARE_MAC_BUF(mac);                   ^  /home/neofyta/Desktop/agnx/debug.h:315:18: note: each undeclared  identifier is reported only once for each function it appears in  /home/neofyta/Desktop/agnx/debug.h:372:9: error: implicit declaration of  function ‘ieee80211_get_hdrlen’ [-Werror=implicit-function-declaration]           hdrlen = ieee80211_get_hdrlen(fctl);          ^  /home/neofyta/Desktop/agnx/debug.h:378:3: error: implicit declaration of  function ‘print_mac’ [-Werror=implicit-function-declaration]     printk(" A1=%s", print_mac(mac, hdr->addr1));    ^ cc1: some warnings  being treated as errors make[2]: *** [/home/neofyta/Desktop/agnx/rf.o]  Error 1 make[1]: *** [_module_/home/neofyta/Desktop/agnx] Error 2  make[1]: Leaving directory `/usr/src/linux-headers-3.11.0-12-generic'  make: *** [modules] Error 2

I'd really appreciate some help!

Thank you

---

