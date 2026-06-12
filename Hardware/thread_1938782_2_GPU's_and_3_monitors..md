---
title: "2 GPU's and 3 monitors."
date: 2012-03-10
forum: Hardware
---

### Post by gnomey on 2012-03-10
Hi guys,

I've recently upgraded my computer, I've added 2 ATI Radeon 5830's to it to replace my old NVidia card. After I done this, I was unable to boot ubuntu, so I made a boot disk and used it to install another copy of ubuntu over my current copy, while leaving personal my files.

GPU0, my main GPU, has 2 monitors connected to it. I have managed to get the fglrx driver installed and working with the GPU, and have got my monitors working on it.

GPU1 has 1 monitor connected to it. In catalyst it shows up as an unknown adapter with an unknown display and everytime I try to enable it, Catalyst crashes.

I have a feeling this is because GPU1 isn't using the fglrx driver, but I have no idea how to fix this.

Can anyone help me? Thanks in advance

Here is a copy of my xorg.conf:

> 
Section "Monitor"
	Identifier   "0-DFP4"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1680x1050"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "1366 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Monitor"
	Identifier   "0-CRT2"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1366x768"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "0 282"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Screen"
	Identifier "Default Screen"
	DefaultDepth	24
EndSection

Section "Screen"
	Identifier "amdcccle-Screen[7]-0"
	Device     "amdcccle-Device[7]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Virtual   3046 3046
		Depth     24
	EndSubSection
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "ServerLayout"
	Identifier     "amdcccle Layout"
	Screen      0  "amdcccle-Screen[7]-0" 0 0
EndSection

Section "Device"
	Identifier  "amdcccle-Device[7]-0"
	Driver      "fglrx"
	Option	    "Monitor-DFP4" "0-DFP4"
	Option	    "Monitor-CRT2" "0-CRT2"
	BusID       "PCI:7:0:0"
EndSection


---

### Post by gnomey on 2012-03-10
I just ran the following commands, and i've made some progress:

sudo aticonfig --initial --heads=2 --adapter=1
sudo aticonfig --initial --heads=2 --adapter=2

now all of my monitors are detected, and all appear in Catalyst. The problem is, only my main monitor works (monitor0 of gpu0) and all of the other ones show a white screen, and when I move the mouse on to them I get a black x as a pointer.

I know I have to make some change to my xorg.conf, but not sure what exactly.

Here's my new xorg.conf:

> Section "ServerLayout"
	Identifier     "amdcccle Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
	Screen         "aticonfig-Screen[0]-1" LeftOf "aticonfig-Screen[0]-0"
	Screen         "aticonfig-Screen[1]-0" RightOf "aticonfig-Screen[0]-0"
	Screen         "aticonfig-Screen[1]-1" RightOf "aticonfig-Screen[1]-1"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[1]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[1]-1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:7:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-1"
	Driver      "fglrx"
	BusID       "PCI:7:0:0"
	Screen      1
EndSection

Section "Device"
	Identifier  "aticonfig-Device[1]-0"
	Driver      "fglrx"
	BusID       "PCI:2:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[1]-1"
	Driver      "fglrx"
	BusID       "PCI:2:0:0"
	Screen      1
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

Section "Screen"
	Identifier "aticonfig-Screen[0]-1"
	Device     "aticonfig-Device[0]-1"
	Monitor    "aticonfig-Monitor[0]-1"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[1]-0"
	Device     "aticonfig-Device[1]-0"
	Monitor    "aticonfig-Monitor[1]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[1]-1"
	Device     "aticonfig-Device[1]-1"
	Monitor    "aticonfig-Monitor[1]-1"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection


---

### Post by gnomey on 2012-03-14
Bump. Still haven't fixed this yet. Anybody have an idea?

---

