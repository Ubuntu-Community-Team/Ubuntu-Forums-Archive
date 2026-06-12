---
title: "Dual Monitors for Xubuntu 8.04 with SiSm7606x"
date: 2010-03-08
forum: Hardware
---

### Post by QueenNedro on 2010-03-08
Computer: Acer Aspire 3004wlci
OS: Xubuntu 8.04
Video Card: SiSm7606x

My laptop is over four years old. It is running Xubuntu 8.04. There was no driver available for its integrated video card, so it is using a generic driver. This means that it can not do 3D effects. Does this also prevent it from supporting dual monitors (extending the desktop)? If not, how do I go about setting that up?

I've found instructions for other video and graphic cards, but nothing that relates to my laptop. 

Thanks

---

### Post by QueenNedro on 2010-03-09
I'd like to extend my cry for help to say that the video card will clone the display to the second monitor, so extending the display must be possible. Another is the command 

xrandr -q 

shows this (with second monitor connected and used to clone display):

Screen 0: minimum 320 x 200, current 1280 x 800, maximum 1280 x 800
default connected 1280x800+0+0 0mm x 0mm
   1280x800       75.0*    60.0  
   1280x768       75.0     60.0  
   1280x720       75.0     60.0  
   1024x768       85.0     75.0     70.0     60.0  
   1024x576       75.0     60.0  
   960x600        60.0  
   960x540        60.0  
   800x600        85.0     75.0     72.0     60.0     56.0  
   768x576        60.0  
   720x576        60.0  
   856x480        60.0     76.0  
   848x480        60.0     76.0  
   800x480        85.0     75.0     60.0  
   720x480        61.0  
   640x480        85.0     75.0     73.0     60.0  
   640x400        72.0  
   512x384        60.0  
   400x300        60.0  
   320x240        61.0  
   320x200        71.0  

So, I cannot follow the instructions I've found to use xrandr. In addition, my xorg.conf file is pretty empty:

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
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
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
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection

Any advice on how to go about this?

---

