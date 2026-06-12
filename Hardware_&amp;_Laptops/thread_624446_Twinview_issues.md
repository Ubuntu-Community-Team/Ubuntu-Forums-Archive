---
title: "Twinview issues"
date: 2007-11-27
forum: Hardware &amp; Laptops
---

### Post by IndroAppt on 2007-11-27
I see alot of others with similar probs and I have followed the howtos for setting up twinview without success. Ultimately, I really want the tvout to work via svideo but have had no luck. I've attempted to work backwards and get twinview to run an external flat panel first and had no luck with this either.

The log file indicates that the card is detecting the external flat panel monitor ok and is in fact making it monitor 0 while making the internal flat panel monitor 1. The external monitor is receiving no signal though. 

I'm running
Ubuntu Gutsy
Tecra M2
Geforce FX Go5200

Xorg.conf
```
Section "Device"
	Identifier	"nVidia Corporation NV34M [GeForce FX Go5200 32M/64M]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo" 		"off"
	Option		"TwinView" 		"on"
	Option		"MetaModes" 		"1024x768,1024x768"
#	Option		"MetaModes" 		"1024x768,640x480; 1024x768,NULL; 800x600,NULL; 640x480,NULL"
#	Option		"UseEDIDFreqs"		"On"
#	Option		"SecondMonitorHorizSync" "30-50"
#	Option		"SecondMonitorVertRefresh" "60"
	Option		"TwinViewOrientation" 	"Clone"
#	Option		"ConnectedMonitor" 	"CRT-0,DFP-0"
#	Option		"ConnectedMonitor" 	"DFP-0,TV"
#	Option		"TVOutFormat" 		"COMPOSITE"
#	Option		"TVStandard" 		"PAL-B"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	28-51
	Vertrefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV34M [GeForce FX Go5200 32M/64M]"
	Monitor		"Generic Monitor"
	Defaultdepth	24	
	SubSection "Display"
		Modes		"1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  	Screen 		"Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
EndSection
```

xorg.0.log
```
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "off"
(**) NVIDIA(0): Option "TwinView" "on"
(**) NVIDIA(0): Option "TwinViewOrientation" "Clone"
(**) NVIDIA(0): Option "MetaModes" "1024x768,1024x768"
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(**) NVIDIA(0): TwinView enabled
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce FX Go5200 32M/64M (NV34) at PCI:1:0:0
(II) NVIDIA(0):     (GPU-0)
(--) NVIDIA(0): Memory: 65536 kBytes
(--) NVIDIA(0): VideoBIOS: 04.34.20.63.a3
(II) NVIDIA(0): Detected AGP rate: 4X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce FX Go5200 32M/64M at
(--) NVIDIA(0):     PCI:1:0:0:
(--) NVIDIA(0):     Proview HD-772 (CRT-0)
(--) NVIDIA(0):     TOSHIBA Internal Panel (DFP-0)
(--) NVIDIA(0): Proview HD-772 (CRT-0): 350.0 MHz maximum pixel clock
(--) NVIDIA(0): TOSHIBA Internal Panel (DFP-0): 270.0 MHz maximum pixel clock
(--) NVIDIA(0): TOSHIBA Internal Panel (DFP-0): Internal Dual Link LVDS
(II) NVIDIA(0): Assigned Display Devices: CRT-0, DFP-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1024x768,1024x768"
(II) NVIDIA(0): Virtual screen size determined to be 1024 x 768
(--) NVIDIA(0): DPI set to (76, 72); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(**) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
```

Overall, I am so impressed with gutsy (been at it for 3 days now) but without tvout support I'm really going to have to revert to micros%*t...

Help, please?

---

