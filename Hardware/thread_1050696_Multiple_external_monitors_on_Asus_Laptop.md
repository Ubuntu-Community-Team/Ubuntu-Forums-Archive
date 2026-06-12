---
title: "Multiple external monitors on Asus Laptop"
date: 2009-01-25
forum: Hardware
---

### Post by nugget210 on 2009-01-25
I'm probably missing something obvious in my xorg.conf file but...

I'm trying to get my LG 22" Widescreen to work through VGA connection and my Sony 40" TV to work via HDMI - AT THE SAME TIME...

I can get either one working by itself but as soon as I plug both in, it reverts back to only using one at a time.

Here's my xorg.conf file...

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
	InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
EndSection

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizEdgeScroll" "0"
EndSection

Section "Monitor"
	Identifier   "Configured Monitor"
EndSection

Section "Device"
	Identifier  "Configured Video Device"
	Driver      "fglrx"
	Option	    "EnableMonitor" "crt1,lvds,tv,tmds1,crt2,tmds2,cv,tmds2i"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
	DefaultDepth    24
EndSection



So do I need to make another section for another screen or something?  Sorry about my noobness...

Thanks!!

---

### Post by nixscripter on 2009-01-26
Basic question: does "at the same time" mean (a) mirrored copies of one desktop, (b) different sections of a single desktop, (c) different desktops on different devices?

---

