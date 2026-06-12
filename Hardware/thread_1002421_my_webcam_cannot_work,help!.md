---
title: "my webcam cannot work,help!"
date: 2008-12-05
forum: Hardware
---

### Post by jinzhong8120 on 2008-12-05
when i type lsusb,i got this:
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[COLOR="Red"]Bus 003 Device 004: ID 0ac8:301b Z-Star Microelectronics Corp. ZC0301 WebCam[/COLOR]
Bus 003 Device 003: ID 046d:c404 Logitech, Inc. TrackMan Wheel
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 0e8f:0002 GreenAsia Inc.
Bus 002 Device 003: ID 06a3:0006 Saitek PLC Cyborg Gold Joystick
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


so i use easycam2 to download the webcam driver,and it can work in cheese
but it cannot work in skype or camorama, when i want to test the webcam,the software ended itself.i'm a new in linux,so any help?

---

### Post by DieB on 2008-12-05
some one had a solution:
> 
have figured it out!

Simply running Ekiga didn't do it for me. I had to unload the modules in order.
Code:

sudo modprobe -r gspca
sudo modprobe -r zc0301
sudo modprobe -r videodev
sudo modprobe -r v4l1_compat

Now I load them back without the v4l1_compat
Code:

sudo modprobe gspca

It wasn't the v4l1_compat module after all, because it automatically get loaded. What didn't get loaded was the zc0301 module, and it worked when it wasn't loaded!

it is in that post:

[http://ubuntuforums.org/showthread.php?t=583132](http://ubuntuforums.org/showthread.php?t=583132)

hope it is a hint

---

