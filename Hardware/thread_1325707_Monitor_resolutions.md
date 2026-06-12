---
title: "Monitor resolutions"
date: 2009-11-13
forum: Hardware
---

### Post by cfoley on 2009-11-13
Earlier today I installed Ubuntu 9.10 on my Advent netbook. I went for the desktop version, not the netbook remix. Everything seems to be working fine except the screen resolutions.

The built in monitor:
stuck at: 800x600
should be: 1024x600

Second monitor:
stuck at: 1024x786
should be 1920x1085

I tried the advice on the wiki but when I added and selected new modes using xrandr they did not display properly. I also tried searching google but to no avail.

Any advice would be most appreciated! :)

---

### Post by cfoley on 2009-11-13
If you will excuse the double post I can add some more information. At the moment I am concentrating on the external monitor so I have set that to the only display. This is the typical terminal session I have been trying:

```
chris@chris-laptop:~$ xrandr
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 4096 x 4096
VGA1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 443mm x 249mm
   1024x768       70.1     60.0* 
   800x600        60.3     56.2  
   640x480        66.7     60.0  
   720x400        70.1  
LVDS1 connected (normal left inverted right x axis y axis)
   1024x600       60.0 +
   640x480        59.9  
chris@chris-laptop:~$ cvt 1920 1080
# 1920x1080 59.96 Hz (CVT 2.07M9) hsync: 67.16 kHz; pclk: 173.00 MHz
Modeline "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
chris@chris-laptop:~$ xrandr --newmode "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
chris@chris-laptop:~$ xrandr --addmode VGA1 1920x1080_60.00

```

If I try and execute this last command the screen resolution does appear to change to the correct dimensions but only one vertical column of the desktop appears at the left hand side of the screen. The rest is black except for the mouse pointer which I can move around as normal.

---

### Post by cfoley on 2009-11-14
I have found a workaround, thanks.

---

