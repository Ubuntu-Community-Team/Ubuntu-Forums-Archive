---
title: "will the webcam ever work?"
date: 2008-05-24
forum: Hardware
---

### Post by captainsmooty on 2008-05-24
hello hello
i am using a toshiba satellite a215-s4747, it is a vista laptop as we all know....  however since i have ubuntu on here, i wanted to know if the driver for the webcame exists. i know a lot of stuff is not compatible with ubuntu, but anything you guys can offer will be a great help. i kind of don't want to waste all of the technology that is in this thing. 
thanks for all your help  :D

---

### Post by hotweiss on 2008-05-24
This is what got my webcam working:

A) First we’ll need to install the files needed to build the driver by typing the following in Terminal:
> sudo apt-get install build-essential subversion linux-headers-`uname -r`

B) Now we will build the driver by typing the following commands in Terminal:
> cd /usr/src
and then
> sudo svn checkout svn://svn.berlios.de/linux-uvc/linux-uvc/trunk
and then
> cd trunk
and then
> sudo make
and then
> sudo cp -a uvcvideo.ko /lib/modules/`uname -r`/ubuntu/media/usbvideo/

C) Reboot, and your webcam will now be working.

---

### Post by daka on 2008-09-01
NO LUCK FOR ME ... an ideas

Satellite L300

daka@daka-TB:~$ cd /usr/src
daka@daka-TB:/usr/src$ sudo svn checkout svn://svn.berlios.de/linux-uvc/linux-uvc/trunk 
A    trunk/uvc_status.c
A    trunk/svn-version.sh
A    trunk/uvc_ctrl.c
A    trunk/uvc_queue.c
A    trunk/uvc_video.c
A    trunk/uvc_isight.c
A    trunk/uvc_v4l2.c
A    trunk/uvc_compat.h
A    trunk/uvc_driver.c
A    trunk/uvcvideo.h
A    trunk/Makefile
A    trunk/dynctrl.txt
Checked out revision 246.
daka@daka-TB:/usr/src$ cd trunk
daka@daka-TB:/usr/src/trunk$ sudo make
Building USB Video Class driver...
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-15-generic'
  CC [M]  /usr/src/trunk/uvc_driver.o
  CC [M]  /usr/src/trunk/uvc_queue.o
  CC [M]  /usr/src/trunk/uvc_v4l2.o
  CC [M]  /usr/src/trunk/uvc_video.o
  CC [M]  /usr/src/trunk/uvc_ctrl.o
  CC [M]  /usr/src/trunk/uvc_status.o
  CC [M]  /usr/src/trunk/uvc_isight.o
  LD [M]  /usr/src/trunk/uvcvideo.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /usr/src/trunk/uvcvideo.mod.o
  LD [M]  /usr/src/trunk/uvcvideo.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-15-generic'
daka@daka-TB:/usr/src/trunk$ sudo cp -a uvcvideo.ko /lib/modules/`uname -r`/ubuntu/media/usbvideo/
cp: target `/lib/modules/2.6.22-15-generic/ubuntu/media/usbvideo/' is not a directory: No such file or directory
daka@daka-TB:/usr/src/trunk$ sudo cp -a uvcvideo.ko /lib/modules/`uname -r`/ubuntu/media/usbvideo/ 
cp: target `/lib/modules/2.6.22-15-generic/ubuntu/media/usbvideo/' is not a directory: No such file or directory
daka@daka-TB:/usr/src/trunk$ sudo cp -a uvcvideo.ko /lib/modules/`uname -r`/ubuntu/media/usbvideo/ 
cp: target `/lib/modules/2.6.22-15-generic/ubuntu/media/usbvideo/' is not a directory: No such file or directory


Daka

---

