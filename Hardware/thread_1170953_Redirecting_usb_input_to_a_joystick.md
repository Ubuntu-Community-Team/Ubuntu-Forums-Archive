---
title: "Redirecting usb input to a joystick"
date: 2009-05-26
forum: Hardware
---

### Post by jimmyhilldrix on 2009-05-26
I'm currently running Ubuntu 9.04

A while ago, I build a SNES to usb converter as a small embedded systems project.  When I plug it into my computer I can cat data from it through /dev/input/event7 but it doesn't show up as a /dev/input/jsX.  I also need to be root to read data from it.

Is there any way to redirect what's comes through event7 into a joystick or simply have the usb device mount as a joystick that doesn't need root privileges?

Thanks

---

