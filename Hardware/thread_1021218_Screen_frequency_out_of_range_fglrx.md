---
title: "Screen frequency out of range fglrx"
date: 2008-12-25
forum: Hardware
---

### Post by shamnex on 2008-12-25
First of all I would like to say Im a complete NOOB.

Hope I dont get flamed but after installing the fglrx driver using the restricted hardware drivers way my screen just goes black out on reboot after log on. I think the defaut resolution set for my monitor is too high cos My monitor only supports up to 1280x1024.

My graphic card is an old agp  x1300 running at 4x.

I tried installing with envy but got the same thing.

Thanks in advance

I running on ubuntu 8.10.



I've googled but can't seem to find a solution

---

### Post by shamnex on 2008-12-25
anybody?

nvm,solved it.

but now I've now moved from one problem to another.

I can't use visual effect.

I get "this drive is activated but currently not in use"

how do I use it ?co i  cannot activate visual effects

---

### Post by shamnex on 2008-12-28
someone please?
here is my xorg config 
> 

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
	HorizSync       30-81 
        VertRefresh     60
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
		Modes	  "1280x1024_60"  
	EndSubSection
EndSection

---

### Post by shamnex on 2009-01-01
anyone?

---

