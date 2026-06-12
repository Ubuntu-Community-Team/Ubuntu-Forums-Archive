---
title: "any success with Matrox g400 dualhead and two monitors?"
date: 2005-07-17
forum: Hardware &amp; Laptops
---

### Post by arjay1 on 2005-07-17
I know there are a lot of posts in this forum about dual monitor setups - but most apply to nvidia twinview or dual video card systems.

I have a Matrox g400 dualhead that, as the name implies - has two video outputs for two monitors on the one card.  I managed to get the card to work in Fedora FC3 and in simplymepis but don't like those distros for various reasons.  I am very keen on Kubuntu which has installed flawlessly on my system - including finding my various digital cameras and a mixed win xp, linux, wireless laptop network. 

However, I just cannot get the card to work in a dual monitor setup under kubuntu - which is very disppointing.  I have been fiddling around for several days now cutting and pasting from my old xorg.conf's from the other distros.  I have also tried switching to an XF86config-4 setup - to no avail.

If anyone has succeeded with this card, I would appreciate a copy of their xorg,conf file, and/or a listing of their var/log/xorg.0.log.  

The main trouble I am having is that my setup does not like the very common lines in the xorg.conf of Screen0 and Screen1 under devices. Below is the relevant bit of my file.  Perhaps someone could have a look at it for any obvious errors?

TIA

Partial output from xorg.conf:

Section "Device"
	Identifier	"G400_0"
	Driver		"mga"
	BusID		"PCI:1:0:0"
	Screen0
EndSection

Section "Device"
	Identifier	"G400_1"
	Driver		"mga"
	BusID		"PCI:1:0:0"
	Screen1
EndSection

Section "Monitor"
	Identifier	"Monitor0"
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"Monitor1"
	Option		"DPMS"
EndSection


Section "Screen"
	Identifier	"Screen0"
	Device		"G400_0"
	Monitor		"Monitor0"
	DefaultDepth	24
SubSection "Display"
		Depth		24
		Modes		"1280x1024" 
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Screen1"
	Device		"G400_1"
	Monitor		"Monitor1"
	DefaultDepth	16
SubSection "Display"
		Depth		16
		Modes		"800x600"
	EndSubSection
	
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Screen0" LeftOf "Screen1"
	Screen 		"Screen1" 0 0
	InputDevice	"Configured Mouse"
	InputDevice	"Generic Keyboard"
	Option "Xinerama"
	
EndSection

---

### Post by alex.e.c. on 2007-02-09
Try here:

[http://www.tuxx-home.at/projects/mga/HOWTO_mga_Xorg7](http://www.tuxx-home.at/projects/mga/HOWTO_mga_Xorg7)

Though not with edgy, and the links seem to be broken as well.

---

