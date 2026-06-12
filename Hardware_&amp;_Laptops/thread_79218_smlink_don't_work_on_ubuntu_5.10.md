---
title: "smlink don't work on ubuntu 5.10"
date: 2005-10-19
forum: Hardware &amp; Laptops
---

### Post by moriero on 2005-10-19
Hi, i have a problem with my modem: SmartLink.
i read many guide to configure this but i can't do it.
I have installed this file:sl-modem-daemon_2.9.10+2.9.9d-6ubuntu1_i386.deb sl-modem-source_2.9.10+2.9.9d-6ubuntu1_i386.deb con kpackage,and try to modife the Makefile as was written in the file README:
i try to written 
KERNEL_DIR=/usr/src/linux-source-2.6.12
or
KERNEL_DIR:=/usr/src/linux-headers-2.6.12-9
but when i give command make in the terminal (under directory slmodem-2.9.10)
i have this reply:
```
make -C modem all
make[1]: Entering directory `/home/moriero/slmodem-2.9.10/modem'
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o modem.o -c modem.c
modem.c: In function ‘modem_reset’:
modem.c:1701: error: invalid storage class for function ‘sregs_init’
modem.c:1713: warning: implicit declaration of function ‘sregs_init’
modem.c: At top level:
modem.c:1727: error: static declaration of ‘sregs_init’ follows non-static declaration
modem.c:1713: error: previous implicit declaration of ‘sregs_init’ was here
make[1]: *** [modem.o] Error 1
make[1]: Leaving directory `/home/moriero/slmodem-2.9.10/modem'
make: *** [modem] Error 2
```
Sorry for my bad english ,i hope in a reply. Thanks

---

### Post by dsd on 2005-11-30
I'm getting the same problem following the instructions from the Smartlink driver (downloaded from their website). I can't install the sl-modem packages, as they are not available for the AMD64.

---

### Post by howlerbr on 2005-12-05
I have the same problem here!!! Someone could help? I can't make the driver compile!!!!!! PLease help!!!!!

---

### Post by dsd on 2005-12-06
I'm busy working on this, and have just gotten into contact with the guys at [http://linmodems.technion.ac.il/](http://linmodems.technion.ac.il/). I'm not sure if anything will come out of it, but I will keep you posted (this shouldn't be an issue on i386, as you can just install the sl-modem packages through apt-get/synaptic)

---

