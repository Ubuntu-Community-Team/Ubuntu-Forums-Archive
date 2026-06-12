---
title: "unknown monitor and i cant add modelines"
date: 2011-02-02
forum: Hardware
---

### Post by gokudera889 on 2011-02-02
hello, i know theres another topic about this issue but it didnt worked at me or i cant do that, i tried nearly everything. here is the xorg.conf


```
Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
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

i want to add 1920x1080, but i cant, i made a lot of modelines from modeline generator but they didnt work. i have ati hd4650 videocard and lg E2240S monitor, please help me..

---

