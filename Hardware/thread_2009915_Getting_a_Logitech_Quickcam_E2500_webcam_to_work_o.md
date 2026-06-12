---
title: "Getting a Logitech Quickcam E2500 webcam to work on newer systems"
date: 2012-06-25
forum: Hardware
---

### Post by Lyfang on 2012-06-25
Hi, I cannot find an updated driver for a webcam Logitech Quickcam E 2500 webcam. It doesn't work with Cheese nor does it work with Skype. I'm using Lubuntu 12.04 LTS. I have tried the packages qc-usb-utils (utility programs for the QuickCam Express driver) & qc-usb-source (source for the QuickCam Express driver) without a result. I tried to compile the gspca Linux kernel module driver for the Logitech webcam, also without a result. Is there any driver present in the kernel tree?

Logitech Quickcam E2500 webcam & Ubuntu recommends the gspca driver? This driver worked with fine with 8.04, 9.10, 10.10? [https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams)

Are there any updated gspca drivers out there for Lubuntu 12.04 LTS?

See also: How to install webcam Logitech quickcam e2500  [http://ubuntuforums.org/showthread.php?t=1043579](http://ubuntuforums.org/showthread.php?t=1043579)
Logitech Quickcam E2500 not supported [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/326674](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/326674)
Logitech e2500 webcam doesn't work after upgrade to 11.10 [http://ubuntuforums.org/showthread.php?t=1860190](http://ubuntuforums.org/showthread.php?t=1860190)

---

### Post by Lyfang on 2012-07-04
Logitech Quickcam E2500 works with Cheese on Ubuntu 12.04 without an installation of a driver?
> **kjaspan said:**
> I have just installed Ubuntu 12.04 Precise on my new HP p1247 Pavilion x64 AMD computer. Previously I had Skype running, with some tweaks, on 11.10 on my old Dell E310 32 bit Intel Pentium PC.

My video works with Cheese but not with Skype 2.2.0.35 Beta for Linux/Ubuntu. I have tried many of the Forum threads, including those suggesting using LD_PRELOAD=LD_PRELOAD='/usr/lib32/libv4l/v4l1compat.so skype' after installing libv4l-0. I have a Logitech Quickcam E2500 series webcam.

Has anybody had the same problem or is there a solution somewhere?

Thanks in advance.

Are these instructions for legacy kernels only? [Re: How to install webcam Logitech quickcam e2500]("http://ubuntuforums.org/showpost.php?p=6574097&postcount=4")

If the Linux kernel dropped support for legacy products that might be the end for those that want to give their old PC a new life? Please help or this webcamera might decide to use Windows.

---

### Post by Lyfang on 2012-11-01
The webcam doesn't works in Ubuntu 12.10 (Quantal Quetzal) either using Skype. Is there a legacy kernel for Quantal? Since more and more disappear and the new kernels are often missing drivers or support for older hardware. Slackware has the 'huge' kernel with support for just about every driver in the Linux kernel, is there an equivalent in Ubuntu? New kernels also have new features and drivers that are merged in the Linux kernel, but the Logitech Quickcam E2500 webcam is an older piece of hardware.

---

