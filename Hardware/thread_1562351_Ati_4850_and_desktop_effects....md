---
title: "Ati 4850 and desktop effects..."
date: 2010-08-27
forum: Hardware
---

### Post by firefreak on 2010-08-27
Is this possible?

I've followed some guide to change to the radeon HD driver but compizcheck gives me this:

 Distribution:          Ubuntu 10.04
 Desktop environment:   KDE4
 Graphics chip:         ATI Technologies Inc RV770 [Radeon HD 4850]
 Driver in use:         radeonhd
 Rendering method:      None


Xorg.conf looks like this:

Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"radeonhd"
	option   "DRI" "on"   #this is the default in recent radeonhd versions
        Option   "AccelMethod" "EXA" #this is the default in recent radeonhd versions

EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection


I'm running Kubuntu 10.04.

Any ideas?

---

