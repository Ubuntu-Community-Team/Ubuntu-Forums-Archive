---
title: "Phillips toucam pro 2"
date: 2005-05-29
forum: Hardware &amp; Laptops
---

### Post by Hackmo on 2005-05-29
I have a phillips toucam pro 2 and according to this page [http://www.ubuntulinux.org/wiki/HardwareSupportComponentsMultimediaWebCameras](http://www.ubuntulinux.org/wiki/HardwareSupportComponentsMultimediaWebCameras) it should work.  It is detected on boot up because the red light on top of the camera comes on.  However when I try to use my webcam with a program(camorama, xatv, gnomemeeting etc..) I get the error that the camera is already in use.  There is nothing else using the camera.  Any ideas?

---

### Post by Hackmo on 2005-07-08
bump


It's been awhile but I still have this problem.  Does anyone have any ideas at all?


When I run lsusb I get this

> root@ubuntu:/home/sean13 # lsusb
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 002: ID 0471:0311 Philips PCVC740K ToUcam Pro [pwc]
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

and when I run "tail -f /var/log/messages" while unplugging the camera I get

> Jul  8 05:37:16 localhost -- MARK --
Jul  8 05:57:20 localhost -- MARK --
Jul  8 06:17:21 localhost -- MARK --
Jul  8 06:37:22 localhost -- MARK --
Jul  8 06:40:30 localhost kernel: pwc Too many ISOC errors, bailing out.
Jul  8 06:40:30 localhost kernel: pwc Too many ISOC errors, bailing out.
Jul  8 06:40:30 localhost kernel: usb 3-2: USB disconnect, address 2
Jul  8 06:40:31 localhost kernel: pwc Too many ISOC errors, bailing out.
Jul  8 06:40:31 localhost kernel: pwc Too many ISOC errors, bailing out.
Jul  8 06:40:31 localhost kernel: pwc Disconnected while webcam is in use!


when I plug the camera back in nothing happens.

---

### Post by Hackmo on 2005-07-13
another bump

i've noticed that when I run lsusb after I un-plug the camera and then plug it back in while the computer is on nothing will happen in the terminal, it just hangs and I can't get back out of it with pressing ctrl + c.

---

