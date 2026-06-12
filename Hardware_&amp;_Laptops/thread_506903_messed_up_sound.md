---
title: "messed up sound"
date: 2007-07-22
forum: Hardware &amp; Laptops
---

### Post by davidsrsb on 2007-07-22
After a losing battle with on board usb sound, including building alsa 1.0.14, I gave up and installed an old CMI8738 pci card. This works under XP.

lspci sees the card
lsmod shows nothing loaded and modprobe snd-cmipci says that it can't find snd_cmipci

I tried to reinstall alsa-base etc

---

### Post by davidsrsb on 2007-07-23
Sorted, sound now works
I reinstalled the kernel and  the snd_cmipci module is loaded

---

### Post by Chymera on 2007-07-27
how do i do that?

---

