---
title: "Problem with Creative Fatality Champion"
date: 2013-11-16
forum: Hardware
---

### Post by JeanDaniel.Tissot on 2013-11-16
Hi all,
I download XFiDrv_Linux_Public_US_1.00.tar.gz.
I suppress #include <sound/driver.h> in xfi.c and ctatc.h
I also include this line in xfi.c :
#include <linux/module.h>

When i do make, i have these errors :

make -C /lib/modules/3.8.0-33-generic/build M=/home/jdt/Desktop/XFiDrv_Linux_Public_US_1.00
make[1]: Entering directory `/usr/src/linux-headers-3.8.0-33-generic'
  CC [M]  /home/jdt/Desktop/XFiDrv_Linux_Public_US_1.00/xfi.o
In file included from /home/jdt/Desktop/XFiDrv_Linux_Public_US_1.00/xfi.c:17:0:
/home/jdt/Desktop/XFiDrv_Linux_Public_US_1.00/ctatc.h:135:15: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'ct_atc_create'
/home/jdt/Desktop/XFiDrv_Linux_Public_US_1.00/xfi.c:39:1: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'ct_card_probe'
/home/jdt/Desktop/XFiDrv_Linux_Public_US_1.00/xfi.c:91:23: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'ct_card_remove'
/home/jdt/Desktop/XFiDrv_Linux_Public_US_1.00/xfi.c:101:11: error: 'ct_card_probe' undeclared here (not in a function)
/home/jdt/Desktop/XFiDrv_Linux_Public_US_1.00/xfi.c:102:2: error: implicit declaration of function '__devexit_p' [-Werror=implicit-function-declaration]
/home/jdt/Desktop/XFiDrv_Linux_Public_US_1.00/xfi.c:102:24: error: 'ct_card_remove' undeclared here (not in a function)
/home/jdt/Desktop/XFiDrv_Linux_Public_US_1.00/xfi.c:26:12: warning: 'index' defined but not used [-Wunused-variable]
/home/jdt/Desktop/XFiDrv_Linux_Public_US_1.00/xfi.c:27:14: warning: 'id' defined but not used [-Wunused-variable]
/home/jdt/Desktop/XFiDrv_Linux_Public_US_1.00/xfi.c:28:12: warning: 'enable' defined but not used [-Wunused-variable]
cc1: some warnings being treated as errors
make[2]: *** [/home/jdt/Desktop/XFiDrv_Linux_Public_US_1.00/xfi.o] Error 1
make[1]: *** [_module_/home/jdt/Desktop/XFiDrv_Linux_Public_US_1.00] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.8.0-33-generic'
make: *** [all] Error 2

I'm running Ubuntu precise with precise-backports
My running kernel is 3.8.0-33-generic 64 bits.

Can anyone help me to compile this driver or at less help me to blacklist the default module from my kernel, I have Intel integrated sound card which work perfectly.
It seem that sound are numeric send to analogical part of the Creative card sound.

Thanks in advance

Regards, Jean-Daniel.

---

