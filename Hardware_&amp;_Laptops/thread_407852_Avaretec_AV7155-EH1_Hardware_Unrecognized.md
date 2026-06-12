---
title: "Avaretec AV7155-EH1 Hardware Unrecognized"
date: 2007-04-12
forum: Hardware &amp; Laptops
---

### Post by WNxCryptic on 2007-04-12
I've tried a variety of Ubuntu versions including 6.06, 6.10, and 7.04 but none have provided to be any better than the others as far as functionality goes with the hardware in my laptop.

I've researched and found that it seems no one can find a driver for the LAN on it, and it appears as if I'm Linux-retarted as I'm unable to even get the wireless to connect (the list of networks appears, but when I connect to one it just "circles" for 40 seconds and then goes back to "No Network connection").

I was told that ndiswrapper should work for the wireless, but when I go to make it and whatnot, I get a variety of terminal errors and whatnot which I'm not qualified to diagnose or understand.

Any help?

---

### Post by WNxCryptic on 2007-04-12
Went to install a Ralink (RT...) driver that supposedly works with my hardware, but when I go to "Make" it as the installation suggests:

I get the following build error:

> make -C /lib/modules/2.6.20-12-generic/build SUBDIRS=/home/culture/RT61_Linux_STA_Drv1.1.0.0/Module modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-12-generic'
   CC [M]  /home/culture/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.o
/home/culture/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.c: In function 'RT61_probe':
/home/culture/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.c:197: error 'struct net_device' has no member named 'get_wirelesss_stats'
/home/culture/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.c:326: warning: passing argument 2 of 'request_irq' from incompatible pointer type
make[2]: *** [/home/culture/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.o] Error 1
make[1]: *** [_module_/home/culture/RT61_Linux_STA_Drv1.1.0.0/Module] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-2.6.20-12-generic'
make: *** [all] Error 2

---

