---
title: "help webcam on a vaio VNG FZ35G"
date: 2010-07-12
forum: Hardware
---

### Post by oneworld72 on 2010-07-12
ubuntu geek :)

I'm not new with ubuntu, been on and off several times and finally decide to remove all microsoft of my live :) good thing

been learning how to use linux and in particular ubuntu 10.04 LTS. all the installation was fine and i could find my way around the terminal and so on, but i'm having problems to connect the webcam on my VAIO VGNFZ35G 

I have look around to try to find a solution but all i found didn't solve my problem
 
[http://inshame.blogspot.com/2008/06/ubuntu-hardy-heron-on-sony-vaio-vgn.html](http://inshame.blogspot.com/2008/06/ubuntu-hardy-heron-on-sony-vaio-vgn.html)

the following is what happen in my Terminal, do you think you can help me or forword this message to someone that can.
thanks so much for your help

terminal:
 
nuno@Naires:~$ sudo gedit /etc/pm/config.d/unload_modules
[sudo] password for nuno: 
nuno@Naires:~$ sudo apt-get install subversion
Reading package lists... Done
Building dependency tree       
Reading state information... Done
subversion is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
nuno@Naires:~$ svn co [http://svn.mediati.org/svn/r5u870/trunk](http://svn.mediati.org/svn/r5u870/trunk) r5u870
A    r5u870/r5u870_183a.fw
A    r5u870/r5u870_183b.fw
A    r5u870/r5u870_1870_1.fw
A    r5u870/r5u870_183e.fw
A    r5u870/AUTHORS
A    r5u870/ChangeLog
A    r5u870/r5u870.c
A    r5u870/recode-fw.scm
A    r5u870/debug.mk
A    r5u870/README
A    r5u870/r5u870_1810.fw
A    r5u870/r5u870_1812.fw
A    r5u870/r5u870_1830.fw
A    r5u870/r5u870_1841.fw
A    r5u870/r5u870_1832.fw
A    r5u870/r5u870_1833.fw
A    r5u870/r5u870_1834.fw
A    r5u870/r5u870_1870.fw
A    r5u870/r5u870_1835.fw
A    r5u870/r5u870_1836.fw
A    r5u870/COPYING
A    r5u870/r5u870_1839.fw
A    r5u870/MAINTAINERS
A    r5u870/Kbuild
A    r5u870/usbcam
A    r5u870/usbcam/usbcam.h
A    r5u870/usbcam/usbcam_priv.h
A    r5u870/usbcam/usbcam_fops.c
A    r5u870/usbcam/usbcam_buf.c
A    r5u870/usbcam/usbcam_util.c
A    r5u870/usbcam/usbcam_dev.c
A    r5u870/usbcam/usbcam_skel.c
A    r5u870/usbcam/Makefile
A    r5u870/NEWS
A    r5u870/Makefile
Checked out revision 109.
nuno@Naires:~$ cd r5u870
nuno@Naires:~/r5u870$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
nuno@Naires:~/r5u870$ make
make -C /lib/modules/2.6.32-23-generic/build M=/home/nuno/r5u870 V=0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-23-generic'
  CC [M]  /home/nuno/r5u870/r5u870.o
/home/nuno/r5u870/r5u870.c:872:1: warning: "V4L2_CID_PRIVACY" redefined
In file included from include/linux/videodev.h:17,
                 from /home/nuno/r5u870/usbcam/usbcam.h:38,
                 from /home/nuno/r5u870/r5u870.c:59:
include/linux/videodev2.h:1160:1: warning: this is the location of the previous definition
  CC [M]  /home/nuno/r5u870/usbcam/usbcam_dev.o
/home/nuno/r5u870/usbcam/usbcam_dev.c: In function ‘usbcam_register_mod’:
/home/nuno/r5u870/usbcam/usbcam_dev.c:535: warning: assignment from incompatible pointer type
  CC [M]  /home/nuno/r5u870/usbcam/usbcam_fops.o
/home/nuno/r5u870/usbcam/usbcam_fops.c: In function ‘usbcam_v4l_vidioc_querycap’:
/home/nuno/r5u870/usbcam/usbcam_fops.c:522: error: ‘struct device’ has no member named ‘bus_id’
/home/nuno/r5u870/usbcam/usbcam_fops.c: In function ‘usbcam_v4l_ioctl’:
/home/nuno/r5u870/usbcam/usbcam_fops.c:1170: warning: passing argument 1 of ‘video_usercopy’ from incompatible pointer type
include/media/v4l2-ioctl.h:298: note: expected ‘struct file *’ but argument is of type ‘struct inode *’
/home/nuno/r5u870/usbcam/usbcam_fops.c:1170: warning: passing argument 2 of ‘video_usercopy’ makes integer from pointer without a cast
include/media/v4l2-ioctl.h:298: note: expected ‘unsigned int’ but argument is of type ‘struct file *’
/home/nuno/r5u870/usbcam/usbcam_fops.c:1170: warning: passing argument 4 of ‘video_usercopy’ makes pointer from integer without a cast
include/media/v4l2-ioctl.h:298: note: expected ‘v4l2_kioctl’ but argument is of type ‘long unsigned int’
/home/nuno/r5u870/usbcam/usbcam_fops.c:1170: error: too many arguments to function ‘video_usercopy’
/home/nuno/r5u870/usbcam/usbcam_fops.c:1174: warning: passing argument 1 of ‘video_ioctl2’ from incompatible pointer type
include/media/v4l2-ioctl.h:302: note: expected ‘struct file *’ but argument is of type ‘struct inode *’
/home/nuno/r5u870/usbcam/usbcam_fops.c:1174: warning: passing argument 2 of ‘video_ioctl2’ makes integer from pointer without a cast
include/media/v4l2-ioctl.h:302: note: expected ‘unsigned int’ but argument is of type ‘struct file *’
/home/nuno/r5u870/usbcam/usbcam_fops.c:1174: error: too many arguments to function ‘video_ioctl2’
/home/nuno/r5u870/usbcam/usbcam_fops.c:1162: warning: unused variable ‘udp’
make[3]: *** [/home/nuno/r5u870/usbcam/usbcam_fops.o] Error 1
make[2]: *** [/home/nuno/r5u870/usbcam] Error 2
make[1]: *** [_module_/home/nuno/r5u870] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-23-generic'
make: *** [all] Error 2
nuno@Naires:~/r5u870$ sudo make install
make -C /lib/modules/2.6.32-23-generic/build M=/home/nuno/r5u870 V=0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-23-generic'
  CC [M]  /home/nuno/r5u870/usbcam/usbcam_fops.o
/home/nuno/r5u870/usbcam/usbcam_fops.c: In function ‘usbcam_v4l_vidioc_querycap’:
/home/nuno/r5u870/usbcam/usbcam_fops.c:522: error: ‘struct device’ has no member named ‘bus_id’
/home/nuno/r5u870/usbcam/usbcam_fops.c: In function ‘usbcam_v4l_ioctl’:
/home/nuno/r5u870/usbcam/usbcam_fops.c:1170: warning: passing argument 1 of ‘video_usercopy’ from incompatible pointer type
include/media/v4l2-ioctl.h:298: note: expected ‘struct file *’ but argument is of type ‘struct inode *’
/home/nuno/r5u870/usbcam/usbcam_fops.c:1170: warning: passing argument 2 of ‘video_usercopy’ makes integer from pointer without a cast
include/media/v4l2-ioctl.h:298: note: expected ‘unsigned int’ but argument is of type ‘struct file *’
/home/nuno/r5u870/usbcam/usbcam_fops.c:1170: warning: passing argument 4 of ‘video_usercopy’ makes pointer from integer without a cast
include/media/v4l2-ioctl.h:298: note: expected ‘v4l2_kioctl’ but argument is of type ‘long unsigned int’
/home/nuno/r5u870/usbcam/usbcam_fops.c:1170: error: too many arguments to function ‘video_usercopy’
/home/nuno/r5u870/usbcam/usbcam_fops.c:1174: warning: passing argument 1 of ‘video_ioctl2’ from incompatible pointer type
include/media/v4l2-ioctl.h:302: note: expected ‘struct file *’ but argument is of type ‘struct inode *’
/home/nuno/r5u870/usbcam/usbcam_fops.c:1174: warning: passing argument 2 of ‘video_ioctl2’ makes integer from pointer without a cast
include/media/v4l2-ioctl.h:302: note: expected ‘unsigned int’ but argument is of type ‘struct file *’
/home/nuno/r5u870/usbcam/usbcam_fops.c:1174: error: too many arguments to function ‘video_ioctl2’
/home/nuno/r5u870/usbcam/usbcam_fops.c:1162: warning: unused variable ‘udp’
make[3]: *** [/home/nuno/r5u870/usbcam/usbcam_fops.o] Error 1
make[2]: *** [/home/nuno/r5u870/usbcam] Error 2
make[1]: *** [_module_/home/nuno/r5u870] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-23-generic'
make: *** [all] Error 2
nuno@Naires:~/r5u870$ sudo modprobe r5u870
FATAL: Module r5u870 not found.
nuno@Naires:~/r5u870$

---

