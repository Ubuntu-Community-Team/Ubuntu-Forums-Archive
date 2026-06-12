---
title: "webcam isn't working in lubuntu"
date: 2013-11-21
forum: Hardware
---

### Post by ksuourgos on 2013-11-21
Hello. I have recently installed Lubuntu 13.04 and I am having a few problems.  I downloaded a program named cheese but if I run it all I see is a black screen. The webcam also doesn't work in Skype.  I opened the terminal and typed some commands that I found in threads in this forum that might be helpful. I would appreciate any help.


**lsusb**
Bus 001 Device 003: ID 045e:0766 Microsoft Corp. 
Bus 002 Device 002: ID 045e:0083 Microsoft Corp. Basic Optical Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub





**dmesg | grep "video"**
[    0.262841] pci 0000:01:00.0: Boot video device
[   13.911673] Linux video capture interface: v2.00
[   14.229722] uvcvideo: Found UVC 1.00 device Microsoft LifeCam VX-800 (045e:0766)
[   14.240494] usbcore: registered new interface driver uvcvideo
[  263.049275] uvcvideo: Failed to resubmit video URB (-1).
[  263.049305] uvcvideo: Failed to resubmit video URB (-1).
[  263.049334] uvcvideo: Failed to resubmit video URB (-1).
[  263.049361] uvcvideo: Failed to resubmit video URB (-1).





**lsmod | grep "video"**
uvcvideo               71279  0 
videobuf2_vmalloc      12920  1 uvcvideo
videobuf2_memops       13042  1 videobuf2_vmalloc
videobuf2_core         39161  1 uvcvideo
videodev               95806  2 uvcvideo,videobuf2_core
video                  18894  1 nouveau




Also if I press Alt&F2 and type **guvcview** a certain application opens but again I only see a black screen.

---

