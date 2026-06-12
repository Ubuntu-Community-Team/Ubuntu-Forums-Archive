---
title: "modeline problem"
date: 2009-11-03
forum: Hardware
---

### Post by deadite66 on 2009-11-03
using karmic with a pci nvidia 6200 and a 26" Panasonic lcd tv.
tried using 173 and 185 drivers.

i've googled for over a week on this and can't sort this out, i want 1360x768 i know the tv can do it as i've previously had this res on an old version of ubuntu pre hardy.

the problem is i can get 1360x768 but can't adjust it so i can see the full screen the tv controls are maxed out and xvidtune refuses to work "unable to query monitor info" error.

if anyone has any idea's i'd be happy.

last xorg.conf i've tried.
```

Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
	Subsection "Display"
                Depth       24
		Modes "1360x768"
        EndSubsection

EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver		"nvidia"
	Option		"NoLogo"		"True"
        Option          "AddARGBGLXVisuals"     "True"
        Option          "UseEDID"               "False"
        Option          "NoDDC"                 "on"
        Option          "IgnoreEDID"            "on"
        Option          "RenderAccel"           "on"
        Option          "Coolbits"              "1"
        Option          "ModeValidation" "NoEdidModes, NoMaxPClkCheck, NoVertRefreshCheck, NoHorizSyncCheck, NoEdidMaxPClkCheck, NoDFPNativeResolutionCheck" 
EndSection

Section "Monitor"
	Identifier "Generic Monitor"
	Option "DPMS"
#	Modeline "1360x768"   84.75   1360 1432 1568 1776   768 771 781 798  -hsync +vsync
#	Modeline "1360x768"   84.75   1360 1424 1560 1776   768 771 781 798  -hsync +vsync
#	Modeline "1360x768"   84.75   1360 1416 1552 1776   768 771 781 798  -hsync +vsync
#	Modeline "1360x768"   84.75   1360 1408 1544 1776   768 771 781 798  -hsync +vsync
#	Modeline "1360x768"   84.75   1360 1400 1536 1776   768 771 781 798  -hsync +vsync
#	Modeline "1360x768"   84.75   1360 1384 1520 1776   768 771 781 798  -hsync +vsync
	Modeline "1360x768"   84.75   1360 1360 1496 1776   768 771 781 798  -hsync +vsync
EndSection

```

---

