---
title: "DisplayPort Not Working"
date: 2016-02-25
forum: Hardware
---

### Post by DanielWEWO on 2016-02-25
Hi there. I'm using a thinkpad x230 running Ubuntu 15.10. I'm attempting to connect a display via displayport, but Ubuntu doesn't seem to recognize that anything is plugged in. No extra displays pop up in settings, and xrandr --query just yields the following:

```

daniel@daniel-ThinkPad-X230:~/Homestead$ xrandr --queryScreen 0: minimum 8 x 8, current 1366 x 768, maximum 32767 x 32767
LVDS1 connected primary 1366x768+0+0 (normal left inverted right x axis y axis) 277mm x 156mm
   1366x768      60.10*+
   1360x768      59.80    59.96  
   1280x720      60.00  
   1024x768      60.00  
   1024x576      60.00  
   960x540       60.00  
   800x600       60.32    56.25  
   864x486       60.00  
   640x480       59.94  
   720x405       60.00  
   680x384       60.00  
   640x360       60.00  
DP1 disconnected (normal left inverted right x axis y axis)
DP2 disconnected (normal left inverted right x axis y axis)
DP3 disconnected (normal left inverted right x axis y axis)
HDMI1 disconnected (normal left inverted right x axis y axis)
HDMI2 disconnected (normal left inverted right x axis y axis)
HDMI3 disconnected (normal left inverted right x axis y axis)
VGA1 disconnected (normal left inverted right x axis y axis)
VIRTUAL1 disconnected (normal left inverted right x axis y axis)



```

I've tried this cable with different machines, and I've tried different cables with this machine, and different monitors. Anybody have any ideas on how to troubleshoot this? Is my port just dead? Is there anything I can do about that?

Edit: VGA works fine, it's just too blurry at 2560x1440.

---

