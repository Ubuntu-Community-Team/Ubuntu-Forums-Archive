---
title: "xserver and gdm dont work"
date: 2009-06-29
forum: Installation &amp; Upgrades
---

### Post by Simonpatp on 2009-06-29
I have a nice old Dell D300 that has 300MHz Pentium II and 128MB of RAM, and no internet connection. I decieded to install Xubuntu on it, and after it installed, I booted it up, and X did not show up, instead I got a command line login and interface. I tried startx, and it outputs 
**unimportant stuff
(EE)VESA(0) Driver can't support depth 24
(EE)sceens found but none have a usable configuration

Fatal server error:
no screens found
**more stuff

xorg.conf looks like this:
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


I added in DefaultDepth 16 and it changed the first line of the error to VESA: no mathing modes
I reistalled GDM, and have tried to start gdm, it starts fine, Ctrl alt F7 is just blank however
I have looked around, and havenot found any answers
Please help

---

### Post by Simonpatp on 2009-06-29
I should also mention that I previously had  Ubuntu 8.10 working on it, it was slow, so  Instaled Xubuntu 810, and it had this same problem, along with Ubuntu 904 and xubuntu 904

---

