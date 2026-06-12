---
title: "gamepad detected too many axes"
date: 2006-02-04
forum: Hardware &amp; Laptops
---

### Post by endless on 2006-02-04
I have recently bought me a gamepad for use in cedega and tuxracer. The gamepad is detected without any problem by ubuntu:


$ lsusb
Bus 001 Device 008: ID 0583:a000 Padix Co., Ltd (Rockfire)


The joystick/gamepad has two axes and eight buttons, but the linux driver seems to think it has 5 axes:

$ jstest /dev/js0
Joystick (2-Axis,8-Button ) has 5 axes and 8 buttons. Driver version is 2.1.0.


The problem is that these non-existing axes can not be calibrated by me, so they have no effect:


Axes:  0:     0      1:     0      2:     0      3:     0      4:     0 
Axes:  0: -32767  1:     0      2:     0      3:     0      4:     0 
Axes:  0: -32767  1: -32767  2:     0      3:     0      4:     0 
Axes:  0: -32767  1: -32767  2: -32767  3:     0      4:     0
Axes:  0: -32767  1: -32767  2: -32767  3: -32767  4:     0 
Axes:  0: -32767  1: -32767  2: -32767  3: -32767  4: -32767 

The 3 other axes are affected by the first two real ones in a way I don't understand yet. But the problem is that this has an effect on games I play. (for example in tuxracer after a while, I keep going to the right, or in GTA under cedega I keep spinning). Is there a way to make ubuntu detect the right number of axes or correct this some other way? Or is my gamepad just crappy?

endless

---

