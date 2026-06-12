---
title: "USB Joystick not seen by XINPUT LIST"
date: 2017-02-14
forum: Hardware
---

### Post by mark bower on 2017-02-14
A USB joystick which previously worked in 15.04 and was seen by "xinput", now does not work and is not seen by xinput in 16.04.  I used xinput to disable the Mouse/Key events which compete with the joystick.  so,

xinput list -      does not see joystick (WALLY PPM)
jstest-gtk -	sees joystick
lsusb -	sees joystick
evtest -	sees joystick
cat  /proc/bus/input/devices - sees joystick

I observe that:  1) the keyboard Microsoft Microsoft® Nano Transceiver v2.0 and 2) SanDisk USB thumb drive are both detected by XINPUT.

So what might be simply done to restore xinput seeing the joystick?

Note:  Having trouble getting responses, I have posted both on Gaming and Hardware.

---

### Post by mark bower on 2017-02-18
bumped for attention

---

### Post by howefield on 2017-02-18
And closed.

---

