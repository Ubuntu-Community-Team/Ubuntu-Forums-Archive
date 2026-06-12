---
title: "Screen issues"
date: 2009-10-29
forum: Hardware
---

### Post by M16mKies on 2009-10-29
Howdy!
I'm using Ubuntu 9.10 (final).
My graphics card is Radeon HD 3850 (gainward).
My monitor - Samsung 920NW (via d-sub).

The problem is - refresh rate and vertical/horizontal/whatever sync issue.
On every Windows i had no problems setting refresh rate at 75Hz on 1440x900 native resolution. On 9.10, after installing ATi Drivers properly, I have no such option. I'm stuck at 55.9kHz 60Hz, while on any windows, including 7, I'm able to use 70.7kHz 75Hz.

I tried forcing Xorg.conf to use 75Hz, but it didn't change anything.

So, what can I do? It's REALLY annoying, since it makes watching movies very uncomfortable, especially on dynamic scenes.

My Xorg.conf file looks like following:

```
Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

---

### Post by M16mKies on 2009-10-29
bump?

---

