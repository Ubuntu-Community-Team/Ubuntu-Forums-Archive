---
title: "AverTVHD Volar Max not being detected by Myth"
date: 2009-11-08
forum: Hardware
---

### Post by hubmaster on 2009-11-08
I tried to build the driver for AverTVHD Volar Max on Mythbuntu 9.10 x64 with Kernel 2.6.31-14 with no success. I ran the expert setting which dumps the drivers into a specific folder so that one can sudo make && install

Drivers available at:
[http://driverscollection.com/?H=AVerTV%20Hybrid%20Volar%20MAX%20%28H826%29&By=AVerMedia](http://driverscollection.com/?H=AVerTV%20Hybrid%20Volar%20MAX%20%28H826%29&By=AVerMedia)

When I sudo make:
make -C /lib/modules/2.6.31-14-generic/source O=/lib/modules/2.6.31-14-generic/build SUBDIRS=`pwd` 
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
  LD      /home/john/Desktop/ExtractedDriver/H826D-expert-install/built-in.o
  CC [M]  /home/john/Desktop/ExtractedDriver/H826D-expert-install/aver/averusb-mod.o
  CC [M]  /home/john/Desktop/ExtractedDriver/H826D-expert-install/driver-core.o
  CC [M]  /home/john/Desktop/ExtractedDriver/H826D-expert-install/aver/osdep.o
  SHIPPED /home/john/Desktop/ExtractedDriver/H826D-expert-install/aver/osdep_dvb.o
  CC [M]  /home/john/Desktop/ExtractedDriver/H826D-expert-install/aver/osdep_th2.o
  CC [M]  /home/john/Desktop/ExtractedDriver/H826D-expert-install/aver/osdep_v4l2.o
  CC [M]  /home/john/Desktop/ExtractedDriver/H826D-expert-install/aver/osdep_vbuf.o
  CC [M]  /home/john/Desktop/ExtractedDriver/H826D-expert-install/aver/osdep_alsa.o
/home/john/Desktop/ExtractedDriver/H826D-expert-install/aver/osdep_alsa.c: In function ‘SysAlsaInitCard’:
/home/john/Desktop/ExtractedDriver/H826D-expert-install/aver/osdep_alsa.c:206: error: implicit declaration of function ‘snd_card_new’
/home/john/Desktop/ExtractedDriver/H826D-expert-install/aver/osdep_alsa.c:206: warning: assignment makes pointer from integer without a cast
make[3]: *** [/home/hubert/Desktop/ExtractedDriver/H826D-expert-install/aver/osdep_alsa.o] Error 1
make[2]: *** [_module_/home/hubert/Desktop/ExtractedDriver/H826D-expert-install] Error 2

Output from lsusb:
Bus 001 Device 003: ID 07ca:1826 AVerMedia Technologies, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04d9:0499 Holtek Semiconductor, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Any help on this?

---

