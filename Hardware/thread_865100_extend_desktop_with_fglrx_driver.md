---
title: "extend desktop with fglrx driver"
date: 2008-07-20
forum: Hardware
---

### Post by luntain on 2008-07-20
I was happily running gutsy with extended desktop until I upgraded to hardy. Now my dual-head setup almost works, but the quality annoys me (I see some waves on my external display). That starts to be upgrading-tradition: I had problems with my dual-head setup when upgrading from faisty to gutsy also.

Anyway, my gutsy xorg.conf:

```
Section "Device"
	Identifier	"radeon"
	Driver		"ati"
	Option		"UseFBDev"		"true"
    Option      "Monitor-LVDS"  "Internal Panel"
    Option      "Monitor-VGA-0" "External Panel"
EndSection

Section "Monitor"
	Identifier	"Internal Panel"
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"External Panel"
	Option		"DPMS"
    Option      "RightOf" "Internal Panel"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"radeon"
	Monitor		"Internal Panel"
	DefaultDepth	24
	SubSection "Display"
		Depth 24
		Virtual 3200 1200
	EndSubSection
EndSection


Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection
```

As I said, it almost works in Hardy, except for unacceptable quality of the image on my external monitor (some settings to improve it anyone?).

The system was offering me to enable proprietary driver for my ati card; I enabled it, and the image is crisp clear, but it is no longer an extended desktop :(. As I noticed, there was only one change in the xorg.conf, in the device section it changed driver from "ati" to "fglrx".

So how do I improve image with "ati" driver or how do I extend the desktop with "fglrx" (the proprietary one)?

I tried aticonfig --initial=dual-head --screen-layout=right with fglrx, which only screwed things up, and I had to restore xorg.conf in command line mode.

---

