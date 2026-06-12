---
title: "Unable to read GPU temperature ATI HD4650"
date: 2010-09-24
forum: Hardware
---

### Post by urosg3 on 2010-09-24
```
aticonfig --od-gettemperature
``` returns me

```
No layout section was found in the file: '/etc/X11/xorg.conf'.
Please run 'aticonfig --initial' first or modify your configurationfile manually and run aticonfig again.
```

I run aticonfig --initial with no luck

```
urosh@urosh-desktop:~$ aticonfig --initial
Found fglrx primary device section
 Unable to find any supported Screen sections
```

Any help please?

---

### Post by alanwalterthomas on 2010-12-05
Same problem here. BUMP!

---

### Post by alanwalterthomas on 2010-12-05
Solved it!

This worked:
sudo aticonfig --initial -f

Putting that -f at the end made the difference.

In case it helps, this is what my xorg.conf became:

Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
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

---

### Post by urosg3 on 2010-12-05
Yes, working here to. Someone must edit wiki howto, and add little -f at the end

---

