---
title: "Intrepid Xorg problems"
date: 2008-12-17
forum: Installation &amp; Upgrades
---

### Post by amohanty on 2008-12-17
Hi All.

I recently updated my system to intrepid and ran into some expected and some unexpected problems. A bit about the system:

1. Lenovo T-61 with Intel core-2 duo and gma964 integrated video.
2. Two external monitors attached via docking station.

Also I don't do the usual desktop setup, but install a CLI system using the alternate CD and setup SLiM and openbox with some other stuff.

The great thing was X started up fine with no hiccups, unfortunately for the dual external monitors to work I have to slip in a Virtual line in x.org which means a device and a monitor (minimal) entries also made it in. That done xrandr does a great job and I get 3840x1200 no problems.

Now for the issues:

1. My marble mouse is (obviously) not configured properly. I have used a custom InputDevice section in the past and tried to do so. Per Xorg.0.log, the setting is picked up and applied by X and then promptly **overriden** by what it picks up via evdev!! And no matter what I do, I cannot get the original settings back. I can use the mouse but two buttons out of four are completely wasted.

2. Previously hardy allowed me to setup X so that when the laptop was docked and the lid closed, the two external display started in mirrored mode but when X fired up, I got a nice spanning desktop. Unfortunately that seems close to impossible to do with the new X. What gives?

I have attached my xorg that I am using right now and the script to use both monitors. 

Any help would be greatly appreciated.

Thanks
AM

xorg.conf
===========================================
Section "InputDevice"
	Identifier	"Configured Keyboard"
	Driver		"kbd"
	Option		"XkbRules"              "xorg"
	Option		"XkbModel"              "pc105"
	Option		"XkbLayout"             "us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"				"/dev/input/mice"
	Option		"Protocol"              "ExplorerPS/2"
	
	Option		"Buttons"				"5"
	Option		"ButtonMapping"			"1 8 3 2 9"
	Option		"EmulateWheel"			"true"
	Option		"EmulateWheelTimeout"	"300"
	Option		"EmulateWheelButton"	"2"
	Option		"YAxisMapping"			"4 5"
	Option		"ZAxisMapping"			"6 7"
	Option		"DragLockButtons"		"9 1"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Modes	"1920x1200" "1400x1050"
		Virtual	3840 1200
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice "Configured Keyboard"
	InputDevice "Configured Mouse"
EndSection
===========================================

Script to setup both monitors post-login:
============================================
xrandr --output TMDS-1 --auto
xrandr --output LVDS --off
xrandr --output VGA --auto
xrandr --output VGA --right-of TMDS-1
============================================

---

