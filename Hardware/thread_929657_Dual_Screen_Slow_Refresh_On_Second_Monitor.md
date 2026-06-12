---
title: "Dual Screen: Slow Refresh On Second Monitor"
date: 2008-09-25
forum: Hardware
---

### Post by give.away on 2008-09-25
Hello,

ATI Radeon 2600 HD (Mobile), fglrx , XCFE, Xinerama, internal monitor resolution 1440x900, external (DVI) monitor resolution 1280x1024.

Expected behavior, but on external monitor refresh rate seems to low, i. e. when I move a window the motion is not smooth and a copy of the window seems to trail it like a shadow.

On internal monitor this is not the case.

My xorg.conf:
```

Section "ServerLayout"
	Identifier     "Dual Screen Layout"
	Screen         "Internal Screen" 0 0
	Screen         "External Screen" RightOf "Internal Screen"
	InputDevice    "Synaptics Touchpad"
	Option	       "Xinerama" "true"
	Option	       "AIGLX" "true"
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

# input devices here

Section "Monitor"
	Identifier   "Internal Monitor"
	Option	     "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "External Monitor"
	HorizSync    30.0 - 83.0
	VertRefresh  56.0 - 75.0
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "Radeon2600HDM0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "Radeon2600HDM1"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "Internal Screen"
	Device     "Radeon2600HDM0"
	Monitor    "Internal Monitor"
	DefaultDepth     24
EndSection

Section "Screen"
	Identifier "External Screen"
	Device     "Radeon2600HDM1"
	Monitor    "External Monitor"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

Thanks in advance,
GA

---

### Post by give.away on 2008-09-26
Hello,

I worked around the problem, because Xinerama is not the right mode. For ati-cards I recommend BigDesktop, which does nearly the same.

I understood that Xinerama supports no acceleration on the second monitor, therefore the bad performance. BigDesktop supports 3D-acceleration. The only drawback is, that the "vertical resolution" has to be the same on each monitor.

Thanks anyway,
GA

---

