---
title: "External Monitors and Projectors"
date: 2007-06-05
forum: Hardware &amp; Laptops
---

### Post by royrules22 on 2007-06-05
I'm running Fesity with Beryl installed BTW. And I'm connecting with a VGA cable not DVI.

I can turn on my laptop connected to my external monitor and it will display the display on both the laptop screen and the monitor. It also doesn't let me go above the highest resolution the laptop display supports (1280x768) which looks ugly on a monitor that has a native res of 1680x1050. How do I get it to just turn off the laptop display and show on the monitor at a higher res?

Also when the system is already running and I connect a monitor or say a projector it does nothing. Display is only on laptop, not external screen. Fn+F8 does nothing. I can't find a menu listing to change displays either.

Any help would be appreciated.

PS: Everytime I post here I note that I've already searched and none of the suggestions help, but I still get flamed. Please can we avoid that now?

---

### Post by IntuitiveNipple on 2007-06-05
Switching monitor outputs usually depends on model-specific functionality including hot-key drivers, ACPI event handling, and video driver support.

It might help to describe your PC model, video card chip-set version, and any additional hot-key or model-specific embedded controller drivers you are aware it uses.

---

### Post by royrules22 on 2007-06-05
Ok thanks for the reply.

It's an Asus W3J+ model
Core Duo T2500
ATI Radeon Mobility x1600

I think I have fglrx (It's been a while since I set up Beryl so I'm not sure)

AFAIK I have not touched any hot-key drivers. On Windows Fn+F8 is to switch display.

> 01:00.0 VGA compatible controller: ATI Technologies Inc M56P [Radeon Mobility X1600]

I don't know what acpi is. Command gives me battery and thermal info.

> *-display
                description: VGA compatible controller
                product: M56P [Radeon Mobility X1600]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@01:00.0
                version: 00
                size: 256MB
                width: 32 bits
                clock: 33MHz
                capabilities: vga bus_master cap_list
                configuration: driver=fglrx_pci latency=0
                resources: iomemory:c0000000-cfffffff ioport:b000-b0ff iomemory:fdff0000-fdffffff irq:16

I'll post my xorg when I'm connected to the monitor in a short while.

---

### Post by royrules22 on 2007-06-05
Ok I got it to display 1680x1050 on my screen resolution thing, but my laptop screen is still on and when I do choose 1680x1050 I get this screen (see attached). It cuts off most of the screen estate. I've also attached my xorg.conf for your viewing. Err apparently I can't upload .conf files so inlined:

EDIT- Monitor model is 22" Samsung 226BW. Native resolution of 1680x1050, Contrast Ratio(typ.)	 1000:1, Horizontal Refresh Rate 30kHz - 81kHz, Vertical Refresh Rate 	56Hz - 75Hz

```

Section "Monitor"
	Identifier   "Generic Monitor"
	HorizSync    28.0 - 64.0
	VertRefresh  43.0 - 60.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. ATI Default Card"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. ATI Default Card"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x768" "1280x1024" "1440x900" "1680x1050"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x768" "1280x1024" "1440x900" "1680x1050"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x768" "1280x1024" "1440x900" "1680x1050"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x768" "1280x1024" "1440x900" "1680x1050"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x768" "1280x1024" "1440x900" "1680x1050"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x768" "1280x1024" "1440x900" "1680x1050"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes    "1280x768" "1280x1024" "1440x900" "1680x1050"
	EndSubSection
EndSection

```

---

### Post by royrules22 on 2007-06-06
It's been 14 hours? Anyone? :D

---

### Post by royrules22 on 2007-06-07
Anybody? 

(Posted 14 hours after last)

---

### Post by royrules22 on 2007-06-20
Help? I still get that problem

---

### Post by royrules22 on 2007-06-22
no one?

---

### Post by royrules22 on 2007-07-05
The latest updates didn't help either (though it did kill my sound)

---

