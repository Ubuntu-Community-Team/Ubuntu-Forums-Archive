---
title: "Installing the proper video drivers"
date: 2008-08-01
forum: General Help
---

### Post by inzania on 2008-08-01
Hey all,

In most regards, I feel as though I've graduated to understanding linux pretty well.  However, I have never quite understood the driver situation, mostly with regard to my video drivers.  I've tried to do my due-diligence here, but please excuse me if I have missed something obvious/easy.  I'm using a ThinkPad T60 (Intel Dual-Core) with 2GB of RAM, but otherwise fairly standard.  I'm concerned with my video drivers for a couple reasons: although the system now works fine and runs smoothly, I had a lot of trouble with getting an external monitor to work properly, and also my framerate is pretty low when doing anything at all graphics-intensive.  According to the "lspci | grep AGP" command, my video card is as follows:
```
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)

```
Well, this is not NVIDIA or ATI, I suppose.  Some googling of that phrase came up with this [thinkpad linux drivers website]("http://intellinuxgraphics.org/download.html").  On the website, there seems to be drivers for my video card, but I'm confused as to if it is actually necessary to download/build them, or if they are already on my machine with the regular distro.  I have looked at my xorg.conf file, and what caught my eye is how "standard" everything is.  When I see other people's config files, they usually have reference to specific hardware, etc.  Most people say that they only made small modifications, as well, which leads me to wonder if that is indicative of missing drivers or otherwise poor configuration:
```
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
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth 24 
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection
```

So, in short, I want to make sure I'm getting the best performance and configuration out of my hardware.  I feel like quite a newb writing this post, but I had to ask.  Thanks for your time.

---

### Post by Choad on 2008-08-01
intel's drivers are all open source now, so they work out of the box

this is my understanding of the situation anyway... i could be wrong

edit: tho i agree, that xorg.conf looks fishy to me as well :S

---

### Post by inzania on 2008-08-04
bump... still having trouble with this, and it is forcing me to use *gasp* Windows!  Would really appreciate some help...

---

