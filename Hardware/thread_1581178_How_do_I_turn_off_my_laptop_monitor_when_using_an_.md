---
title: "How do I turn off my laptop monitor when using an external display?"
date: 2010-09-24
forum: Hardware
---

### Post by papillion on 2010-09-24
So I have an Acer 5100 series that works absolutely flawlessly with Ubuntu. Recently, I purchased an external monitor and keyboard and they're working fine too. But I want to turn my laptop display off when I connect my external monitor and can't find out how to do it.

I found a few places on Google that mention going to System > Preferences > Display but I notice that 'Display' isn't available on my system for some reason.  The menu jumps right from 'CompizConfig' to 'IBus Preferences'.

Can anyone help?

Thanks!
Anthony

---

### Post by IcarusR on 2010-09-24
Try the script in this thread that uses xrandr 

[http://ubuntuforums.org/showthread.php?t=1243541]("http://ubuntuforums.org/showthread.php?t=1243541")

Also see xrandr man page

```
man xrandr
```

---

### Post by efflandt on 2010-09-24
Specifics depend upon what video chip you have and may depend whether you are using default or proprietary drivers.  Different brands of video chips or drivers may have different names for video output devices.  The **xrandr** command would tell you what your video outputs are called if using default video modules.

This is one example of a script that sets a video mode not on the default list, turns off laptop display, and switches external display to the new mode.  When the laptop first boots with the external display connected, Ubuntu puts both displays into a common 1024x768 mode that it assumes both are capable of (they are) even though that is not the native resolution of either display.  A launcher on top panel or on desktop can run the script with a click or two of the mouse.

#!/bin/bash
xrandr --newmode "1920x1080_60.00"  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync
xrandr --addmode VGA1 1920x1080_60.00
xrandr --output LVDS1 --off
xrandr --output VGA1 --mode 1920x1080_60.00

Also see [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

---

### Post by pricetech on 2010-09-24
Doesn't your laptop have a hotkey for changing the display ??  It's usually tied to the "Fn" key.

---

