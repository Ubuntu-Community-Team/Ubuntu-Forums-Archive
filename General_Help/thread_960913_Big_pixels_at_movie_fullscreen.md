---
title: "Big pixels at movie fullscreen"
date: 2008-10-27
forum: General Help
---

### Post by purplys on 2008-10-27
I am using Ubuntu 8.04 on laptop Amilo xi 1554
My Graphic Card is Ati X1900
I instaled registicted driver.
Everything is fine but when i am trying to watch a movie to fullscreen the Pixels in the movie its to big...in normal size everything is fine.
Tha happens with any player....mplayer,vlc..bla bla....


Here is my xorg.conf , glxinfo and fglrxinfo


Xorg.conf:

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

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"fglrx"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
EndSection






fglrxinfo :

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1900
OpenGL version string: 2.1.7412 Release



And glxinfo (i want to point that direct rendering is ok) :

name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2

---

### Post by purplys on 2008-10-28
Update: 
Compiz and visual effects working perfect....

---

