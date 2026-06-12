---
title: "tc1100 stylus maverick"
date: 2010-12-20
forum: Hardware
---

### Post by redbook4574 on 2010-12-20
Help, upgraded from lucid to maverick on my hp tc1100 tablet, all works great but i cannot get the stylus to rotate with screen rotation, it stubbornly refuses to change orientation

OK sorted. Needed some changes to the rotate file

For those interested, this works fine.


#!/bin/sh
if [ -n "$(xrandr | grep 768x1024)" ]; then
xrandr -o normal && xsetwacom set "Serial Wacom Tablet stylus" Rotate NONE && xsetwacom set "Serial Wacom Tablet eraser" Rotate NONE
else
xrandr -o left && xsetwacom set "Serial Wacom Tablet stylus" Rotate CCW && xsetwacom set "Serial Wacom Tablet eraser" Rotate CCW
fi

---

### Post by reyescjr on 2012-04-21
This Script works great in 12.04 as well! ubuntu rocks on tc1100 and so far 12.04 works great just add the script here and you have it all no problems so far! :guitar:

---

