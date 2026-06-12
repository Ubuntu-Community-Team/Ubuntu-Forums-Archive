---
title: "How do I undo what Easycam did to my system"
date: 2008-08-09
forum: Hardware
---

### Post by merllin on 2008-08-09
Ubuntu used to detect my Creative webcam no problem, but then I stupidly ran "easycam" on another webcam (a Bresser Microscope cam) and now I cant use the Creative webcam. How can I undo the changes it has made and get back to the state that it was. I do not want to re-install Ubuntu from scratch as I have spent 2 weeks getting how I want. Thanks!

---

### Post by scarf on 2009-05-26
i would like to know how to do this too...

it looks like it compiled and installed its own drivers, but i don't know how to uninstall.  simply uninstalling easycam doesn't work.

the easycam website is in french, so that isn't much help to me.

this is what happened when i told it to install the driver, maybe someone knows how to reverse it?

```

$ gksudo 'python /usr/share/EasyCam2/core.py --gtk'
GO !
ln: creating symbolic link `/lib/modules/2.6.27-14-generic/build/include/linux/config.h': File exists
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.27-14-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
rm -f *.o *.ko .*.cmd .*.flags *.mod.c Module.symvers version.h modules.order
rm -rf .tmp_versions
Building USB Video Class driver...
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-14-generic'
  CC [M]  /usr/share/EasyCam2/drivers/uvc/uvc_driver.o
  CC [M]  /usr/share/EasyCam2/drivers/uvc/uvc_queue.o
  CC [M]  /usr/share/EasyCam2/drivers/uvc/uvc_v4l2.o
  CC [M]  /usr/share/EasyCam2/drivers/uvc/uvc_video.o
  CC [M]  /usr/share/EasyCam2/drivers/uvc/uvc_ctrl.o
  CC [M]  /usr/share/EasyCam2/drivers/uvc/uvc_status.o
  CC [M]  /usr/share/EasyCam2/drivers/uvc/uvc_isight.o
  LD [M]  /usr/share/EasyCam2/drivers/uvc/uvcvideo.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: could not open /usr/share/EasyCam2/drivers/uvc/version.h: Invalid argument
  CC      /usr/share/EasyCam2/drivers/uvc/uvcvideo.mod.o
  LD [M]  /usr/share/EasyCam2/drivers/uvc/uvcvideo.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-14-generic'
Installing USB Video Class driver...
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-14-generic'
  INSTALL /usr/share/EasyCam2/drivers/uvc/uvcvideo.ko
  DEPMOD  2.6.27-14-generic
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-14-generic'
$ 

```

thanks.

---

