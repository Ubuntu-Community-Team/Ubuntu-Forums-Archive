---
title: "Retrolink snes gamepad not recognized"
date: 2013-04-19
forum: Hardware
---

### Post by Perados on 2013-04-19
Hellos guys,

I bought two Retrolink snes gamepads and two nes gamepads, both snes gamepads are not recognized by my laptop. I am running on Ubuntu 12.10 and already tried with joystick and jscalibtrator, the installation was not easy :P . When I do a lsusb with a snes gampead plugged, it is not recognized, but when I do it with a nes gamepad it is recognized. 
I do not know what could be the problem, because none of the snes gamepads work, I do not think the are both broken.

Thank you!

---

### Post by Grumbel on 2013-04-19
If 'lsusb' can't even detect the gamepads, then it might very well be a hardware issue. Either the pads are broken or some other USB trouble prevents them from working. If they are connected to a HUB, you could try plugging them into the computer directly, if they are already plugged into the computer, you could try plugging them into another USB port. You could also look at the output of "dmesg", when USB stuff goes wrong, that's where you tend to find some error messages. Trying the gamepads on a non-Linux machine could also provide some insight.

---

