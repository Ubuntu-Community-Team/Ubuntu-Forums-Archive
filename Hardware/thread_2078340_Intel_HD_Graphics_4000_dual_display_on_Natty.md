---
title: "Intel HD Graphics 4000 dual display on Natty"
date: 2012-10-30
forum: Hardware
---

### Post by bissong on 2012-10-30
Hi,

I am using Ubuntu 11.04 64-bit with a kernel 3.4.0 on my Dell N5520 laptop.

This latter has only one graphics chipset which is the Intel HD4000 (integrated in the Core i5-3210M).

Everything works fine except for the dual display (and Unity but I couldnt care less). The laptop has a VGA and HDMI output. On each of these outputs the result is the same, I get only a clone of what is on the main screen. I would like to have one extended desktop but the monitors are not recognized.

I tried following these steps:
[http://askubuntu.com/questions/195812/2-external-displays-on-thinkpad-t430s-with-hd4000-graphics](http://askubuntu.com/questions/195812/2-external-displays-on-thinkpad-t430s-with-hd4000-graphics)
[http://ubuntuforums.org/showthread.php?t=2032530](http://ubuntuforums.org/showthread.php?t=2032530)

But in my case none of the above solution applies as my monitors are not recognized. Even my main screen is set to unknown in the System > Preferences > Monitors application.

The output of xrandr command is the following no matter if a second monitor is connected or not:
```
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 1366 x 768, current 1366 x 768, maximum 1366 x 768
default connected 1366x768+0+0 0mm x 0mm
   1366x768        0.0*
```

I do not know why even my main display is not recognized properly... But my main concern is that VGA or HDMI never shows up even though some clone display is applied to them.

Right now I'm stuck and do know what else to try. I don't know if a solution exists for my version Ubuntu but I can't upgrade to 12.xx. Any advice is welcome ;-)

Thanks

---

