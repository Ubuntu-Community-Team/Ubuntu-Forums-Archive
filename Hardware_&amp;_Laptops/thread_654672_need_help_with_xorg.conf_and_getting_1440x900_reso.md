---
title: "need help with xorg.conf and getting 1440x900 resolution on Radeon 9550"
date: 2007-12-31
forum: Hardware &amp; Laptops
---

### Post by ze_otter on 2007-12-31
I recently upgraded to the new ATI Catalyst 7.12 drivers on my Kubuntu Gutsy installation, according to the [instructions here]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide"). Otherwise it seems to work out all right, except that the login screen has different resolution to the rest of the system. I've tried editing xorg.conf file in various ways, inserting modelines for my monitor (from gtf), trying out different mode settings, just about everything I can think of, but any changes to the current settings seem to hose the system so that I lose the 1440x900 settings, no matter what I do.

One thing troubling me is that I don't see the 1440x900 setting anywhere except on the modeline in the Modes section, which I have added myself and which seems to be reduntant since commenting it out didn't change anything. I've done the dpkg-reconfigure route as well, but that didn't work-as soon as I reinstalled the fglrx driver, the configuration was hosed again. Neither the Catalyst Control Center or the KDE's System Settings seem to be able to do anything useful; they either don't recognize 1440x900 setting at all, or hose the system so that I get out-of-range errors on my monitor (those modelines were inserted by the system configuration tools. Touching them in any way seems to lose the 1440x900 settings).

Could some guru please help to clean up the xorg.conf so I can get a smooth-running system in 1440x900? Or if anyone has a fully functional system with the same set-up, posting a functioning xorg.conf might help to fix this myself.

Posted below are the display-relevant sections of my xorg.conf:
```

Section "Modes"
	Identifier	"Modes"
  modeline  "1024x768" 76.2 1024 1080 1192 1360 768 769 772 800
  modeline  "1024x768" 64.1 1024 1080 1184 1344 768 769 772 795
  modeline  "1440x900" 100.0 1440 1456 1464 1480 900 916 924 940 -hsync -vsync
EndSection

Section "Monitor"
	Identifier	"L194WT"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1400x1050@75" 155.85 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
  modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1792x1344@60" 204.8 1792 1920 2120 2448 1344 1345 1348 1394 -hsync +vsync
	Gamma	1.0
EndSection

Section "Monitor"
	Identifier	"aticonfig-Monitor[0]"
	Option		"VendorName"	"ATI Proprietary Driver"
	Option		"ModelName"	"Generic Autodetecting Monitor"
	Option		"DPMS"	"true"
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc RV350 AS [Radeon 9550]"
	Boardname	"ati"
	Busid		"PCI:1:0:0"
	Driver		"fglrx"
	Screen	0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV350 AS [Radeon 9550]"
	Monitor		"L194WT"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1792	1344
		Modes		"1400x1050@75"	"1600x1200@65"	"1400x1050@60"	"1600x1200@60"	"1280x960@75"	"1792x1344@60"	"1280x1024@60"	"1280x960@60"	"1280x1024@75"	"1152x864@75"	"1024x768@60"	"1024x768@70"	"1024x768@75"	"832x624@75"	"800x600@60"	"800x600@75"	"800x600@72"	"800x600@56"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "device" #
	Identifier	"device1"
	Boardname	"ati"
	Busid		"PCI:1:0:0"
	Driver		"fglrx"
	Screen	1
EndSection
Section "screen" #
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
EndSection
Section "monitor" #
	Identifier	"monitor1"
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection

```

---

