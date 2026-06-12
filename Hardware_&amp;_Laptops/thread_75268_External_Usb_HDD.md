---
title: "External Usb HDD"
date: 2005-10-13
forum: Hardware &amp; Laptops
---

### Post by born_confused on 2005-10-13
It seems an external hdd doesnt automount. I inserted a 512 mb usb stick and it automounted fine, however a usb 15 gig external hdd didnt. I did however manage to mount it manually. Why is this so? How do I resolve this?

More information

As I said earlier I can mount manually, yet, when running gnome-volume-manager on terminal, to observe output, I plugged in the 15 gig and it says this

manager.c/1642: not a mountable volume: /org/freedesktop/Hal/devices/storage_model_MHN2150AT

---

### Post by born_confused on 2005-10-13
Ok im sure this is a bug, however I am no good with bugzilla, put it this way, having had a look at the source code of gnome-volume-manager, with a usb stick it mounts as it considers it removable, however an external hard disk is well for my case anyway just a normal hard disk with casing, not removable. Both usb stick and usb hdd say not mountable, but gvm shows some sort of switch which allows the stick to mount and not usb hdd.

---

### Post by grinias on 2005-10-18
[QUOTE=born_confused]Ok im sure this is a bug, however I am no good with bugzilla, put it this way, having had a look at the source code of gnome-volume-manager, with a usb stick it mounts as it considers it removable, however an external hard disk is well for my case anyway just a normal hard disk with casing, not removable. Both usb stick and usb hdd say not mountable, but gvm shows some sort of switch which allows the stick to mount and not usb hdd.[/QUOTE]

I have exactly the same problem. Any suggestion?

---

