---
title: "Creative Xfi driver won't compile"
date: 2011-08-04
forum: Hardware
---

### Post by EngDrewman on 2011-08-04
I recently installed a Creative Xfi extreme gamer card in my desktop, downloaded the linux driver from Creative, but it won't compile.

```
drew@BFG-Ubuntu:/usr/src/XFiDrv_Linux_Public_US_1.00$ sudo make
[sudo] password for drew: 
make -C /lib/modules/2.6.38-10-generic/build M=/usr/src/XFiDrv_Linux_Public_US_1.00
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-10-generic'
  CC [M]  /usr/src/XFiDrv_Linux_Public_US_1.00/xfi.o
/usr/src/XFiDrv_Linux_Public_US_1.00/xfi.c:14:26: fatal error: sound/driver.h: No such file or directory
compilation terminated.
make[2]: *** [/usr/src/XFiDrv_Linux_Public_US_1.00/xfi.o] Error 1
make[1]: *** [_module_/usr/src/XFiDrv_Linux_Public_US_1.00] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-10-generic'
make: *** [all] Error 2
drew@BFG-Ubuntu:/usr/src/XFiDrv_Linux_Public_US_1.00$ 

```

I'm running Ubuntu 11.04 x64. The driver says it is compatible with 64 bit on their web site. Below is the readme file:

```
====================================================================

  Sound Blaster X-Fi Linux 32/64-bit Driver Source Release Readme File
  September 2008

====================================================================

The purpose of this document is to describe how to build and install the 
X-Fi Linux device driver.



Quick install

=============
In terminal,

1) Goto source directory
2) Execute make command as root
   make
   make install

Uninstall
=========
In terminal,
1) Goto source directory
2) Execute make command as root
   make uninstall


Copyright (c) 2008 Creative Technology Ltd. All rights reserved.
====================================================================
  End of Readme File
====================================================================
```

---

### Post by 1clue on 2011-08-04
Is there a reason why you're compiling it?

From **lspci -k**:
08:00.0 Multimedia audio controller: Creative Labs SB X-Fi
	Subsystem: Creative Labs Device 002f
	Kernel driver in use: SB-XFi
	Kernel modules: snd-ctxfi

---

### Post by EngDrewman on 2011-08-04
you're right- my bad it is already working. Had to change some settings in the sound control panel.](*,)

---

### Post by 1clue on 2011-08-04
I know what you're talking about though, I got my card before there was driver support and went through hell to try to get it working.

It still only works like any other sound card, the external control panel just as well be in the garbage.  But at least it's a sound card.

---

