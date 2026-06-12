---
title: "Controlling a virtual joystick with a second mouse"
date: 2016-03-16
forum: Hardware
---

### Post by Pivetta on 2016-03-16
Hi,
I have already posted this, formulated in another way on ask ubuntu, but It may not be the best place to cover a discussion and ask for hints.
I am building a giant trackball using two mice as input, one tracking the X and Y axes, the second one tracking the Z axis.

I have to tweak the input data in the OS as I made a game on Unity and there just core pointer and joystick axes are read.
Theoretically it's working, now I don't know even where to start for the software side. If it was 2012 I would do this on Windows with PPJoy and GlovePie, but since they are not supported anymore I thought moving on ubuntu as the mouse input data is simplier to read (at leas I think so).
I saw there are a lot of programs that do the opposite of what I want to do like AntiMicro, where I can control the mouse with a joystick, but I am looking for the opposite and I couldn't find anything.

What I have to do is to in a list:

-remove the second mouse from the core pointer in xinput (deactivating it is ok? or have I to do it in another way?).
-start a virtual joystick.
-send the mouse X or Y position to the virtual joystick axis.
-read the mouse and joystick data in the executable and calibrate it.

I am working on a fresh Ubuntu 15.10 installation with the Nvidia 340 drivers if this may help, the rest is just at the last official distro update.
I hope someone could give me a direction to follow. If it is too much code I may have to make my producer sad ;P

Cheers,
Pivetta

---

