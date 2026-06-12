---
title: "Docking Stations &amp; gnome-display-properties"
date: 2010-10-08
forum: Hardware
---

### Post by gdi2k on 2010-10-08
I use a [docking station]("http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-70299") for my laptop which is connected to 2 external monitors. However, each time I place my laptop on it, I have to manually reconfigure the display settings using gnome-display-properties to be able to use the external monitors. 

Has anyone found a way to either: 
[LIST]
[*]Save display "profiles" such that I can just select an option from a dropdown to load the correct settings (Lenovo's ThinkWhatever Utilities for Windows offer this).
[*]Automatically detect when my external monitors are present and load the correct settings automatically.
[/LIST]

It's an annoying issue that I've had ever since XRandr has been used by gnome-display-properties.

---

### Post by P4man on 2010-10-08
Which videocard do you have? Maybe this will help if you use an nvidia card:
[http://willem.engen.nl/projects/disper/](http://willem.engen.nl/projects/disper/)

And this is based on it:

[http://ubuntuforums.org/showthread.php?t=1515267](http://ubuntuforums.org/showthread.php?t=1515267)

---

### Post by gdi2k on 2010-10-08
Thanks P4, I checked it out, but as you say it focuses on Nvidia cards, and I have an Intel IGP (Integrated Intel® X4500 HD according to the datasheet). 

I've since tried arandr, and although it looks like what I want (you can save configs and load them with hotkeys), actually loading the saved configuration sprouts errors and doesn't work. 

I think creating a script to configure the xrandr manually may be the way forward. I'll report back if I have success.

---

### Post by gdi2k on 2010-10-09
Ok, I've had some success with manually creating a xrandr script, so I just have to click an icon on my taskbar to set the resolutions properly. 

For reference, mine looks like this: 
```
#!/bin/sh
xrandr --output LVDS1 --off
xrandr --output VGA1 --mode 1920x1080 --pos 0x0 --output HDMI2 --mode 1280x1024 --pos 1920x0
```

Where LVDS1 is my laptop's monitor, VGA is the VGA output and (oddly) HDMI2 is the dock's DisplayPort output. 

I run two xrandr commands because I get "xrandr: cannot find crtc for output HDMI2" if I don't first switch off the LVDS1 output.

---

