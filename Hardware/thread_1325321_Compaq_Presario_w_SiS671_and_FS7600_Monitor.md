---
title: "Compaq Presario w/ SiS671 and FS7600 Monitor"
date: 2009-11-13
forum: Hardware
---

### Post by Devilman13 on 2009-11-13
Hey guys. I'm trying to acheive a desktop resolution of 1024x768. Desktop effects are not needed, I'm just annoyed with 800x600.

I downloaded and installed a driver for the 671 using this guide...
[http://ubuntuforums.org/showthread.php?t=1245831](http://ubuntuforums.org/showthread.php?t=1245831) without any errors.

This is my current Xorg.conf:

```

Section "Device"
	Identifier	"Configured Video Device"
        Driver "vesa"
EndSection

Section "Monitor"
Identifier "Compaq FS7600"
Option "DPMS"
HorizSync 30-70
VertRefresh 50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

```

Note that "driver" is set to "vesa" because I'm not even sure what I should put in this field. I installed xorg-driver-sis671_0.9_i386.deb but I'm pretty sure it's not in use with this config. Horiz and Vert refresh rates are set to the specs of the Compaq FS7600 monitor. I'm not sure what Option "DPMS" even is, I got that from another example config.

I tried adding this subsection to specify the resolution, but I end up with a garbled mess at the login screen if I do, and have to go back and remove the section and reboot. I suspect this is probably due to not specifying the driver?

```

DefaultDepth 24
SubSection "Display"
             Viewport   0 0
             Virtual 1280 1024
             Modes       "1280x1024" "1024x768" "800x600" "640x480"
             Depth     24
EndSubSection

```

Can someone help me out here? I feel I'm getting very close to getting it where I want it but I just don't get something. I would just slap a video card in this POS and go on with life, but this is a PC @ work. Thanks in advance for any help.

---

### Post by Devilman13 on 2009-11-16
^Bump^

Anyone know if not specifying the "driver" as xorg-driver-sis671_0.9_i386 or something of the sort is causing the problem? Trying to avoid countless restarts.

---

### Post by Devilman13 on 2009-11-18
Ok, bit of an update.

Changing DRIVER from "vesa" to "sis" has given me more resolution options.

I now have a range of 320x240 to 960x600. Still short of 1024x768

So, I then re-added the following:

```
DefaultDepth 24
SubSection "Display"
             Viewport   0 0
             Virtual 1280 1024
             Modes       "1280x1024" "1024x768" "800x600" "640x480"
             Depth     24
EndSubSection

```

Which before with the vesa driver would give me the lines and garbled mess before I specified to use the sis driver. What's weird is though.. with the sis driver in place, and the above section added to xorg.conf, X refuses to start and gives me an error:

```

Fatal Error:
No screens found

```

](*,)    Anyone have any suggestions?

EDIT: Hrm... just noticed that when using the SiS driver instead of vesa, I get bad tearing and artifacts when scrolling through my file browser or Internet browser :|

---

### Post by Devilman13 on 2009-12-11
This is no longer an issue at all after a recent update. After the required restart, I could tell the screen res had changed due to the size of the login screen. Then in my display options, I was able to select 1024x768 :D

---

