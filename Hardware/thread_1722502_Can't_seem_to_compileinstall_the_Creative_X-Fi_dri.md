---
title: "Can't seem to compile/install the Creative X-Fi drivers"
date: 2011-04-05
forum: Hardware
---

### Post by PC_Dude74 on 2011-04-05
I'm using Kubuntu 10.10 (64-Bit) and my kernel version is 2.6.35-28. I am having trouble compiling and installing the X-Fi drivers from Creative's site. Whenever I run the "make" command, it spits out this error:

make -C /lib/modules/2.6.35-28-generic/build M=/home/timbo/Desktop/XFiDrv_Linux_Public_US_1.00
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-28-generic'
  CC [M]  /home/timbo/Desktop/XFiDrv_Linux_Public_US_1.00/xfi.o
/home/timbo/Desktop/XFiDrv_Linux_Public_US_1.00/xfi.c:14: fatal error: sound/driver.h: No such file or directory
compilation terminated.
make[2]: *** [/home/timbo/Desktop/XFiDrv_Linux_Public_US_1.00/xfi.o] Error 1
make[1]: *** [_module_/home/timbo/Desktop/XFiDrv_Linux_Public_US_1.00] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-28-generic'
make: *** [all] Error 2

Everything that I try to compile ends with a error 1 and error 2 and I also have the build-essentials package installed too. I'm still learning the ropes to this OS but I love it, could it be my kernel version or am I doing something wrong? I would appreciate any information on this issue. Thanks.

---

