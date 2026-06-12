---
title: "Reconfiguring a new monitor (widescreen)"
date: 2008-07-17
forum: General Help
---

### Post by Dark Aspect on 2008-07-17
How do I make Ubuntu 8.04 detect a new LCD monitor? The maximum resolution of my old LCD is 1280x1024 but I am trying to set it higher for a newer wide screen LCD (preferably something like 1920x1200) but I can't seem to set the new maximum resolution limit.I have tried Nvidia X server settings and the default screen resolution application under preferences.However the "detect displays" button doesn't seem to do anything.

Any other ideas?

---

### Post by Dark Aspect on 2008-07-17
Bump,threads get buried quick on these forums.Anyway here is my xorg.conf

> # xorg.conf (X.Org X Window System server configuration file)
#
# This file was created by hand and is prefect,don't **** with it
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
        Option          "CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"NVIDIA GeForce 6800 (generic)"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Option		"NoLogo"	"Flase"
	Screen	0
	Vendorname	"NVIDIA"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1280x1024"
	Horizsync	31.5-64.0
	Vertrefresh	56.0 - 65.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1280	1024
		Modes		"1280x1024@60"	"1280x960@60"	"1024x768@60"	"800x600@60"	"800x600@56"	"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
EndSection

Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"NVIDIA GeForce 6800 (generic)"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Option		"NoLogo"	"Flase"
	Screen	1
	Vendorname	"NVIDIA"
EndSection

Section "screen" # 
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
EndSection

Section "monitor" # 
	Identifier	"monitor1"
	Gamma	1.0
EndSection

Section "ServerFlags"
EndSection

and it seems the native resolution is 1680x1050 (Not 1920x1200) though I am still stuck in 1280x1028.

---

### Post by bodhi.zazen on 2008-07-17
It appears you are using a nvidia card.

Try :

```
gksu nvidia-settings
```

Be sure to save your settings.

It necessary install it:

```
sudo apt-get install nvidia-settigns
```

---

