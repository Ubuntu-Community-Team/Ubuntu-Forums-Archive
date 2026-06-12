---
title: "twinview on new install... plz help"
date: 2005-06-13
forum: Hardware &amp; Laptops
---

### Post by foobar on 2005-06-13
i searched and tried most of the twinview threads with no luck...
i now have a fresh install of hoary and am looking for help to set this up.

specs:
 geforce fx5500 (vga, dvi, s)
 2 - syncmaster 152n
 dell 530 workstation

what should be the very first step?... drivers?

---

### Post by GrumpySmurf on 2005-06-13
Did you see this thread?

[http://ubuntuforums.org/showthread.php?t=27871](http://ubuntuforums.org/showthread.php?t=27871)

Shouldn't be much different for you.

---

### Post by foobar on 2005-06-13
yes i have, but i had zero luck with it... most likely due to my noobiness
so, the first thing i should do is dl and install NVIDIA-Linux-x86-1.0-7174-pkg1.run?

---

### Post by GrumpySmurf on 2005-06-14
First you'll need to install the binary NVIDIA driver.

[http://www.ubuntuguide.org/#installnvidiadriver](http://www.ubuntuguide.org/#installnvidiadriver)

My other thread assumes that the NVIDIA driver is installed and functional.

---

### Post by foobar on 2005-06-14
driver is installed and seems to be working fine.
how did you get the names of your screens?

---

### Post by foobar on 2005-06-15
got it working... Xorg.0.log told me everything.

thanks for the help

---

### Post by leohart on 2005-06-21
[QUOTE=foobar]got it working... xorg.conf told me everything.

thanks for the help[/QUOTE]

Would you mind posting a little guide and your xorg.conf file for reference?

---

### Post by foobar on 2005-06-21
sure;

this is how my xorg looked before twinview-
```
Section "Device"
	Identifier	"NVIDIA Corporation NV34 [GeForce FX 5500]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV34 [GeForce FX 5500]"
	Monitor		"SyncMaster"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection
```
and this is how it looks [color=red]with twinview-[/color]
```
Section "Device"
	Identifier	"NVIDIA Corporation NV34 [GeForce FX 5500]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
        [color=red]Option          "NoLogo"
	Option          "TwinView"
        Option          "TwinViewOrientation" "RightOf"
	Option          "MetaModes" "CRT-0: 1024x768, CRT-1: 1024x768"
	Option 		"RenderAccel" 		"true"[/color]
EndSection

Section "Monitor"
	Identifier	"[color=red]CRT-1[/color]"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV34 [GeForce FX 5500]"
	Monitor		"[color=red]CRT-1[/color]"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection
```
i got the names of the screens 'crt-0' and 'crt-1' from the X0rg.0.log. (im using lcds though)  ;-)

---

