---
title: "Can't compile driver"
date: 2009-03-13
forum: Hardware
---

### Post by lingenfr on 2009-03-13
I am trying to compile a driver for my SCM 241 smartcard reader. SCMMicro provides a 2.6 driver. When I try to compile it, I get the following:

lingenfr@ubuntu:~/Desktop/scr24x_v4.2.4_Release/scr24x_2.6.x_v4.2.4/src$ sudo make
make -C /lib/modules/`uname -r`/build SUBDIRS=`pwd` modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-11-generic'
  CC [M]  /home/lingenfr/Desktop/scr24x_v4.2.4_Release/scr24x_2.6.x_v4.2.4/src/scr241_main.o
In file included from /home/lingenfr/Desktop/scr24x_v4.2.4_Release/scr24x_2.6.x_v4.2.4/src/scr241_main.c:51:
/home/lingenfr/Desktop/scr24x_v4.2.4_Release/scr24x_2.6.x_v4.2.4/src/includes.h:89:27: error: asm/semaphore.h: No such file or directory
/home/lingenfr/Desktop/scr24x_v4.2.4_Release/scr24x_2.6.x_v4.2.4/src/includes.h:106:28: error: pcmcia/bulkmem.h: No such file or directory
/home/lingenfr/Desktop/scr24x_v4.2.4_Release/scr24x_2.6.x_v4.2.4/src/scr241_main.c: In function ‘Driver_Config’:
/home/lingenfr/Desktop/scr24x_v4.2.4_Release/scr24x_2.6.x_v4.2.4/src/scr241_main.c:527: warning: passing argument 3 of ‘pccard_validate_cis’ from incompatible pointer type
make[2]: *** [/home/lingenfr/Desktop/scr24x_v4.2.4_Release/scr24x_2.6.x_v4.2.4/src/scr241_main.o] Error 1
make[1]: *** [_module_/home/lingenfr/Desktop/scr24x_v4.2.4_Release/scr24x_2.6.x_v4.2.4/src] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-11-generic'
make: *** [default] Error 2

I assume that I need to install a dev package to get semaphore.h and bulkmem.h, but I have googled and can't figure out which one. I have installed build-essential and kernel headers. Does anyone know what I need to do? Thanks.

***The solution is in the link below.

---

### Post by Beefeater on 2009-03-18
Check this out, [http://ubuntuforums.org/showthread.php?t=1006111](http://ubuntuforums.org/showthread.php?t=1006111)

---

