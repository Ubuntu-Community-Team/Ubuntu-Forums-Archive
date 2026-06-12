---
title: "Screen magnifies on brightness change"
date: 2008-07-18
forum: Hardware
---

### Post by and.hunt on 2008-07-18
On my Laptop (Toshiba Portege R100) I have a strange problem in that whenever the screen brightness is changed (whether manually with fn buttons, automatically through KPowerSave, or also automatically when closing the lid), the display gets magnified: The top-left quarter of the desktop is shown on the display. To restore a normal display you either have to change modes in xorg (i.e. out of the current mode, and then back into the wanted mode with "Ctrl"-"Alt"-"+ or -"), or change to a different virtual terminal and back.

I have tried modifying the xorg.conf as to have only the wanted mode available: In this case the problem still occurs, to get rid of it you then have to change vt's, since you cannot change modes.

Does anyone know what could be causing the problem or how it can be fixed?

Here is my xorg.conf, in case it could be causing problems: (The laptop's display wasn't recognised automatically at installation time, I had to set up the correct resolution with xfailsafedialog.)
```
Section "Device"
	Identifier	"Configured Video Device"
EndSection
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
EndSection
Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "screen1" 0 0
EndSection
Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection
Section "device" #  
	Identifier	"device1"
	Boardname	"Trident CyberBlade (generic)"
	Busid		"PCI:1:0:0"
	Driver		"trident"
	Screen	0
	Vendorname	"Trident"
EndSection
Section "screen" #  
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
	SubSection "Display"
		Depth	24
		Virtual	1024	768
		Modes		"1024x768@60"	"800x600@60"	"800x600@56"	"640x480@60"
	EndSubSection
EndSection
Section "monitor" #  
	Identifier	"monitor1"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1024x768"
	Horizsync	31.5-48.0
	Vertrefresh	56.0 - 65.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection
Section "device" # 
	Identifier	"device2"
	Boardname	"Trident CyberBlade (generic)"
	Busid		"PCI:1:0:0"
	Driver		"trident"
	Screen	1
	Vendorname	"Trident"
EndSection
Section "screen" # 
	Identifier	"screen2"
	Device		"device2"
	Defaultdepth	24
	Monitor		"monitor2"
EndSection
Section "monitor" # 
	Identifier	"monitor2"
	Gamma	1.0
EndSection

```

// Edit:
I switched on the option "CyberStretch" in the section for the graphics card: Now, instead of the screen magnifying, the display gets corrupted. (CyberStretch interpolates smaller screen resolutions to fill the screen, which it does fine.) The display can be fixed again in the same way as usual.

---

