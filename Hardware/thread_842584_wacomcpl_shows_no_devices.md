---
title: "wacomcpl shows no devices"
date: 2008-06-27
forum: Hardware
---

### Post by starkes on 2008-06-27
Hey there,

I work at a place with a lot of wacoms kicking around, we're probably going to upgrade from fedora core 6 (yes its old) to ubuntu 8.04, but theres a few things in our way. wacom support is good but we still get calibration issues.

hardy heron does not come with wacomcpl somehow, but i installed it from the prebuilt folder that comes with the source for the linuxwacom driver from their website.

now i have wacomcpl, but when I open it, it doesn't show any devices. I've tried this on two machines with two different wacom tablets, (one is a cintiq actually) and they both have the same problem.

I do have all the normal stylus, eraser, and whatever the third one is inside my xorg.conf and the driver is working normally.

has anyone run into this before?

---

### Post by ceti331 on 2008-08-28
under ubuntu 8.04 i can get an intuous working but not the cintiq 12wx. it shows up under lsusb but not in /dev/input

---

### Post by fadumpt on 2009-10-20
I think it has to do with how the device is named.  It has to be compatible with wacomcpl.  I was kinda hoping there would be an answer to how to do that here though :(

---

### Post by Favux on 2009-10-20
Hi fadumpt,

It depends on what version of Ubuntu you are running, what model of Wacom tablet you have, and which version of linuxwacom you are using.

If you are in Jaunty or Karmic and using the default linuxwacom most tablet models work with wacomcpl if you use the modified wacom.fdi in post #176 here:  [http://ubuntuforums.org/showthread.php?t=967147&page=18](http://ubuntuforums.org/showthread.php?t=967147&page=18)

Unless your model is brand new.

---

