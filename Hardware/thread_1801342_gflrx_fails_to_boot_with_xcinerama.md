---
title: "gflrx fails to boot with xcinerama"
date: 2011-07-10
forum: Hardware
---

### Post by kc7rwx on 2011-07-10
I have two Radeon HD 5500 Series adapters.  

I can get them working with two x-servers but if I enable xcinerama the system hangs on boot.

any ideas?
 

my xorg.conf

```
Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
	Screen         "aticonfig-Screen[1]-0" RightOf "aticonfig-Screen[0]-0"
EndSection

Section "Module"
EndSection

Section "ServerFlags"
	Option	    "Xinerama" "on"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
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

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:10:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[1]-0"
	Driver      "fglrx"
	BusID       "PCI:4:0:0"
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
	Identifier "aticonfig-Screen[1]-0"
	Device     "aticonfig-Device[1]-0"
	Monitor    "aticonfig-Monitor[1]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection
```

---

