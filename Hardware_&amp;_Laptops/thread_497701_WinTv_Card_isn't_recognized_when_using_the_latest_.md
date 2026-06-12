---
title: "WinTv Card isn't recognized when using the latest Ubuntu Kernel"
date: 2007-07-10
forum: Hardware &amp; Laptops
---

### Post by seriousstorm85 on 2007-07-10
I have a Wintv-USB tv card. When I plugin the usb of the tv card on my laptop, The Hardware Information window picks up the usb, however it says its "Unknown"(0x4d29).

I am using the latest kernel for Ubuntu Fiesty Fawn (2.6.20-16)

However doing modprobe usbvision in the terminal and then trying TvTime, I get the following information on TvTime:-

No Source

Frames Too Short from Usbvision
Cannot Open Capture device /dev/video0.


Here is an extract related to usbvision of what it says when doing dmesg on the terminal

 usb 1-2: configuration #1 chosen from 4 choices
[ 1126.536000] drivers/media/video/usbvision/usbvision-video.c: usbvision_probe: Hauppauge WinTv-USB Model 40205 Rev B298 found
[ 1126.540000] drivers/media/video/usbvision/usbvision-video.c: USBVision[1]: registered USBVision Video device /dev/video0 [v4l2]
[ 1126.540000] drivers/media/video/usbvision/usbvision-video.c: USBVision[1]: registered USBVision VBI device /dev/vbi0 [v4l2] (Not Working Yet!)

---

### Post by wieman01 on 2007-08-24
I have a WinTv-USB Model 40205 Rev B298 and could not get it to work. This one, however, does:

[http://ubuntuforums.org/showthread.php?t=533528]("http://ubuntuforums.org/showthread.php?t=533528")

It's a Hauppauge WinTV Nova-T Stick. Works after installing the firmware and using Kaffeine. Great & inexpensive solution.

---

### Post by Siph0n on 2007-10-17
Hi. I have this old wintv usb tv tuner and wanted to try and get it to work. When I plug it in, I see the following in dmesg:

[ 2656.444000] usb 2-1: new full speed USB device using uhci_hcd and address 3
[ 2656.932000] usb 2-1: configuration #1 chosen from 4 choices
[ 2656.936000] drivers/media/video/usbvision/usbvision-video.c: usbvision_probe: Hauppauge WinTv-USB II (PAL) FM Model 40201 Rev B226 found
[ 2656.936000] drivers/media/video/usbvision/usbvision-video.c: USBVision[1]: registered USBVision Video device /dev/video0 [v4l2]
[ 2656.936000] drivers/media/video/usbvision/usbvision-video.c: USBVision[1]: registered USBVision Radio device /dev/radio0 [v4l2]
[ 2656.936000] drivers/media/video/usbvision/usbvision-video.c: USBVision[1]: registered USBVision VBI device /dev/vbi0 [v4l2] (Not Working Yet!)


However when I start tvtime I see the following error message:

Frames Too Short from Usbvision
Cannot Open Capture device /dev/video0.


Does anyone have any ideas how to get this to work, or even if its compatible or not??? Thanks! :) I know mythtv is out there, but that seems like a lot of work just to watch tv and record a show ;)

---

### Post by braddock on 2008-02-10
I am having this problem as described above as well.

$ cat /etc/issue
Ubuntu 7.04 \n \l

$ uname -a
Linux  2.6.20-16-generic #2 SMP Fri Feb 1 02:59:08 UTC 2008 i686 GNU/Linux

$ lsusb
[...snip....]
Bus 004 Device 003: ID 0573:4d10 Zoran Co. Personal Media Division (Nogatech) Hauppauge WinTV-USB with FM USA radio

$ dpkg -l
ii  tvtime         1.0.2-0.2ubunt A high quality television application

Dell Inspiron E1505N (linux pre-installed but fully up-to-date).

When I try playing in zapper, it does bring up a screen of static, but any attempt to edit channels crashes.  

xawtv will bring up static.  Channel editor crashes on me.

---

### Post by braddock on 2008-02-14
Note, I _AM_ able to watch video using the S-Video input on my WinTV USB using xawtv.  It seems that tuning is just broken, and that something about the driver doesn't play nice with most of the video players.

I had to use `xawtv -nodga` to get xawtv to launch.

---

