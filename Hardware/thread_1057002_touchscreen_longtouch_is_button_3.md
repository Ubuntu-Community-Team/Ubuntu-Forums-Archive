---
title: "touchscreen longtouch is button 3"
date: 2009-02-01
forum: Hardware
---

### Post by Spherical on 2009-02-01
For some reason, my touchscreen is loaded with the correct touch-settings.
The most important is the longtouch action down, longtouch button 1.

Problem is, it somehow gets switched to longtouch action is click, longtouch button is 3.

This is impossible to change from xorg.conf it seems.

in the Xorg.0.log, I see the correct settings being loaded, and right away, all events are reloaded with this wrong setting.
Anyone got a clue?

Using eGalax touchscreen (according to the lsusb :P )

---

### Post by Spherical on 2009-02-01
I'm having some other issues as well.
Now, the resolution of the touchscreen is 1/10th of the screen (the screen is divided into blocks of 10 steps in the touchscreen, kinda weird)

I'll post my xorg.conf, dmesg etc. asap (having some problems in the real world to solve first)

---

### Post by Spherical on 2009-02-02
Problem solved, multiple drivers where loaded with different settings.
Got it fixed by just using my own drivers.

---

