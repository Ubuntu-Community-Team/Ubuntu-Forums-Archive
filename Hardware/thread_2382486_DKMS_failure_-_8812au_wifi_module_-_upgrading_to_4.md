---
title: "DKMS failure - 8812au wifi module - upgrading to 4.13.0-26.29~16.04.2"
date: 2018-01-14
forum: Hardware
---

### Post by nerderello2 on 2018-01-14
Hi,
was happily using the 8812au wifi module, using DKMS to compile new module for each new kernel that came along. 

Got the module from [HTML]https://github.com/Grawp/rtl8812au_rtl8821au.git[/HTML]

When I installed the new kernel, I get this error:
```
ERROR (dkms apport): binary package for 8812au: 4.3.20_16317.20160108 not found
Error! Bad return status for module build on kernel: 4.13.0-26-generic (x86_64)
Consult /var/lib/dkms/8812au/4.3.20_16317.20160108/build/make.log for more information.
```

And when I look in the "make.log" I get:
```
DKMS make.log for 8812au-4.3.20_16317.20160108 for kernel 4.13.0-26-generic (x86_64)
Fri 12 Jan 11:55:30 GMT 2018
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/4.13.0-26-generic/build M=/var/lib/dkms/8812au/4.3.20_16317.20160108/build  modules
make[1]: Entering directory '/usr/src/linux-headers-4.13.0-26-generic'
  CC [M]  /var/lib/dkms/8812au/4.3.20_16317.20160108/build/core/rtw_cmd.o
In file included from /var/lib/dkms/8812au/4.3.20_16317.20160108/build/include/drv_types.h:32:0,
                 from /var/lib/dkms/8812au/4.3.20_16317.20160108/build/core/rtw_cmd.c:22:
/var/lib/dkms/8812au/4.3.20_16317.20160108/build/include/osdep_service.h: In function ‘thread_enter’:
/var/lib/dkms/8812au/4.3.20_16317.20160108/build/include/osdep_service.h:343:2: error: implicit declaration of function ‘allow_signal’ [-Werror=implicit-function-declaration]
  allow_signal(SIGTERM);
  ^
/var/lib/dkms/8812au/4.3.20_16317.20160108/build/include/osdep_service.h: In function ‘flush_signals_thread’:
/var/lib/dkms/8812au/4.3.20_16317.20160108/build/include/osdep_service.h:353:6: error: implicit declaration of function ‘signal_pending’ [-Werror=implicit-function-declaration]
  if (signal_pending (current)) 
      ^
/var/lib/dkms/8812au/4.3.20_16317.20160108/build/include/osdep_service.h:355:3: error: implicit declaration of function ‘flush_signals’ [-Werror=implicit-function-declaration]
   flush_signals(current);
   ^
cc1: some warnings being treated as errors
scripts/Makefile.build:308: recipe for target '/var/lib/dkms/8812au/4.3.20_16317.20160108/build/core/rtw_cmd.o' failed
make[2]: *** [/var/lib/dkms/8812au/4.3.20_16317.20160108/build/core/rtw_cmd.o] Error 1
Makefile:1550: recipe for target '_module_/var/lib/dkms/8812au/4.3.20_16317.20160108/build' failed
make[1]: *** [_module_/var/lib/dkms/8812au/4.3.20_16317.20160108/build] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.13.0-26-generic'
Makefile:1670: recipe for target 'modules' failed
make: *** [modules] Error 2
```

I have confirmed that I've got the headers for the new kernel.

Anybody got any ideas of what I should do to make this work?

thanks
Nerderello

---

### Post by Yellow Pasque on 2018-01-14
Did you just transition from 4.10.x kernel to 4.13.x ?

Basically, you need a patch like this: [https://ubuntuforums.org/showthread.php?t=2378892&p=13716787#post13716787](https://ubuntuforums.org/showthread.php?t=2378892&p=13716787#post13716787)
^Maybe that repo would even work for you, despite the different name. I don't know. There seem to be a bunch of different versions of the 88xxxu driver floating around on github.

EDIT: This one's already patched and it's kept updated: [https://github.com/gnab/rtl8812au](https://github.com/gnab/rtl8812au)

---

### Post by nerderello2 on 2018-01-14
Temüjin,
thanks for that. Even though it's an older version, the patched version on the gnab git worked a treat,

Thanks again for your help
Nerderello

---

