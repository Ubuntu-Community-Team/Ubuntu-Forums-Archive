---
title: "Trouble with Nvidia &quot;Twinview&quot; and TV-Out"
date: 2009-05-04
forum: Hardware
---

### Post by Sarai the Geek on 2009-05-04
I have a laptop with a native screen resolution of 1280x800 and a TV with a native resolution of 1024x768. Prior to yesterday I had it set up that I could switch between screens by restarting X (if the vga cord was plugged in it would go to the TV, if not it would run normally) which worked fairly well for my purposes. However, after an unfortunate incident involving a windows xp install disk and a blue screen of death, my computer got wiped. Most of my stuff was backed up, but I lost my xorg.conf. I don't remember what exactly I did to get it the way it was, and I can't find the instructions I followed.

I can get it to do what I want by going to the nvidia settings panel, enabling my tv monitor, configuring it as a "separate x screen", setting the correct resolution, and hitting apply. However, once I restart the X server I cannot get back to my tv without doing it all again. When I try to save it to the x config file it says "Failed to parse existing X config file '/etc/X11/xorg.conf'!"

Here is my current xorg.conf:
```

Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection

Section "ServerFlags"
    Option        "DontZap"    "off"
EndSection
```

---

### Post by Sarai the Geek on 2009-05-04
Well, I got it to auto-recognize what screen to use by additing this to the screen section of my xorg.conf:
```
Option         "TwinView"
    Option         "MetaModes" "1280x800,1152x864"
    Option         "SecondMonitorHorizSync" "60-85"
    Option         "SecondMonitorVertRefresh" "60-160"
    Option         "TwinViewOrientation" "Clones"
```

But when it loads, the position is automatically set to absolute so the wallpaper and any full screen apps get weirdly stretched or cut off. I tried changing the "twinvieworeintation" to "clones", as you can see, but it didn't help. Ideas?

---

