---
title: "brightness adjustment slider appears but display not dimming/brightening"
date: 2010-10-22
forum: Hardware
---

### Post by jlsm on 2010-10-22
I have a problem with my lenovo 3000 g430 with Intel Graphics Media Accelerator 4500M. The slider appears when pressing fn+up/down, but the actual display is not dimming/brightening.

I have searched other posts and threads for a solution, but haven't found one that worked for me yet. I've tried "xrandr --output LVDS --set BACKLIGHT_CONTROL native" and it restarted Maverick, but didn't work.

xrandr -q results were


Screen 0: minimum 320 x 200, current 1280 x 800, maximum 8192 x 8192
VGA1 disconnected (normal left inverted right x axis y axis)
LVDS1 connected 1280x800+0+0 (normal left inverted right x axis y axis) 303mm x 190mm
1280x800 60.0*+
1024x768 60.0 
800x600 60.3 56.2 
640x480 59.9 
DP1 disconnected (normal left inverted right x axis y axis)

so I tried changing LVDS in the xrandr --output to LVDS1 which resulted in an error,

X Error of failed request: BadName (named color or font does not exist)
Major opcode of failed request: 150 (RANDR)
Minor opcode of failed request: 11 (RRQueryOutputProperty)
Serial number of failed request: 29
Current serial number in output stream: 29


BTW, I installed xbacklight as another post suggested, but I don't know how to use it.

Any help would be greatly appreciated.


jlsm

---

