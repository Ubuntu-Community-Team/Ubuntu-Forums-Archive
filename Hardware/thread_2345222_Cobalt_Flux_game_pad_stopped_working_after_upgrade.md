---
title: "Cobalt Flux game pad stopped working after upgrade to 16.04"
date: 2016-12-01
forum: Hardware
---

### Post by frostline64 on 2016-12-01
This is my game pad for Stepmania.  The pad still works on my Win2k machine.  System Settings/Input Devices/Joystick, jstest-gtk and Stepmania recognize the device "Cobalt Flux Controller (/dev/js0)".  They list 27 axes and 19 buttons (The pad consists of a start and select button and 8 buttons on the mat itself.) on the device, but won't recognize any input from the pad.  Calibration does nothing.  I think I need some help here.

---

### Post by frostline64 on 2016-12-04
I was able to replicate the problem on my laptop... an upgrade to 16.04 broke the game pad.  

I played around with a "antimicro", a gui which maps keys to the gamepad, but no success.  The computer still recognizes the device but cannot detect any input from the device.  Is there any way I can try force reverting to old drivers for this?

---

