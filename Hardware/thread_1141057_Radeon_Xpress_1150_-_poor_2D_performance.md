---
title: "Radeon Xpress 1150 - poor 2D performance"
date: 2009-04-28
forum: Hardware
---

### Post by Bobber76 on 2009-04-28
Hi there!

I'm using Ubuntu since 8.10, but i have a big problem with my ATI Xpress 1150 VGA. The 3D performance is acceptable, but in 2D, it's crappy. When I move a windows, this looks like the attachment. I have upgraded to Jaunty, but some days after, i had to downgrade back to Intrepid, because the Xpress 1150 is absolutely useless in Jaunty (lack of good 3d support)
The situation is again the same. Good 3D, bad 2D. I have tried 9.2 and 9.3 fglrx too... Can someone help?

Here is my xorg.conf:

```

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "Configured Video Device"
	Option	    "UseFBDev" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:5:0"
	Option 	"AccelMethod" "EXA"
Option "MigrationHeuristic" "greedy"
 Option "AccelDFS" "true"
 Option "EnablePageFlip" "true"
 Option "EnableDepthMoves" "true"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

---

