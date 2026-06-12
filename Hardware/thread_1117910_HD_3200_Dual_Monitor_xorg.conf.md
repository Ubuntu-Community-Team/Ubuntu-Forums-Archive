---
title: "HD 3200 Dual Monitor xorg.conf"
date: 2009-04-06
forum: Hardware
---

### Post by toobukume on 2009-04-06
Doesn't Display Properly...

My Physical Setup:
HP Pavilion tx2510us Tablet Notebook with ATI Radeon HD 3200 Graphics card integrated
External monitor to the left of the laptop.

With the xorg.conf below, when the system comes on, the laptop's monitor shows the desktop and has a workable mouse but no toolbars or anything. The external monitor is black but I CAN move my mouse over to it. When I move my mouse over to it, I no longer have the pretty ubuntu mouse and it becomes an "X". 

Can someone please point out what's wrong in my config? Thanks in advance!

BTW, This started out as an aticonfig xorg.conf that I modified so that it made more sense to me. The original xorg.conf had the same results.

```

Section "Module"
	Load  "glx"
EndSection

Section "ServerLayout"
	Identifier     "layout0"
	Screen         "screen0"
	Screen         "screen1" LeftOf "screen0"
EndSection

Section "Monitor"
	Identifier   "monitor0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "monitor1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "hd3200-0"
	Driver      "fglrx"
	BusID       "PCI:1:5:0"
EndSection

Section "Device"
	Identifier  "hd3200-1"
	Driver      "fglrx"
	BusID       "PCI:1:5:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "screen0"
	Device     "hd3200-0"
	Monitor    "monitor0"
	DefaultDepth     24
	SubSection "Display"
		Depth     24
		Modes    "1280x800"
	EndSubSection
EndSection

Section "Screen"
	Identifier "screen1"
	Device     "hd3200-1"
	Monitor    "monitor1"
	DefaultDepth     24
	SubSection "Display"
		Depth     24
		Modes    "1680x1050"
	EndSubSection
EndSection

```

---

