---
title: "IVTV compiling problems"
date: 2005-02-03
forum: Hardware &amp; Laptops
---

### Post by naj_geetsrev on 2005-02-03
Well, problems.... it doesn't compile at all. I have a PVR-150 and I am trying to compile the 0.3.2d IVTV drivers. But when ik make, the following is the output (or at least a part of the output):

root@ubuntu:~/ivtv-0.3.2d/driver # make | more
make -C /lib/modules/2.6.10-2-686/build SUBDIRS=/home/najgeetsrev/ivtv-0.3.2d/driver modules
make[1]: Entering directory `/usr/src/linux-source-2.6.10'
Makefile:484: .config: No such file or directory
grep: /lib/modules/2.6.10-2-686/build/.config: No such file or directory
  CC [M]  /home/najgeetsrev/ivtv-0.3.2d/driver/tuner.o
In file included from include/linux/module.h:9,
                 from /home/najgeetsrev/ivtv-0.3.2d/driver/tuner.c:1:
include/linux/config.h:4:28: linux/autoconf.h: No such file or directory
In file included from include/linux/module.h:10,
                 from /home/najgeetsrev/ivtv-0.3.2d/driver/tuner.c:1:
include/linux/sched.h:4:37: asm/param.h: No such file or directory
In file included from include/linux/types.h:13,
                 from include/linux/capability.h:16,
                 from include/linux/sched.h:7,
                 from include/linux/module.h:10,
                 from /home/najgeetsrev/ivtv-0.3.2d/driver/tuner.c:1:
include/linux/posix_types.h:47:29: asm/posix_types.h: No such file or directory
In file included from include/linux/capability.h:16,
                 from include/linux/sched.h:7,
                 from include/linux/module.h:10,
                 from /home/najgeetsrev/ivtv-0.3.2d/driver/tuner.c:1:
include/linux/types.h:14:23: asm/types.h: No such file or directory
In file included from include/linux/capability.h:16,
                 from include/linux/sched.h:7,
                 from include/linux/module.h:10,
                 from /home/najgeetsrev/ivtv-0.3.2d/driver/tuner.c:1:
include/linux/types.h:18: error: syntax error before "__kernel_dev_t"
include/linux/types.h:18: warning: type defaults to `int' in declaration of `__kernel_dev_t'
include/linux/types.h:18: warning: data definition has no type or storage class
include/linux/types.h:21: error: syntax error before "dev_t"
include/linux/types.h:21: warning: type defaults to `int' in declaration of `dev_t'
include/linux/types.h:21: warning: data definition has no type or storage class
include/linux/types.h:22: error: syntax error before "ino_t"
include/linux/types.h:22: warning: type defaults to `int' in declaration of `ino_t'
include/linux/types.h:22: warning: data definition has no type or storage class
include/linux/types.h:23: error: syntax error before "mode_t"
include/linux/types.h:23: warning: type defaults to `int' in declaration of `mode_t'
include/linux/types.h:23: warning: data definition has no type or storage class
include/linux/types.h:24: error: syntax error before "nlink_t"
include/linux/types.h:24: warning: type defaults to `int' in declaration of `nlink_t'
include/linux/types.h:24: warning: data definition has no type or storage class
include/linux/types.h:25: error: syntax error before "off_t"

and so on, and so on

Can anybody help me  :roll:

---

### Post by laura.c on 2005-03-28
Most of the popular new PVR cards sold for Windows XP MC are based on Connexant's "Blackbird" design, which hasn't had drivers for Linux or Myth.

We have been working on these drivers and released an alpha version at [http://plutohome.com](http://plutohome.com). Pluto even has a self-booting kick-start CD that will automatically install & configure everything for you, including a ready-to-go Myth system. It's the fastest and easiest way to get a MythTV PVR up and running, and also installs Xine, Asterisk and our own software to give you the most advanced media & entertainment, home automation, security, telecom & computing system, controllable with your Symbian Bluetooth mobile phone, as well as PDA's and Webpads.

We're working hard to harden the drivers as quickly as possible and would like as much feedback as possible. These 2nd generation "Blackbird" cards are lower in price and offer better picture quality than the current models supported in IVTV, so be sure to check them out.

visit: plutohome.com, click 'support', 'support site', and choose "CX88 Blackbird Drivers" from the projects menu

---

### Post by candc540 on 2005-04-01
[QUOTE=naj_geetsrev]Well, problems.... it doesn't compile at all. I have a PVR-150 and I am trying to compile the 0.3.2d IVTV drivers. But when ik make, the following is the output (or at least a part of the output):

root@ubuntu:~/ivtv-0.3.2d/driver # make | more
make -C /lib/modules/2.6.10-2-686/build SUBDIRS=/home/najgeetsrev/ivtv-0.3.2d/driver modules
make[1]: Entering directory `/usr/src/linux-source-2.6.10'
Makefile:484: .config: No such file or directory
grep: /lib/modules/2.6.10-2-686/build/.config: No such file or directory
  CC [M]  /home/najgeetsrev/ivtv-0.3.2d/driver/tuner.o
In file included from include/linux/module.h:9,
                 from /home/najgeetsrev/ivtv-0.3.2d/driver/tuner.c:1:
include/linux/config.h:4:28: linux/autoconf.h: No such file or directory
In file included from include/linux/module.h:10,
                 from /home/najgeetsrev/ivtv-0.3.2d/driver/tuner.c:1:
include/linux/sched.h:4:37: asm/param.h: No such file or directory
In file included from include/linux/types.h:13,
                 from include/linux/capability.h:16,
                 from include/linux/sched.h:7,
                 from include/linux/module.h:10,
                 from /home/najgeetsrev/ivtv-0.3.2d/driver/tuner.c:1:
include/linux/posix_types.h:47:29: asm/posix_types.h: No such file or directory
In file included from include/linux/capability.h:16,
                 from include/linux/sched.h:7,
                 from include/linux/module.h:10,
                 from /home/najgeetsrev/ivtv-0.3.2d/driver/tuner.c:1:
include/linux/types.h:14:23: asm/types.h: No such file or directory
In file included from include/linux/capability.h:16,
                 from include/linux/sched.h:7,
                 from include/linux/module.h:10,
                 from /home/najgeetsrev/ivtv-0.3.2d/driver/tuner.c:1:
include/linux/types.h:18: error: syntax error before "__kernel_dev_t"
include/linux/types.h:18: warning: type defaults to `int' in declaration of `__kernel_dev_t'
include/linux/types.h:18: warning: data definition has no type or storage class
include/linux/types.h:21: error: syntax error before "dev_t"
include/linux/types.h:21: warning: type defaults to `int' in declaration of `dev_t'
include/linux/types.h:21: warning: data definition has no type or storage class
include/linux/types.h:22: error: syntax error before "ino_t"
include/linux/types.h:22: warning: type defaults to `int' in declaration of `ino_t'
include/linux/types.h:22: warning: data definition has no type or storage class
include/linux/types.h:23: error: syntax error before "mode_t"
include/linux/types.h:23: warning: type defaults to `int' in declaration of `mode_t'
include/linux/types.h:23: warning: data definition has no type or storage class
include/linux/types.h:24: error: syntax error before "nlink_t"
include/linux/types.h:24: warning: type defaults to `int' in declaration of `nlink_t'
include/linux/types.h:24: warning: data definition has no type or storage class
include/linux/types.h:25: error: syntax error before "off_t"

and so on, and so on

Can anybody help me  :roll:[/QUOTE]

Make sure you have installed the kernel-headers. ( apt-get install kernel-headers-`uname -r`)

Try the make in the ivtv directory again. I would try upgrading to 0.3.2i or greater of ivtv and follow the instructions very carefully in the quicksetup or quickinstall in the doc directory.

---

