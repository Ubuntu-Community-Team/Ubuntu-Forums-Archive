---
title: "External screen flickering @ 1680x1050"
date: 2008-10-11
forum: Hardware
---

### Post by oellegaard on 2008-10-11
Hello everyone!

I keep getting flickering at the screen, when using 1680x1050, all other resolutions works fine!

I've attached my laptops configuration and hardware (a zip file, containing a HTML file, sinced they can't be attached directly).

**My xorg.conf:**

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"dk"
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
	Option "DPMS" "true"
	HorizSync 30-60
	VertRefresh 50-70
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

[B]
xrandr -q[/B]
Screen 0: minimum 320 x 200, current 1280 x 960, maximum 1440 x 1440
VGA connected 1280x960+0+0 (normal left inverted right x axis y axis) 470mm x 300mm
   1440x900       59.9  
   1280x960       59.9* 
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        66.7     60.0  
LVDS connected 1280x800+0+0 (normal left inverted right x axis y axis) 331mm x 207mm
   1280x800       59.9*+   60.0  
   1280x768       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
TV disconnected (normal left inverted right x axis y axis)


It would really be appreciated if you could help me on this matter, been trying for several weeks now, and Windows can do it, so it's sad that ubuntu won't let me!! :O

/Kristian

---

