---
title: "Xinput does in see my USB Joystick in 16.04"
date: 2017-02-16
forum: Hardware
---

### Post by mark bower on 2017-02-16
A USB 2.0 joystick which previously worked in 15.04 and was seen by "xinput", now does not work in 16.04 and is not seen by xinput command.  I used xinput to disable the Mouse/Key events which compete with the joystick.  so,

xinput - does not see joystick (WALLY PPM)
jstest-gtk	sees joystick
lsusb		sees joystick
evtest		sees joystick
cat  /proc/bus/input/devices		sees joystick

I observe that xinput sees the keyboard Microsoft Microsoft® Nano Transceiver v2.0, but does not see a flash drive in addition to the joystick

So what might be simply done to restore xinput seeing the joystick?

---

### Post by mark bower on 2017-02-18
bumped for attention

---

### Post by oldrocker99 on 2017-02-18
*Thread moved to Hardware.*

---

### Post by mark bower on 2017-02-23
As stated, in 15.04 I used xinput to help set up the function of the joystick.  But to my surprise, in 16.04 I simply went ahead and in installed Crrcsim Flight Simulator - and it worked! The controller does not show in xinput in 16.04?  But it does not need to for the simulator and joystick controller to work.

---

