---
title: "Nvidia 7950GTX screen flicker"
date: 2008-05-11
forum: Hardware
---

### Post by Tlayeh on 2008-05-11
Hello,

I'm currently running nvidia-glx-new as installed from the Restricted Drivers Manager.  It has been working perfectly, except I have been noticing a slight screen flicker every minute or two; the screen will flicker once and then be fine for a minute or sometimes longer.  It does not seem to be affected by CPU or graphics load; it occurs during intensive situations or when idling.  

Specs:
Dell XPS M1710
4GB RAM
GeForce Go 7950GTX 512MB 
1920x1200

My xorg.conf

```
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"        "/dev/psaux"
        Option          "Protocol"      "auto-dev"
        Option          "HorizEdgeScroll"       "0"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "nvidia"
        Option          "NoLogo"        "True"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        Defaultdepth    24
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
  screen "Default Screen"
        Inputdevice     "Synaptics Touchpad"
EndSection
Section "Module"
        Load            "glx"
EndSection

```

I have tested this with and without Compiz to find the same result.  I have observed, however, that the screen will flicker more frequently when running compiz, or scrolling in windows.  

Has anyone else experienced this issue or know any way to fix it?  It's starting to drive me insane...

Thanks.

---

### Post by EXCiD3 on 2008-05-11
Sometimes screen flickering is related to Vertical Sync problems. A simple checking of the Sync To VBlank options in nvidia-settings will fix this. I notice this when rendering the compiz cube mainly however i still get flickering once every hour or so which I have been unable to figure out. Hope this helps!

---

### Post by sdennie on 2008-05-11
This sometimes happens on some nvidia based laptops because of something called powermizer.  When the graphics card changes frequency, it can cause this problem.  There are two ways to fix this (both are essentially hacks):

1) [The Infamous PerfLevelSrc hack]("http://www.nvnews.net/vbulletin/showpost.php?p=1377920&postcount=9")

2) Write a script that constantly runs nvidia-settings -q all > /dev/null.  So something like:

```

#!/bin/bash

while true ; do
    nvidia-settings -q all > /dev/null
    sleep 25
done

```

---

