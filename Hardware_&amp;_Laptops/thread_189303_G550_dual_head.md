---
title: "G550 dual head"
date: 2006-06-05
forum: Hardware &amp; Laptops
---

### Post by ddave01 on 2006-06-05
System settings > Display gave me the opportunity to configure two LCD Flat Panels in xinerama but at low resolution 640x400@60.

I can not seem to get better resolution with the default installation.

Anyone got the G550 working?

---

### Post by ddave01 on 2006-06-05
SOLVED G550 dual head

for those in need of a solution I can point you to the following link;

[http://www.tuxx-home.at/archives/2006/06/04/T14_46_29/](http://www.tuxx-home.at/archives/2006/06/04/T14_46_29/)

The HOWTO_mga_Xorg7 is very well written.  I had to make a correction to the libtool command making the ../mgaHALlib.a to mgaHALlib.a as it is in the same directory as libtool is executed.

I am very grateful for the efforts of Alexander Griesser (matrox@tuxx-home.at) and all the contributors (see HOWTO_mga) like Andrew Lunn 

Many thanks

---

### Post by metasymbol on 2006-06-15
failed...
> checking how to run the C++ preprocessor... /lib/cpp
configure: error: C++ preprocessor "/lib/cpp" fails sanity check
See `config.log' for more details.

OMG why is it so hard to have a proper g550 dualscreen support with all this debian derivats... i have a really simple setup and for example SL.10.0 is able to work with them properly after a short edit of the xorg.conf.

---

### Post by metasymbol on 2006-06-28
mkey, there was an update of this this script, now g++ dependecies are included and it solved my problem. :)

BUT: Now my primary monitor has a bigger virtual resolution then the physical and I don't know how to change it. ](*,) 

Here is a snip my xorg.conf:

```

Section "Device"
  identifier "Matrox Graphics, Inc. MGA G550 AGP"
  boardname "Matrox Millennium G550 DualHead"
  busid "PCI:1:0:0"
  driver "mga"
  screen 0
  vendorname "Matrox"
EndSection

Section "device" #         
  identifier "device1"
  boardname "Matrox Millennium G550 DualHead"
  busid "PCI:1:0:0"
  driver "mga"
  screen 1
  vendorname "Matrox"
EndSection

Section "Monitor"
  identifier "Generic Monitor"
  vendorname "Generic"
  modelname "1280x1024 @ 74 Hz"
  HorizSync 31.5-79.0
  VertRefresh 50-90
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "640x480@85" 36.0 640 696 752 832 480 481 484 509 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1024x768@43" 44.9 1024 1032 1208 1264 768 768 776 817 +hsync interlace +vsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1152x768@54" 64.995 1152 1178 1314 1472 768 771 777 806 +hsync +vsync
  modeline  "1280x854" 80.0 1280 1309 1460 1636 854 857 864 896 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  gamma 1.0
EndSection

Section "monitor" #         
  identifier "monitor1"
  vendorname "Generic"
  modelname "1280x1024 @ 74 Hz"
  HorizSync 31.5-79.0
  VertRefresh 50-90
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "640x480@85" 36.0 640 696 752 832 480 481 484 509 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1024x768@43" 44.9 1024 1032 1208 1264 768 768 776 817 +hsync interlace +vsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1152x768@54" 64.995 1152 1178 1314 1472 768 771 777 806 +hsync +vsync
  modeline  "1280x854" 80.0 1280 1309 1460 1636 854 857 864 896 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  gamma 1.0
EndSection

Section "Screen"
  Identifier "Default Screen"
  Device "Matrox Graphics, Inc. MGA G550 AGP"
  Monitor "Generic Monitor"
  DefaultDepth 24
  SubSection "Display"
    depth 24
    modes "1024x768@75" "1024x768@70" "1024x768@85" "1024x768@60" "832x624@75" "1024x768@43" "800x600@60" "1152x864@75" "800x600@85" "1152x768@54" "800x600@75" "1280x854" "800x600@72" "1280x960@60" "800x600@56" "1280x1024@60" "640x480@85" "1280x960@75" "640x480@75" "1400x1050@60" "640x480@72" "1600x1200@60" "640x480@60"
  EndSubSection
EndSection

Section "screen" #         
  identifier "screen1"
  device "device1"
  defaultdepth 24
  monitor "monitor1"
  SubSection "Display"
    depth 24
    modes "1024x768@75" "1024x768@70" "1024x768@85" "1024x768@60" "832x624@75" "1024x768@43" "800x600@60" "1152x864@75" "800x600@85" "1152x768@54" "800x600@75" "1280x854" "800x600@72" "1280x960@60" "800x600@56" "1280x1024@60" "640x480@85" "1280x960@75" "640x480@75" "1400x1050@60" "640x480@72" "1600x1200@60" "640x480@60"
  EndSubSection
EndSection

Section "ServerLayout"
  Identifier "Default Layout"
  screen 0 "Default Screen" 0 0
  screen 1 "screen1" rightof "Default Screen"
  InputDevice "Generic Keyboard"
  InputDevice "Configured Mouse"
  InputDevice "stylus" "SendCoreEvents"
  InputDevice "cursor" "SendCoreEvents"
  InputDevice "eraser" "SendCoreEvents"
EndSection

Section "DRI"
  Mode 0666
EndSection

Section "ServerFlags"
  option "Xinerama" "true"
EndSection

```

---

### Post by J_Palito on 2007-06-29
Hi everyone,

I already have read lot's of xorg.conf files, lot of other configs, tried everything and i still don't have dualhead.

I have a MGA G550 Dual Head AGP.
It works fine under Windows... But i want it to work also under Ubuntu.
I can see my 1280x800 (DVI) primary desktop, but the TV (640x480) remains black. If i plug a VGA display, it still remains black, as you can see in the picture above.
[IMG]http://www.dropshots.com/photos/318901/20070629/104432.jpg[/IMG]

This is my xorg.conf file:
```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"pt"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"0 - Matrox G550 DH"
	Driver		"mga"
	BusID		"PCI:1:0:0"
	Screen		0
	Option "DDCMode" "True"
	Option "MonitorLayout" "LVDS (TMDS), CRT"
	Option "CRT2Hsync" "30-65" #Horizontal Sync of the Monitor (check your monitor's manual for correct values)
	Option "CRT2VRefresh" "50-75" #Vertical Refresh rate of the Monitor (check your monitor's manual for correct values)	
	Option "OverlayOnCRTC2" "true"
	Option "CRT2Position" "RightOf" #Physical location of your secondary monitor in relationship to your primary monitor. Values can be: LeftOf, RightOf, Above, Below, and Clone.
	Option "MetaModes" "1280x800-640x480" #Monitor Resolutions for Primary-Secondary monitors 
	Option "MergedXineramaCRT2IsScreen0" "false" #determines which screen is going to be the primary screen; value can be "true" or "false"
EndSection

Section "Device"
	Identifier	"1 - Matrox G550 DH"
	Driver		"mga"
	BusID		"PCI:1:0:0"
	Screen		1
	Option "DDCMode" "True"
	Option "MonitorLayout" "LVDS (TMDS), CRT"
	Option "CRT2Hsync" "30-65" #Horizontal Sync of the Monitor (check your monitor's manual for correct values)
	Option "CRT2VRefresh" "50-75" #Vertical Refresh rate of the Monitor (check your monitor's manual for correct values)	
	Option "OverlayOnCRTC2" "true"
	Option "CRT2Position" "RightOf" #Physical location of your secondary monitor in relationship to your primary monitor. Values can be: LeftOf, RightOf, Above, Below, and Clone.
	Option "MetaModes" "1280x800-640x480" #Monitor Resolutions for Primary-Secondary monitors 
	Option "MergedXineramaCRT2IsScreen0" "false" #determines which screen is going to be the primary screen; value can be "true" or "false"
EndSection

Section "Monitor"
	Identifier	"Hp w19b"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-72
EndSection

Section "Monitor"
	Identifier	"TV"
	Option		"DPMS"
	Horizsync    28-64 #You may wish to change the values to fit your specific monitor
	Vertrefresh    43-60
EndSection

Section "Screen"
	Identifier	"Primary Screen"
	Device		"0 - Matrox G550 DH"
	Monitor		"Hp w19b"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"TV Screen"
	Device		"1 - Matrox G550 DH"
	Monitor		"TV"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		0	"Primary Screen"
	Screen		1	"TV Screen" RightOf "Primary Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	Option "Xinerama" "true"
EndSection

Section "DRI"
	Mode	0666
EndSection
```
So, could some one be kind enough and show me were am I mistaken?

BTW, mplayer can't also use the second display, and doesn't even play on the first.
Thanks in advance!

---

