---
title: "Monitor Not detected"
date: 2008-12-24
forum: Hardware
---

### Post by RedSingularity on 2008-12-24
Hey guys, 

I recently installed ubuntu on a new desktop.  It has a Radeon HD 3300 on the motherboard.  I have put a ACER 19 inch monitor in.  The problem is when i go to System> Preferences> screen resolution i get a big fat _Unknown_.  My x.org file does not seem to detect it either.  


Here is the file:

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

---

### Post by RedSingularity on 2008-12-24
....And here is the BUMP!!!!

---

