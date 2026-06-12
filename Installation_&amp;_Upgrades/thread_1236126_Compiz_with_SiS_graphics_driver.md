---
title: "Compiz with SiS graphics driver"
date: 2009-08-09
forum: Installation &amp; Upgrades
---

### Post by joelgsf on 2009-08-09
:confused: I would like to use Compiz with the SiS 315PRO Graphics Card I have in my desktop, running Ubuntu 9.04 (i386). I ran "compiz-check" to check compatibility and got the following output:

```

Gathering information about your system...

 Distribution:          Ubuntu 9.04
 Desktop environment:   GNOME
 Graphics chip:         Silicon Integrated Systems [SiS] 315PRO PCI/AGP VGA Display Adapter
 Driver in use:         sis
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [FAIL]

There has been (at least) one error detected with your setup:
 Error: Software Rasterizer in use

```

It seems to be all Ok, execpt for the fact that "Software Rasterizer" is in use. Well, my problem is that I don't know where this has been set up and how to change it, if possible. My "xorg.conf file reads ...
> 
Section "Device"
	Driver		"sis"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
    	HorizSync    28-72
    	VertRefresh  43-60
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
    	SubSection "Display"
        	Depth    24
        	Modes    "1280x768"    "1024x768"    "800x600"    "640x480"
    	EndSubSection
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection


This configuration file was in use for a "vesa" driver, to solve original problems of resolution, as the system did not recognised automatically my SiS driver. After much search I realized that the SiS driver was already in place and I just switched "vesa" for "sis".
Does anyone know if and how I can correct this problem?
TIA

---

