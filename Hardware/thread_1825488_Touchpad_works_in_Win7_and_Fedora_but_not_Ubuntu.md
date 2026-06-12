---
title: "Touchpad works in Win7 and Fedora but not Ubuntu"
date: 2011-08-15
forum: Hardware
---

### Post by NewShinyCD on 2011-08-15
I figured this would be a better forum to post in rather in Absolute Beginner.

The issue is with my touchpad on my laptop. It works perfectly fine in Windows 7 x64 and also Fedora x64, but if I boot into Ubuntu 11.04 x64 the mouse will jump around within an area the size of a quarter. This happens with holding one area down on the touchpad; also while moving the cursor it will jump around on the path that it is moving.

Even if I tune the sensitivity all the way down and the acceleration it will still jump around. I also tried installing Pointing Devices and adjusting the settings in there doesn't seem to affect it. 

The touchpad is by Synaptics. If I run xinput list in the terminal is does list the touchpad as "SynPS/2 Synaptics TouchPad".

Also when I looked at xorg.conf there was only about 8 lines of code and no section for Input Devices.

---

### Post by NewShinyCD on 2011-08-16
I tried installing Ubuntu 10.04 which fixed the touchpad issue.

Does anyone know if 11.04 is using a different driver than 10.04?

---

