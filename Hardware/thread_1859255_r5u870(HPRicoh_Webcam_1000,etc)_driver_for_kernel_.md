---
title: "* r5u870(HP/Ricoh Webcam 1000,etc) driver for kernel 2.6.x~3.0 (for Ubuntu 11.10 too)"
date: 2011-10-13
forum: Hardware
---

### Post by 3pei on 2011-10-13
here it is: [http://r5u870.googlecode.com/](http://r5u870.googlecode.com/), plz download the latest one (0.2a).

hope it useful for you.

if you want to report a problem, plz report it with your kernel version and other details.

---

### Post by genepool on 2011-10-27
Running 11.10 and I cant seem to build the module. Here is my terminal log:

```
avi@vaiolin:~/Desktop/r5u870$ make
make -C /lib/modules/3.0.0-13-generic/build M=/home/avi/Desktop/r5u870 V=0 modules
make[1]: Entering directory `/usr/src/linux-headers-3.0.0-13-generic'
  CC [M]  /home/avi/Desktop/r5u870/r5u870.o
  CC [M]  /home/avi/Desktop/r5u870/usbcam/usbcam_dev.o
  CC [M]  /home/avi/Desktop/r5u870/usbcam/usbcam_fops.o
/home/avi/Desktop/r5u870/usbcam/usbcam_fops.c: In function ‘usbcam_v4l_open’:
/home/avi/Desktop/r5u870/usbcam/usbcam_fops.c:133:5: warning: ISO C90 forbids mixed declarations and code [-Wdeclaration-after-statement]
/home/avi/Desktop/r5u870/usbcam/usbcam_fops.c: In function ‘usbcam_v4l_ioctl’:
/home/avi/Desktop/r5u870/usbcam/usbcam_fops.c:1191:27: warning: unused variable ‘udp’ [-Wunused-variable]
/home/avi/Desktop/r5u870/usbcam/usbcam_fops.c: At top level:
/home/avi/Desktop/r5u870/usbcam/usbcam_fops.c:1227:2: error: unknown field ‘compat_ioctl’ specified in initializer
/home/avi/Desktop/r5u870/usbcam/usbcam_fops.c:1227:18: error: ‘v4l_compat_ioctl32’ undeclared here (not in a function)
/home/avi/Desktop/r5u870/usbcam/usbcam_fops.c:58:20: warning: ‘v4l_ioctl_names’ defined but not used [-Wunused-variable]
/home/avi/Desktop/r5u870/usbcam/usbcam_fops.c:943:13: warning: ‘usbcam_v4l_int_ioctl’ defined but not used [-Wunused-function]
make[3]: *** [/home/avi/Desktop/r5u870/usbcam/usbcam_fops.o] Error 1
make[2]: *** [/home/avi/Desktop/r5u870/usbcam] Error 2
make[1]: *** [_module_/home/avi/Desktop/r5u870] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.0.0-13-generic'
make: *** [all] Error 2

```

---

