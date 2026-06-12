---
title: "Slow graphics/no 3D with SIS M760"
date: 2007-12-21
forum: Hardware &amp; Laptops
---

### Post by Berolina on 2007-12-21
Hi,

I'm having problems with the SIS M760 vga-card (Fujitsu-Siemens Laptop, ADM Turion 64 bit processor), e. g.  I can't use any 3D effects/games. I'm using the latest Ubuntu version 2.6.22-14-generic  i686. (I'm running the 32-bit version on purpose, as the 64-bit one wouldn't install on my maschine...)
I have tried ```
sudo dpkg-reconfigure -phigh xserver-xorg
```, but it didn't help (just set my keyboard for "german" to "us" ;-(
Here's an excerpt from my xorg.conf:

> Section "Device"
	Identifier	"Standardgrafikkarte"
	Boardname	"sis"
	Busid		"PCI:1:0:0"
	Driver		"sis"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Standardbildschirm"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1024x768"
	Horizsync	31.5-48.0
	Vertrefresh	56.0 - 65.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Standardgrafikkarte"
	Monitor		"Standardbildschirm"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1024	768
		Modes		"1024x768@60"	"800x600@60"	"800x600@56"	"640x480@60"
	EndSubSection
EndSection
Section "device" #  
	Identifier	"device1"
	Boardname	"sis"
	Busid		"PCI:1:0:0"
	Driver		"sis"
	Screen	1
EndSection
Section "screen" #  
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
	SubSection "Display"
		Depth	24
		Modes		"640x480@60"
	EndSubSection
EndSection
Section "monitor" #  
	Identifier	"monitor1"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
	Gamma	1.0
EndSection

Does anyone know a quick and foolproof solution? 

Thanks a lot in advance

---

