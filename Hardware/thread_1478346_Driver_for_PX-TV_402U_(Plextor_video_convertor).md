---
title: "Driver for PX-TV 402U (Plextor video convertor)"
date: 2010-05-09
forum: Hardware
---

### Post by lbarbosa on 2010-05-09
Hello,
 I have installed Ubuntu 9.10 Karmic (Kernel 2.6.31-21-generic).
I would like to run my PX-TV 402U convertX to watch TV and also record TV programs. This device is plugged into my computer via USB port. I have plugged it but Ubuntu does not recoginise. I found a reference from Nikosapi.org of a driver for this device (for the case of Ubuntu Hardy). I followed the installation procedure, which was indicated there, but the driver compilation gives an error. I copied the error messages that the compilation gives.
 ***** Using kernel source in /usr/src/linux-headers-2.6.31-21-generic *****
 make modules -C /usr/src/linux-headers-2.6.31-21-generic M=/home/lbarbosa/Downloads/wis-go7007-linux-0.9.8-2/kernel
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-21-generic'
  CC [M]  /home/lbarbosa/Downloads/wis-go7007-linux-0.9.8-2/kernel/go7007-v4l2.o
/home/lbarbosa/Downloads/wis-go7007-linux-0.9.8-2/kernel/go7007-v4l2.c:33:33: error: linux/video_decoder.h: No such file or directory
/home/lbarbosa/Downloads/wis-go7007-linux-0.9.8-2/kernel/go7007-v4l2.c:41:27: error: asm/semaphore.h: No such file or directory
/home/lbarbosa/Downloads/wis-go7007-linux-0.9.8-2/kernel/go7007-v4l2.c: In function ‘go7007_do_ioctl’:
/home/lbarbosa/Downloads/wis-go7007-linux-0.9.8-2/kernel/go7007-v4l2.c:797: error: implicit declaration of function ‘v4l2_video_std_construct’
/home/lbarbosa/Downloads/wis-go7007-linux-0.9.8-2/kernel/go7007-v4l2.c:878: error: ‘DECODER_SET_NORM’ undeclared (first use in this function)
/home/lbarbosa/Downloads/wis-go7007-linux-0.9.8-2/kernel/go7007-v4l2.c:878: error: (Each undeclared identifier is reported only once
/home/lbarbosa/Downloads/wis-go7007-linux-0.9.8-2/kernel/go7007-v4l2.c:878: error: for each function it appears in.)
/home/lbarbosa/Downloads/wis-go7007-linux-0.9.8-2/kernel/go7007-v4l2.c:942: error: ‘DECODER_SET_INPUT’ undeclared (first use in this function)
/home/lbarbosa/Downloads/wis-go7007-linux-0.9.8-2/kernel/go7007-v4l2.c: In function ‘go7007_ioctl’:
/home/lbarbosa/Downloads/wis-go7007-linux-0.9.8-2/kernel/go7007-v4l2.c:1354: error: implicit declaration of function ‘video_usercopy’
/home/lbarbosa/Downloads/wis-go7007-linux-0.9.8-2/kernel/go7007-v4l2.c: In function ‘go7007_vm_nopage’:
/home/lbarbosa/Downloads/wis-go7007-linux-0.9.8-2/kernel/go7007-v4l2.c:1390: error: ‘NOPAGE_SIGBUS’ undeclared (first use in this function)
/home/lbarbosa/Downloads/wis-go7007-linux-0.9.8-2/kernel/go7007-v4l2.c:1393: error: ‘NOPAGE_OOM’ undeclared (first use in this function)
/home/lbarbosa/Downloads/wis-go7007-linux-0.9.8-2/kernel/go7007-v4l2.c: At top level:
/home/lbarbosa/Downloads/wis-go7007-linux-0.9.8-2/kernel/go7007-v4l2.c:1403: error: unknown field ‘nopage’ specified in initializer
/home/lbarbosa/Downloads/wis-go7007-linux-0.9.8-2/kernel/go7007-v4l2.c:1403: warning: initialization from incompatible pointer type
/home/lbarbosa/Downloads/wis-go7007-linux-0.9.8-2/kernel/go7007-v4l2.c:1477: error: unknown field ‘type’ specified in initializer
/home/lbarbosa/Downloads/wis-go7007-linux-0.9.8-2/kernel/go7007-v4l2.c:1478: warning: initialization from incompatible pointer type
/home/lbarbosa/Downloads/wis-go7007-linux-0.9.8-2/kernel/go7007-v4l2.c: In function ‘go7007_v4l2_init’:
/home/lbarbosa/Downloads/wis-go7007-linux-0.9.8-2/kernel/go7007-v4l2.c:1491: error: incompatible types when assigning to type ‘struct device’ from type ‘struct device *’
make[2]: *** [/home/lbarbosa/Downloads/wis-go7007-linux-0.9.8-2/kernel/go7007-v4l2.o] Error 1
make[1]: *** [_module_/home/lbarbosa/Downloads/wis-go7007-linux-0.9.8-2/kernel] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-21-generic'
make: *** [all] Error 2
 I would appreciate very much if someone could help me to compile this driver or to get one that I can install directly.
 Thanks in advance,
 Luis Barbosa

---

### Post by abelloir on 2011-05-07
[http://ubuntuforums.org/showthread.php?t=1582023&highlight=go7007&page=2](http://ubuntuforums.org/showthread.php?t=1582023&highlight=go7007&page=2)

---

