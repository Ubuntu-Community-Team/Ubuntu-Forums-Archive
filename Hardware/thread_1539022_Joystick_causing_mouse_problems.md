---
title: "Joystick causing mouse problems"
date: 2010-07-26
forum: Hardware
---

### Post by CPO on 2010-07-26
I have an issue with a possible interaction between my joystick and the mouse.  When a joystick is plugged into a usb port it causes the mouse cursor to drift up to the upper left corner of the screen.  This problem was intermittent at first but now occurs every time the computer is booted up.  I am using 10.04 and this computer is, or will be used to run x-plane 9 so a joystick or yoke device is critical.  I have had no other issues with this installation.  The computer is a Dell Dimension 4700 with 2GB ram and a GeForce 8400GS video card.

---

### Post by oshunluvr on 2010-07-31
Try removing /usr/lib/X11/xorg.conf.d/10-joystick.conf

---

### Post by CPO on 2010-08-14
Tried that, same thing as before.  As soon as I run jscal to calibrate the joystick the same thing happens.

---

