---
title: "enlarge screen size with xrandr"
date: 2009-11-04
forum: Hardware
---

### Post by josvanr on 2009-11-04
hello

I'm trying out xrandr to create a larger (virtual) screen size
on my 1280x800 laptop screen. For instance:

xrandr --output LVDS1 --mode 1280x800 --scale 1.3x1.3

should give me a screen that is 1.3 times as large as the 
physical screen.

Now I tried this from within the kde window manager (I'm 
using kubuntu 9.10), and the screen seems to scale up all right,
but the size of the desktop stays small. Ie: windows are only 
displayed on a 1280x800 portion of the screen. The mouse however
moves across the entire screen. Also, the windows don't redraw
correctly and leave a trail when I move them around the screen.
 In XFCE4 it does work correctly. 
Is there some way to make it work for kde?

josvanr

---

