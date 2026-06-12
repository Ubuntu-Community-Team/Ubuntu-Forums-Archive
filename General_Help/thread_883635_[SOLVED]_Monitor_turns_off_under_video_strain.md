---
title: "[SOLVED] Monitor turns off under video strain"
date: 2008-08-08
forum: General Help
---

### Post by sama_j on 2008-08-08
My monitor turns off.
Light goes from green to orange and waiting does nothing. This happens when I am playing a game, not only full-screen, also happened when i was looking at screen-savers. 

The keyboard lights are unresponsive. The only option I see is a reset.

:confused::confused:

---

### Post by ajgreeny on 2008-08-08
Is this just in ubuntu or does it happen in other OSs, if you have any others?  Sounds as if the graphics card is simply not outputting to the monitor sufficiently strongly , so I would suspect the card is weak, or something along those lines.

---

### Post by sama_j on 2008-08-08
I never had the problem in XP. The card is a Nvidia GeForce 6600gt. I haven't had a single problem with it before. I don't know what else to post to help clear this up. Maybe i just have to put up with it.  :(

---

### Post by jocko on 2008-08-08
One thing that may cause that is if your graphics card tries to use a resolution/refresh rate combination that your monitor can't handle.
That will send some monitors to powersaving mode, while others will give an "out of sync" message.

One way to fix it, if that's the problem, is to add the correct sync ranges to your /etc/X11/xorg.conf. You may find them in your monitor's manual or on the manufacturers webpage.

```
gksudo gedit /etc/X11/xorg.conf
```Find the monitor section and add the correct "HorizSync" and "VertRefresh" values for your monitor.
This is mine, as a reference:
```
Section "Monitor"
    Identifier    "Samsung SyncMaster 2032BW"
    Option        "DPMS"
    [COLOR=Blue]HorizSync     30-81
    VertRefresh   56-75[/COLOR]
EndSection
```Don't change anything else in xorg.conf than adding those two lines (and make sure you get the correct values for your monitor), then restart Xorg (Ctrl+Alt+Backspace).

---

### Post by sama_j on 2008-08-08
My xorg looks like this. I ran gksudo displayconfig-gtk nad selected my monitor again. I now have no desktop effects .:(. I don't know what i've done but the thing isn't happy. Thanks for helping.


>  
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Option		"AddARGBGLXVisuals"	"True"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1280	960
		Modes		"1024x768@60"	"1280x960@60"	"1024x768@70"	"1024x768@75"	"832x624@75"	"800x600@60"	"800x600@75"	"800x600@72"	"800x600@56"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"NVIDIA GeForce 6 Series"
	Busid		"PCI:1:0:0"
	Driver		"nv"
	Screen	0
	Vendorname	"NVIDIA"
EndSection

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
	Option		"CorePointer"
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

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Generic CRT Display"
	Modelname	"Monitor 1024x768"
	Horizsync	31.5-61.0
	Vertrefresh	50-75
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
	Gamma	1.0
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection

Section "device" #   
	Identifier	"device1"
	Boardname	"NVIDIA GeForce 6 Series"
	Busid		"PCI:1:0:0"
	Driver		"nv"
	Screen	1
	Vendorname	"NVIDIA"
EndSection
Section "screen" #   
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
	SubSection "Display"
		Depth	24
		Modes		"640x480@60"
	EndSubSection
EndSection
Section "monitor" #   
	Identifier	"monitor1"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection

---

### Post by jocko on 2008-08-08
Hmmm... that looks like a mess.
First you have two device sections, both set to use the wrong driver (you need to use the "nvidia" driver to get 3d working, "nv" will only give 2d).

Could you start over with a fresh xorg.conf?
```
sudo dpkg-reconfigure xserver-xorg
```In hardy that will give you an almost empty xorg.conf, as most things are supposed to be automatically detected by xorg.

Then put some of the options back:
In the Screen section, add ```
Option        "AddARGBGLXVisuals"    "True"
```.
In the Device section, add ```
Driver        "nvidia"
```And in the monitor section, add
```
Horizsync    31.5-61.0
Vertrefresh    50-75
```
That *should* give you a working xorg again, with 3d acceleration and proper handling of the monitor refresh rates.
Any other options you need to add (second monitor, tv-out, ...) can be done through nvidia-settings or by editing xorg.conf manually after backing it up.
My experience with displayconfig-gtk is that it almost always cause more problems than it solves.

---

### Post by ajgreeny on 2008-08-08
Have you actually installed the proprietary nvidia driver for your card or are you still only running the open source driver that the installation gave you?  If the latter, you should try to get the nvidia driver running.

---

### Post by sama_j on 2008-08-10
**Thanks everyone.** I followed the instructions and ended up with four screens trying to cram themselves onto the one monitor. I will chalk this up to a learning experience and not be too agitated. By the way I really am thankful for the help, not being sarcastic! I reinstalled Ubuntu and bought an external HDD for safekeeping of documents. Thanks again. :guitar: You guys rock !!!

---

