---
title: "toshiba dynabook satellite 2590x"
date: 2005-04-10
forum: Hardware &amp; Laptops
---

### Post by pugrit on 2005-04-10
Greets.

i want to install ubuntu on my toshiba dynabook satellite 2590x but their are some problems, th ecd wont detect on start up.

i tried booting it up using a bootdisk and still the same, no boot.

i want to set the bios but it seems thiers no way to access bios from fresf bootup, tried pressing the usuall keys to access bios, del and f2 and nothing. it automatically turns on to windows..

any ideas? it seems that this kind of latop was specifcally designed/made for a windows OS.

anyways, thanks. any suggestions, ideas will surely help a lot.

---

### Post by lgb on 2005-04-10
Try pressing the esc key at boot, then F1. Toshiba also has a hardware configuration utility in the control panel.

---

### Post by pugrit on 2005-04-13
thanks.

---

### Post by jimonade on 2008-07-10
i have hardy installed on a "dynabook satellite 2590x", and i cant get the video card working correctly in xorg.  

it's a " VGA compatible controller: Trident Microsystems Cyber 9525 (rev 49) (pro
g-if 00 [VGA controller])"

i cant get it to do above 800x600, and the screen wont expand to the edges.  there is a 2 inch border all around.

i tried the xorg.conf <Option  "CyberStretch"  "true"> feature of the driver, but that didnt work either.  the left 2/3 of the screen was looking good, but the right 1/3 was just black.

if you have a good xorg.conf, solution, or idea please share.

thanks,

-jimonade

---

### Post by jimonade on 2008-07-10
#
# and here it is!
# full screen 1024x768
#

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
  screen 0 "screen1" 0 0
EndSection
Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection
Section "device" # 
	Identifier	"device1"
	Boardname	"Trident Cyber 9525 (generic)"
	Busid		"PCI:1:0:0"
	Driver		"trident"
	Screen	0
	Vendorname	"Trident"
#       Option  "CyberShadow"   "false"
#        Option  "CyberStretch"  "true"
#       Option  "Display"       "LCD"
EndSection
Section "screen" # 
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	16
	Monitor		"monitor1"
	SubSection "Display"
		Depth	16
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

---

