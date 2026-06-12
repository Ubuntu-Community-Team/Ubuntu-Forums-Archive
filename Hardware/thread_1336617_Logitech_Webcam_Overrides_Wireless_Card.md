---
title: "Logitech Webcam Overrides Wireless Card"
date: 2009-11-24
forum: Hardware
---

### Post by enigma__ on 2009-11-24
Hey, I have an issue with my webcam completely blocking out my wireless card.

I have a Toshiba Satellite A215-S7428 with one of those built-in usb wifi cards and a Logitech Tessar 2.0/3.7 usb webcam.

Whenever I try to plug in my webcam, my wireless card just refuses to work. I've tried restarting NetworkManager, unplugging the webcam, etc. but I can't make my card work again without rebooting my laptop. When I run lsusb, the output shows both devices, and appears to show no conflicts. Any advice?

BTW, the lsusb right now is:

```
Bus 001 Device 002: ID 0bda:8197 Realtek Semiconductor Corp. RTL8187B Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

---

### Post by trevor_e on 2009-11-28
I have the same problem with an A4tech MK 720J webcam: the logitec Quickcam for notebook Model v UBS47 just doesn't work.

---

### Post by enigma__ on 2009-12-23
Bump

---

### Post by Crafty Kisses on 2009-12-23
It could be a module problem, that's what I'm thinking. What you can do is before you plug the webcam in run:
```
lsmod
```
Then plug the camera and and run the exact same command, and see if you see any different results. Just post the results back here at the forums and either I or somebody else can look at it.

---

