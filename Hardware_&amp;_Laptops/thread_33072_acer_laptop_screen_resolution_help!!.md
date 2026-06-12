---
title: "acer laptop screen resolution: help!!"
date: 2005-05-09
forum: Hardware &amp; Laptops
---

### Post by ash on 2005-05-09
hi, 

i have an acer 281LC Travelmate, on which I have installed Ubuntu.  One major problem: the screen resolution is only 640x480 @ 60Hz, and this is the only option available under the Screen Resolution dialog.  Under Windows XP the laptop was running at 1024x768...

Help greatly appreciated.  Please treat as complete newbie as far as Linux is concerned.  Thanks...

---

### Post by dbott67 on 2005-05-09
Hi Ash,

I had similar issues after a fresh installation of Ubuntu 5.04.  My video resolution was only 640x480 with 1" black band along right side and 1/4" along bottom. The issue appears to be related to hsync & vsync, as well as Modeline settings. Secondary issue with performance may be related to default colour depth of 24 (changing colour depth to 16 increases performance noticably).

This is what I had to do:

1. Edit /etc/X11/xorg.conf (**sudo gedit /etc/X11/xorg.conf**):

Added/changed the following lines in "Monitor" Section:

Section "Monitor"
Identifier "Generic Monitor"
**HorizSync 30-64**
**VertRefresh 50-100**
Option "DPMS"
**Modeline "640x480" 25.175 640 664 760 800 480 491 493 525 #60Hz**
**Modeline "800x600" 40 800 848 968 1056 600 601 605 628 +hsync +vsync**
**Modeline "1024x768" 65 1024 1032 1176 1344 768 771 777 806 -hsync -vsync**
EndSection

Section "Screen"
Identifier "Default Screen"
Device "NeoMagic Corporation NM2200 [MagicGraph 256AV]"
Monitor "Generic Monitor"
**DefaultDepth 16**

2. Save file and restart

It took a fair amount of Googling to find information about **hsync, vsync and Modeline** for my Tecra 8000 before I found the above information.

Good luck,
Dave

---

### Post by ash on 2005-05-09
dave, 

it worked!! 

thanks a million, completely appreciate it!

smiling ash. :)

---

### Post by dbott67 on 2005-05-09
[QUOTE=ash]dave, 

it worked!! 

thanks a million, completely appreciate it!

smiling ash. :)[/QUOTE]
 Hi Ash,

That's great!  Maybe you could post the "Monitor" section of your xorg.conf file here for other Acer Travelmate users.

BTW: Ubuntu 4.10 (Warty) picked up the video settings on my Tecra without a problem (I think Warty was using XFree, as opposed to Xorg).  When I upgraded to 5.04 it must have picked up the xfree config file, as the video settings were just fine.  I only had issues when I did a clean install of 5.04.

Take care,
Dave

---

### Post by ash on 2005-05-09
hi dave, 

here are the updated changes: 

Section "Monitor"
	Identifier	"Generic Monitor"
	HorizSync 30-64
	VertRefresh 50-100
	Option		"DPMS"
	Modeline "640x480" 25.175 640 664 760 800 480 491 		493 525 #60Hz
	Modeline "800x600" 40 800 848 968 1056 600 601 605 		628 +hsync +vsync
	Modeline "1024x768" 65 1024 1032 1176 1344 768 771 		777 806 -hsync -vsync

EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Monitor		"Generic Monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection



Thanks 
Ash.

---

