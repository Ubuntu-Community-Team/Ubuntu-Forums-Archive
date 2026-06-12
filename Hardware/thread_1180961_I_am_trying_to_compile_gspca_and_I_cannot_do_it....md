---
title: "I am trying to compile gspca and I cannot do it..."
date: 2009-06-07
forum: Hardware
---

### Post by foottuns on 2009-06-07
hello there, i want to install gspca for my webcam is a Microsoft VX1000 webcam and i cannot do it. I have the source code and every time when I run ./gspca_buil I get this error, can any one help me here please.


```
root@Bogdan-Ubuntu:/usr/src/gspcav1-20071224# ./gspca_build 

 REMOVE the old module if present
ERROR: Module gspca does not exist in /proc/modules

 CLEAN gspca source tree
rm -r -f *.o decoder/.gspcadecoder.o.cmd decoder/*.o \
    .gspca.o.cmd  *.o *.ko *.mod.* .[a-z]* core *.i \
    *.symvers *.err

 COMPILE gspca Please Wait ....!!

 INSTALL gspca in the kernel binary tree
mkdir -p /lib/modules/`uname -r`/kernel/drivers/usb/media/
rm -f /lib/modules/`uname -r`/kernel/drivers/usb/media/spca5xx.ko
rm -f /lib/modules/`uname -r`/kernel/drivers/media/video/gspca.ko
install -c -m 0644 gspca.ko /lib/modules/`uname -r`/kernel/drivers/usb/media/
install: cannot stat `gspca.ko': No such file or directory
make: *** [install] Error 1

 LOAD gspca in memory 
WARNING: All config files need .conf: /etc/modprobe.d/blacklist-custom, it will be ignored in a future release.
FATAL: Module gspca not found.

 PRINT COMPILATION MESSAGES if ERRORS look kgspca.err 
make -C /lib/modules/`uname -r`/build SUBDIRS=/usr/src/gspcav1-20071224 CC=cc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
  CC [M]  /usr/src/gspcav1-20071224/gspca_core.o
/usr/src/gspcav1-20071224/gspca_core.c:54:27: error: asm/semaphore.h: No such file or directory
/usr/src/gspcav1-20071224/gspca_core.c: In function ‘spca5xx_ioctl’:
/usr/src/gspcav1-20071224/gspca_core.c:2463: error: implicit declaration of function ‘video_usercopy’
/usr/src/gspcav1-20071224/gspca_core.c: At top level:
/usr/src/gspcav1-20071224/gspca_core.c:2609: error: unknown field ‘owner’ specified in initialiser
/usr/src/gspcav1-20071224/gspca_core.c:2609: warning: initialisation from incompatible pointer type
/usr/src/gspcav1-20071224/gspca_core.c:2611: error: unknown field ‘type’ specified in initialiser
/usr/src/gspcav1-20071224/gspca_core.c: In function ‘spca50x_create_sysfs’:
/usr/src/gspcav1-20071224/gspca_core.c:2769: error: implicit declaration of function ‘video_device_create_file’
/usr/src/gspcav1-20071224/gspca_core.c:2780: error: implicit declaration of function ‘video_device_remove_file’
/usr/src/gspcav1-20071224/gspca_core.c: In function ‘spca5xx_probe’:
/usr/src/gspcav1-20071224/gspca_core.c:4301: error: incompatible types in assignment
make[2]: *** [/usr/src/gspcav1-20071224/gspca_core.o] Error 1
make[1]: *** [_module_/usr/src/gspcav1-20071224] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
make: *** [default] Error 2
root@Bogdan-Ubuntu:/usr/src/gspcav1-20071224# 

```

---

### Post by foottuns on 2009-06-07
now i have checked the kgspca.err and get these errors......

```
make -C /lib/modules/`uname -r`/build SUBDIRS=/usr/src/gspcav1-20071224 CC=cc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
  CC [M]  /usr/src/gspcav1-20071224/gspca_core.o
/usr/src/gspcav1-20071224/gspca_core.c:54:27: error: asm/semaphore.h: No such file or directory
/usr/src/gspcav1-20071224/gspca_core.c: In function ‘spca5xx_ioctl’:
/usr/src/gspcav1-20071224/gspca_core.c:2466: error: implicit declaration of function ‘video_usercopy’
/usr/src/gspcav1-20071224/gspca_core.c: At top level:
/usr/src/gspcav1-20071224/gspca_core.c:2612: error: unknown field ‘owner’ specified in initialiser
/usr/src/gspcav1-20071224/gspca_core.c:2612: warning: initialisation from incompatible pointer type
/usr/src/gspcav1-20071224/gspca_core.c:2614: error: unknown field ‘type’ specified in initialiser
/usr/src/gspcav1-20071224/gspca_core.c: In function ‘spca50x_create_sysfs’:
/usr/src/gspcav1-20071224/gspca_core.c:2772: error: implicit declaration of function ‘video_device_create_file’
/usr/src/gspcav1-20071224/gspca_core.c:2783: error: implicit declaration of function ‘video_device_remove_file’
/usr/src/gspcav1-20071224/gspca_core.c: In function ‘spca5xx_probe’:
/usr/src/gspcav1-20071224/gspca_core.c:4314: error: incompatible types in assignment
make[2]: *** [/usr/src/gspcav1-20071224/gspca_core.o] Error 1
make[1]: *** [_module_/usr/src/gspcav1-20071224] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
make: *** [default] Error 2
```

---

### Post by cariboo on 2009-06-07
What kernel version are you running? If unsure open System-->Administration-->System Monitor-->System.

As of Jaunty, kernel 2.6.28 that driver will not compile. 

Are you sure the driver for your webcam is not already loaded, myy Logitech Quickcam Messanger uses the gspca driver and it is auto loaded on boot:

```
lsmod | grep spca
```

shows me:

```
gspca_zc3xx            52128  0 
gspca_main             26528  1 gspca_zc3xx
videodev               42624  4 tuner,saa7134,gspca_main,v4l2_common
```

The saa7134 is my tv tuner card.

---

