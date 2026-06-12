---
title: "Unable to compile kernel module sn9Cxxx v 1.48"
date: 2008-11-21
forum: Hardware
---

### Post by jfraire on 2008-11-21
I have a usb "webcam" which appears as 0x0C45:0x602A. When I connect it, it is detected and the sn9c102 module driver is loaded (v1:1.47). However, it says it does not support the camera and therefore it is not working.

I found the source for sn9c102 at its newer version, 1.48, and it *does* support my camera. The problem is that, when following the instructions, I get the following warnings/error. 

Question 1: Is there a pre-packaged binary for this module I can get with Synaptic?

Question 2: In what package is sn9c102?

Question 3: What is needed to compile a kernel module from source? I already installed build-essentials and already had linux-headers packages.

I am running Ubuntu 8.04.

```
julio@albanta2:~/Desktop/webcam/sn9c1xx-1.48$ make modules
**************************************************************************
* Building Video4Linux2 driver v1.48 for SN9C1xx PC Camera Controllers...*
* Official Linux 2.6.19 is the minimum version for this driver.          *
* Read the documentation "sn9c102.txt" for more informations.            *
* Type "make help" for a list of available targets.                      *
**************************************************************************

make -C /lib/modules/`uname -r`/build M=/home/julio/Desktop/webcam/sn9c1xx-1.48 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-21-generic'
  CC [M]  /home/julio/Desktop/webcam/sn9c1xx-1.48/sn9c102_core.o
/home/julio/Desktop/webcam/sn9c1xx-1.48/sn9c102_core.c: In function ‘sn9c102_show_reg’:
/home/julio/Desktop/webcam/sn9c1xx-1.48/sn9c102_core.c:1041: warning: initialization from incompatible pointer type
/home/julio/Desktop/webcam/sn9c1xx-1.48/sn9c102_core.c: In function ‘sn9c102_store_reg’:
/home/julio/Desktop/webcam/sn9c1xx-1.48/sn9c102_core.c:1066: warning: initialization from incompatible pointer type
...
/home/julio/Desktop/webcam/sn9c1xx-1.48/sn9c102_core.c: In function ‘sn9c102_usb_probe’:
/home/julio/Desktop/webcam/sn9c1xx-1.48/sn9c102_core.c:3302: error: ‘struct video_device’ has no member named ‘hardware’
make[2]: *** [/home/julio/Desktop/webcam/sn9c1xx-1.48/sn9c102_core.o] Error 1
make[1]: *** [_module_/home/julio/Desktop/webcam/sn9c1xx-1.48] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-21-generic'
make: *** [modules] Error 2

```

---

