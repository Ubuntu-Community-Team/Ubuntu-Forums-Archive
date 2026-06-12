---
title: "Acer Aspire 5520 camera and mic problem"
date: 2008-06-12
forum: Hardware
---

### Post by iokmjo on 2008-06-12
I'm quite new to ubuntu and can't seem to make my camera and microphone work. I tried some of the stuff from the boards here but couldnt make them work. Please, help.

---

### Post by tihomir on 2008-11-18
> **iokmjo said:**
> I'm quite new to ubuntu and can't seem to make my camera and microphone work. I tried some of the stuff from the boards here but couldnt make them work. Please, help.


I've solved these problems by removing ALSA and using just OSS. I'm using debian etchnhalf, btw (2.6.24 kernel). Also, load up some mixer (I'm using XFCE4-mixer) and push up "Capture" and "Microphone boost" Audio even works on my Virtualbox host OS.

When I was using Xubuntu, I've solved the camera problem just by installing video4linux version 2 (v4l) and the camera worked!

T.C.

---

