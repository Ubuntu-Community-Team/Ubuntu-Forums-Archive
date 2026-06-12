---
title: "USB Mouse jumping around, messing up desktop"
date: 2005-05-21
forum: Hardware &amp; Laptops
---

### Post by Tolomir on 2005-05-21
Hello, I'm using a Logitech USB wheelmouse and get these messages very often:

May 21 08:46:44 localhost kernel: psmouse.c: Wheel Mouse at isa0060/serio4/input0 lost synchronization, throwing 1 bytes away.
May 21 08:46:45 localhost kernel: psmouse.c: Wheel Mouse at isa0060/serio4/input0 lost synchronization, throwing 2 bytes away.
May 21 08:46:46 localhost kernel: psmouse.c: Wheel Mouse at isa0060/serio4/input0 lost synchronization, throwing 6 bytes away.


(These entries from /var/log/messages repeat for about 20 times, after that the mouse is usable again. Is there a way to stop this jumping around, opening and closing all windows below the mousepointer at random?

I got the same problem with the touchpad mouse (I have installed ubuntu on my laptop)

Tolomir

---

### Post by Tolomir on 2005-05-21
Alrights seems like I have found a solution for the problem (by myself ;-)

The Logitech USB mouse came with an PS/2 adaptor. That I was using because on my laptop there is just 1 USB port available. Right there I plugged in my bluetooth device.

Removing bluetooth (is it supported by ubuntu anyway?) and plugging the USB connector directly into the usb port, the problem seems to be gone.

Tolomir

---

