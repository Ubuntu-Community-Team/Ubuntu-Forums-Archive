---
title: "logitech quickcam express hell"
date: 2008-11-12
forum: Hardware
---

### Post by rauko113 on 2008-11-12
very frustrated at this point.
ubuntu gutsy doesnt want to acknowledge my webcam, logitech quickcam express.
reviewed many forums and installed the correct drivers from: [http://qce-ga.sourceforge.net/](http://qce-ga.sourceforge.net/).  Still no luck.  when i plug it in, it appears in the /dev/bus/usb/ directories but when i run any video programs (skype, camorama), a webcam is not detected.  Please lead me to salvation!
much love-
kgood

---

### Post by doug1212 on 2008-11-12
Hi,
what is the name of the webcam:

```
lsusb
```

Also have you any other video devices such as TV card installed because most video apps default to /dev/video0.
With my logi webcam I start with:

```
camorama -d /dev/video1
```

Doug.

---

### Post by Lexicon101 on 2008-11-12
I've had problems with the USB controller and logitech webcams before.
If all else fails, (don't even TRY this with a USB keyboard, its purpose is to take down your USB controller, then put it back up..) if you have the drivers you should, and if your webcam is listed correctly under lsusb, if you're getting random moments of working in with the failure under something like guvcview, if you've tried all the other fixes, and you're comfortable messing with the USB stuff a little, run these commands..
```
sudo modprobe -r ehci_hcd
sudo modprobe ehci_hcd
```
Remember to wait a second before you run the second command to put it back up, because the system may not recognise that it's down yet..
Anyway, use this as a last resort if all the signs point to USB controller failure.
Don't use it if the drivers just don't work.
(I'm not gonna start trying to tell you how to figure out what the problem's with, it took me ages to figure it out, and it'd take me ages to explain it.)

---

### Post by rauko113 on 2008-11-13
hey yea after entering lsusb:
```

Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 002: ID 046d:08af Logitech, Inc.
Bus 001 Device 001: ID 0000:0000

```
So the system seems to recognize the camera, but then after entering camorama -d /dev/bus/usb/001/002, a message pops up: Could not connect to video device.  After trying the modprobe ehci_hcd, same thing happens.  Is there something I'm missing?
Thank you guys for your responses.  I feel like im close to getting this thing to work

---

### Post by doug1212 on 2008-11-13
Hi,
Possible kernel bug???

[HTML]https://bugs.launchpad.net/ubuntu/+source/linux/+bug/255678[/HTML]

---

