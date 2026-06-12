---
title: "Re-calibrating Pen/Touchscreen"
date: 2023-02-23
forum: Hardware
---

### Post by brinston on 2023-02-23
I am looking for a way to either re-calibrate or debug pen/touchscreen issues under Ubuntu 22.04 LTS on a Microsoft Surface Pro 3 running a custom kernel (courtesy of the surface-linux folks over on github).

I'd had 0 issues with the pen and touchscreen up until the other day when I have no idea what caused the pen to go way out of calibration (I have tried two sets of new batteries). 
The surface seems to think that the pen is touching the screen ~7cm down and to the right of where it is actually touching the screen (makes it unusable for notes) - this behaviour is very easily diagnosed just opening Xournal++ and trying to write. However, touch input with my fingers seems to register in the correct spots as I am able to navigate the file manager by touch but not by pen.

I have run ```
evtest
``` and ```
libinput
``` to determine that the surface is in fact receiving input from the pen. 
Oddly running ```
libinput debug-tablet
``` for a x-y readout of where the pen is touching does seem roughly correct with the caveat that I'm not sure what the x-y ABS and otherwise are displaying in. It's just raw numbers but if I track up to the upper left corner bot x and y to approach 0 before the pen runs off the edge of the screen so that seems right.

I'm having trouble narrowing down at what level things are getting confused or even what is actually responsible for handling the touchscreen input (there is a wacom tablet driver baked into Ubuntu's setting but running it's re-calibration doesn't fix the issue but oddly I can hit the calibration targets precisely with the pen).

Edit: Well switching to Xorg "fixed" the problem. I still have no idea what caused Wayland to go sideways as to the best of my knowledge that is what I had been running since I installed 22.04 on the device.

---

