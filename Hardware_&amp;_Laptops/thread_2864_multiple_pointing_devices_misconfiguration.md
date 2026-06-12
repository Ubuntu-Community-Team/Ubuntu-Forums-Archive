---
title: "multiple pointing devices misconfiguration"
date: 2004-11-01
forum: Hardware &amp; Laptops
---

### Post by kastorff on 2004-11-01
Apparently, Ubuntu thinks my IBM Thinkpad T23 has both a Trackpoint and a Synaptics Touchpad. When the desktop loads, I get the normal mouse cursor, and the X default cursor overlaid on the display (for the touchpad that doesn't exist). It will eventually go away, but I'd like to resolve the problem. I tried commenting out the lines referencing the device in XF86Config-4, but it still appears. I'm trying to stay away from a complete reconfiguration of X if possible.

Anyone else seen this? Ideas? Thanks...

---

### Post by bsherman on 2004-11-01
I also have an IBM Thinkpad T23.

The extra "X" cursor you describe is not a side effect of having two mouse devices defined. 

Rather, this is an issue with the S3 SuperSavage IX/C driver in X. You need to add an option to the "Device" section of your "/etc/X11/XF86Config-4" file. Edit it using nano, vi, or gedit, whichever you like.

You'll want to add this line:
```
Option          "SWCursor"
```

The end result should be something like this:
```

Section "Device"
        Identifier      "S3 Inc. SuperSavage IX/C SDR"
        Driver          "savage"
        BusID           "PCI:1:0:0"
        Option          "SWCursor"
EndSection

```

Please backup your XF86Config-4 before making the change, and you'll have to restart GDM or X in general to see the effect.
```
sudo /etc/init.d/gdm restart
```

---

### Post by kastorff on 2004-11-03
Thanks...that was precisely what I needed.

---

