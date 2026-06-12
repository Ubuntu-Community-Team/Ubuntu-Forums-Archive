---
title: "fglrx &amp; ubuntu 8.04 - black screen"
date: 2008-07-16
forum: Hardware
---

### Post by erikf154 on 2008-07-16
I recently install kubuntu 8.04 on my laptop. I have however not been able to get the fglrx driver to work. My laptop has a ATI Mobility 9700, it worked fine in earlier versions of ubuntu.

If I enable the driver (restricted) and reboots I get nothing but a black screen once x has started. I've run apt-get to update the system, but that didn't do anything either.

This is my xorg.conf:
```
Section "ServerLayout"
	Identifier     "Default Layout"

	Screen         "aticonfig-Screen[0]" 0 0

	InputDevice    "Configured Mouse"
	InputDevice    "Synaptics Touchpad"
	InputDevice    "Generic Keyboard"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "Module"
	Load  "GLcore"
	Load  "glx"
	Load  "dbe"
	Load  "v4l"
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

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Depth     24
		Modes    "1400x1051"
	EndSubSection
EndSection

```

When I look into the xorg log I find this:
```
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.47.3
	ABI class: X.Org Server Extension, version 0.3
(II) fglrx(0): Using adapter: 1:0.0.
(--) fglrx(0): VideoRAM: 131072 kByte, Type: DDR SGRAM / SDRAM
(II) fglrx(0): AGP card detected
(WW) fglrx(0): board is an unknown third party board, chipset is supported

``` 

Can anybody help, please. It's driving me nuts.

---

### Post by Shardphoenix on 2008-07-16
Have you tried to get latest drivers from AMD/ATI?

---

### Post by erikf154 on 2008-07-17
No, I want to use the one in the repo. Easier to maintain.

---

