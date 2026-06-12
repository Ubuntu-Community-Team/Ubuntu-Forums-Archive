---
title: "How to compile a kernel with webcam modules ?"
date: 2008-12-23
forum: Installation &amp; Upgrades
---

### Post by frenchn00b on 2008-12-23
Hello, 

I would like to compile the modules [http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html) with my kernel. 

How should I do so ?

thanks


I have those errors:
[http://forum.ubuntuusers.de/topic/howto:-skype-und-logitech-e2500-webcam-via-gs/2/](http://forum.ubuntuusers.de/topic/howto:-skype-und-logitech-e2500-webcam-via-gs/2/)
> 
/tmp/gspcav1-20071224/gspca_core.c:2463: error: implicit declaration of function &#8216;video_usercopy&#8217;
/tmp/gspcav1-20071224/gspca_core.c: At top level:
/tmp/gspcav1-20071224/gspca_core.c:2609: error: unknown field &#8216;owner&#8217; specified in initializer
/tmp/gspcav1-20071224/gspca_core.c:2609: warning: initialization from incompatible pointer type
/tmp/gspcav1-20071224/gspca_core.c:2611: error: unknown field &#8216;type&#8217; specified in initializer
/tmp/gspcav1-20071224/gspca_core.c: In function &#8216;spca50x_create_sysfs&#8217;:
/tmp/gspcav1-20071224/gspca_core.c:2769: error: implicit declaration of function &#8216;video_device_create_file&#8217;
/tmp/gspcav1-20071224/gspca_core.c:2780: error: implicit declaration of function &#8216;video_device_remove_file&#8217;
/tmp/gspcav1-20071224/gspca_core.c: In function &#8216;spca5xx_probe&#8217;:
/tmp/gspcav1-20071224/gspca_core.c:4301: error: incompatible types in assignment
make[2]: *** [/tmp/gspcav1-20071224/gspca_core.o] Error 1
make[1]: *** [_module_/tmp/gspcav1-20071224] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.27.8'


-
I up to now stand up to this difficulty: I havent find a how to that explain in very details howto :(
[http://forums.debian.net/viewtopic.php?t=34055](http://forums.debian.net/viewtopic.php?t=34055)
maybe ubuntu have more n00b oriented howto - kernels :)

---

### Post by frenchn00b on 2008-12-23
into /usr/src:
after the tar xvf 

```
:/usr/src/modules/spca5xx# make
   Building SPCA5XX driver for 2.5/2.6 kernel.
   Remember: you must have read/write access to your kernel source tree.
make -C /lib/modules/`uname -r`/build SUBDIRS=/usr/src/modules/spca5xx CC=cc modules
make[1]: Entering directory `/usr/src/linux-2.6.27.8'
scripts/Makefile.build:46: *** CFLAGS was changed in "/usr/src/modules/spca5xx/Makefile". Fix it to use EXTRA_CFLAGS.  Stop.
make[1]: *** [_module_/usr/src/modules/spca5xx] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.27.8'
make: *** [default] Error 2

```

following : 
[https://help.ubuntu.com/community/Spca5xx](https://help.ubuntu.com/community/Spca5xx)

So what now ?

---

### Post by frenchn00b on 2008-12-23
debug

```
 Considering target file `/usr/src/linux-2.6.27.8/scripts/Kbuild.include'.
  Finished prerequisites of target file `/usr/src/linux-2.6.27.8/scripts/Kbuild.include'.
 No need to remake target `/usr/src/linux-2.6.27.8/scripts/Kbuild.include'.
 Considering target file `Makefile'.
  Finished prerequisites of target file `Makefile'.
 No need to remake target `Makefile'.
Updating goal targets....
Considering target file `modules'.
 File `modules' does not exist.
  Considering target file `_module_/usr/src/linux-headers-2.6.27.8-ver02/modules/spca5xx'.
   File `_module_/usr/src/linux-headers-2.6.27.8-ver02/modules/spca5xx' does not exist.
    Considering target file `crmodverdir'.
     File `crmodverdir' does not exist.
     Finished prerequisites of target file `crmodverdir'.
    Must remake target `crmodverdir'.
Putting child 0x09ccc7e8 (crmodverdir) PID 14251 on the chain.
Live child 0x09ccc7e8 (crmodverdir) PID 14251 
Reaping winning child 0x09ccc7e8 PID 14251 
Removing child 0x09ccc7e8 PID 14251 from chain.
    Successfully remade target file `crmodverdir'.
    Considering target file `/usr/src/linux-2.6.27.8/Module.symvers'.
     File `/usr/src/linux-2.6.27.8/Module.symvers' does not exist.
     Finished prerequisites of target file `/usr/src/linux-2.6.27.8/Module.symvers'.
    Must remake target `/usr/src/linux-2.6.27.8/Module.symvers'.
Putting child 0x09ccf770 (/usr/src/linux-2.6.27.8/Module.symvers) PID 14265 on the chain.
Live child 0x09ccf770 (/usr/src/linux-2.6.27.8/Module.symvers) PID 14265 
Reaping winning child 0x09ccf770 PID 14265 
Removing child 0x09ccf770 PID 14265 from chain.
    Successfully remade target file `/usr/src/linux-2.6.27.8/Module.symvers'.
   Finished prerequisites of target file `_module_/usr/src/linux-headers-2.6.27.8-ver02/modules/spca5xx'.
  Must remake target `_module_/usr/src/linux-headers-2.6.27.8-ver02/modules/spca5xx'.
Putting child 0x09ccf8e8 (_module_/usr/src/linux-headers-2.6.27.8-ver02/modules/spca5xx) PID 14277 on the chain.
Live child 0x09ccf8e8 (_module_/usr/src/linux-headers-2.6.27.8-ver02/modules/spca5xx) PID 14277 
GNU Make 3.81
Copyright (C) 2006  Free Software Foundation, Inc.
This is free software; see the source for copying conditions.
There is NO warranty; not even for MERCHANTABILITY or FITNESS FOR A
PARTICULAR PURPOSE.

This program built for i486-pc-linux-gnu
Reading makefiles...
Reading makefile `scripts/Makefile.build'...
Reading makefile `include/config/auto.conf' (search path) (don't care) (no ~ expansion)...
Reading makefile `scripts/Kbuild.include' (search path) (no ~ expansion)...
Reading makefile `/usr/src/linux-headers-2.6.27.8-ver02/modules/spca5xx/Makefile' (search path) (no ~ expansion)...
scripts/Makefile.build:46: *** CFLAGS was changed in "/usr/src/linux-headers-2.6.27.8-ver02/modules/spca5xx/Makefile". Fix it to 
use EXTRA_CFLAGS.  Stop.
Reaping losing child 0x09ccf8e8 PID 14277 
make[1]: *** [_module_/usr/src/linux-headers-2.6.27.8-ver02/modules/spca5xx] Error 2
Removing child 0x09ccf8e8 PID 14277 from chain.
make[1]: Leaving directory `/usr/src/linux-2.6.27.8'
Reaping losing child 0x098616c8 PID 14156 
make: *** [default] Error 2
Removing child 0x098616c8 PID 14156 from chain.

```

---

