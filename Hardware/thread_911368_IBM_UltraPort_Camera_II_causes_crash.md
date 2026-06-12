---
title: "IBM UltraPort Camera II causes crash"
date: 2008-09-05
forum: Hardware
---

### Post by MooNWalker on 2008-09-05
When I've tried to enable my IBM UltraPort Camera II in Skype, it crashed. The same with other programs that can use webcamera. My machine is ThinkPad T23 with latest firmware updates, camera worked fine under Windows when I still had it. All other problems I've already resolved - like no direct rendering or sound, but this one so far no results.

Here is the output of lsusb:
```
Bus 003 Device 002: ID 0461:0813 Primax Electronics, Ltd IBM UltraPort Camera
```
I've tried to follow this guide:
[How to install the IBM Ultracam II driver]("http://thinkwiki.org/wiki/How_to_install_the_IBM_Ultracam_II_driver")
Got kernel patch for kernel>=2.6.22.x (my kernel is 2.6.24-21-generic), unpacked it into ```
/lib/modules/2.6.24-21-generic/build/drivers/media/video/usbvideo/ultracam-2.6.22.2.c
```entered command ```
patch -p0 -i /lib/modules/2.6.24-21-generic/build/drivers/media/video/usbvideo/ultracam-2.6.22.2.c
``` and got this response:```
patch: **** Only garbage was found in the patch input.
```Headers for kernel 2.6.24.-21-generic are installed. Tried to search this forums, so far w/o results. xawtv gives this output:
```
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.24-21-generic)
xinerama 0: 1400x1050+0+0
/dev/video0 [v4l]: no overlay support
v4l-conf had some trouble, trying to continue anyway
Warning: Cannot convert string "-*-ledfixed-medium-r-*--39-*-*-*-c-*-*-*" to type FontStruct
ioctl: VIDIOCMCAPTURE(frame=0;height=4;width=8;format=7): Invalid argument
ioctl: VIDIOCMCAPTURE(frame=0;height=4;width=8;format=15): Invalid argument
v4l: timeout (got SIGALRM), hardware/driver problems?
ioctl: VIDIOCSYNC(int=0): Interrupted system call
ioctl: VIDIOCMCAPTURE(frame=0;height=4;width=8;format=5): Invalid argument
ioctl: VIDIOCMCAPTURE(frame=0;height=4;width=8;format=3): Invalid argument
ioctl: VIDIOCMCAPTURE(frame=0;height=4;width=8;format=1): Invalid argument
ioctl: VIDIOCMCAPTURE(frame=0;height=4;width=8;format=13): Invalid argument

``` What did I miss?

---

### Post by MooNWalker on 2008-09-05
OK, after [FONT="Courier New"]man patch[/FONT] I've realized that I've tried to patch using normal source code. After midnight will continue my search, meanwhile I would appreciate if someone can give me some clue as to how to make it work.

---

### Post by MooNWalker on 2008-09-06
Ok, so if I understand correctly, I need to compile module for kernel to enable it support my UltraPort Camera. I'm not sure what exactly I need to do to see the driver for it in the list of modules when I do make menuconfig. I'm lost. Can anybody help me out?

---

### Post by hsiehlc on 2012-03-07
hi there, I see this thread was last updated 2008. Just wondering if you ever made your IBM ultraport camera works on your T23? Since recently I also install Ubuntu 11.04 to my T23, and I have a Ultraport camera too.

---

