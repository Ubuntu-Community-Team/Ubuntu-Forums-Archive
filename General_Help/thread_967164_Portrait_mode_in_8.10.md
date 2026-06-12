---
title: "Portrait mode in 8.10"
date: 2008-11-01
forum: General Help
---

### Post by nsivin on 2008-11-01
I have just upgraded from Ubuntu 8.04 to 8.10. I am using an NVIDIA GeForce 6200 TurboCache graphics card (three years old) on a desktop with an AMD 4200+ 64-bit CPU and a Samsung Syncmaster 960B LCD monitor, which I always operate in portrait mode. In Hardy, after activating the proprietary NVIDIA driver, I had no problem with maximum resolution. 

But I still had to get the monitor to rotate into portrait mode. To do this, in v. 8.04, I would edit /etc/X11/xorg.conf, adding to the “Device” section the line
	Option	“RandRRotation” “on” 

I would then go to the System, Preferences, Screen Resolution dialog set Rotation to Left, and check box to set the default. 
In Intrepid, however, when I reboot I get a message to the effect that it can’t parse the Rand RRotation line. I could only get the session going in low graphics mode, so I had to remove the new line. But without that addition to xorg.conf, the Screen Resolution dialog offers no choice of display orientation.

Does someone know how it works in v. 8.10?

---

### Post by Johannes Eva on 2011-01-12
You have to put RandRRotation in the Screen section:
```

Section "Screen"
    Identifier   "Screen0"
    Device       "Device0"
    Monitor      "Monitor0"
    DefaultDepth 24
    Option       "TwinView" "0"
    Option       "metamodes" "CRT: nvidia-auto-select +0+0"
    Option       "RandRRotation" "True"
    SubSection "Display"
        Depth 24
    EndSubSection
EndSection
```

More information on rotation / pivot with NVIDIA gfx and Ubuntu:

_**[Ubuntu & NVIDIA: external monitor, rotation, ...]("http://www.johannes-eva.net/ubuntu-linux-external-monitor-nvidia-rotate")**_

---

