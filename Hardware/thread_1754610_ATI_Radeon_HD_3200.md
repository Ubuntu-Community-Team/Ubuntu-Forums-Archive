---
title: "ATI Radeon HD 3200"
date: 2011-05-10
forum: Hardware
---

### Post by hamiltoncolares on 2011-05-10
Hi friends,

  I'm experiecning some problems with my notebook on a natty fresh install. My video card performance is very with bad with the proprietary driver. The card is an ATI HD 3200 and the notebook is an HP Dv5.
  I have been searching in many foruns on the web but didn't find a solution for the problem. The graphics are slow an sometimes they crash. If I don't install the drivers the performance seems to be better (even it's not good at all), but the crashes remains.
  Hope someone can realy help me. I'm very frustrated because on Ubuntu 10.10 it used to work fine, but if reinstall it now, it's no good too. There goes some outputs commands I hope could help. 

fglrxinfo
```
display: :0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 3200 Graphics 
OpenGL version string: 3.3.10750 Compatibility Profile Context

```

fgl_gears
```
Using GLX_SGIX_pbuffer
996 frames in 5.0 seconds = 199.200 FPS
1223 frames in 5.0 seconds = 244.600 FPS
1279 frames in 5.0 seconds = 255.800 FPS
1288 frames in 5.0 seconds = 257.600 FPS
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0"
      after 23168 requests (23168 known processed) with 0 events remaining.

```

xorg.conf
```
Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	Option	    "UseFastTLS" "1"
	BusID       "PCI:1:5:0"
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

[]'s
Hamilton

---

### Post by hamiltoncolares on 2011-05-10
Anybody people? [-o<

---

### Post by Johnny Buffalkill on 2011-06-13
I have the same GPU, and I couldn't get fglrx working right in Natty either.  I wiped it and then installed Maverick (this is not my primary installation).  When I used the proprietary drivers from System/Administrative/Hardware Drivers it didn't work but when I downloaded the 11.5 drivers from AMD and installed it that way it worked fairly well.  I say fairly well because I still have better 2d graphics (i.e. DVD, Blu-ray, HDTV playback) with the open source drivers.

I didn't do very good science with my experiments because I changed too many variables at once.  I never tried manually downloading the AMD drivers with Natty.  It was an afterthought.  You might try that.  If that doesn't work you could try the same in maverick.  I installed it by double clicking it and selecting "run in terminal".  I didn't use the command line method.

Sorry I don't have a more specific answer, but I see its been four weeks and there haven't been any replies, so maybe my meager information is all there is.

---

