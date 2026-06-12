---
title: "Screen resolution problem in Gnome"
date: 2005-06-05
forum: Hardware &amp; Laptops
---

### Post by bae22 on 2005-06-05
Hi all,

I recently installed Ubuntu 5.04 on my brand new laptop (Acer Aspire 1522WLMi), which has a 15.4 inch widescreen on it. I recently noticed that some text was a bit fuzzy in places, and checked on the resolution in Gnome.

It is running at 1280x768, and there is not option in the Gnome Creen Resolution prefs to change it to 1280x800 as it shoud be.

I checked my xorg.conf file, but it seems to be set up fine:

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-67
	VertRefresh	30-60
	Modeline	"1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV36 [GeForce FX Go 5700]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection
EndSection

It's the only screen resolution mentioned, so why does Gnome only let me use 1280x768? It seems to match another config file from someone who installed SLackware on the same model (found via linux-laptops.net).

I can't find any text config files anywhere for Gnome that are to do with the resolution to try and chage it manually.

Please does anyone have any ideas to solve this annoyance? I am presuming that Gnome is at fault, not my xorg.conf file.

Cheers

---

### Post by flanker on 2005-06-05
Gnome can set resolutions on a per user basis. To force gnome to use the X server default you can delete gnomes resolution config files from your home directory.

Log in as your user and type the following in a terminal;
rm -rf ~/.gconf/desktop/gnome/screen/*

Then logout and back in again.

---

### Post by bae22 on 2005-06-05
[QUOTE=flanker]Gnome can set resolutions on a per user basis. To force gnome to use the X server default you can delete gnomes resolution config files from your home directory.

Log in as your user and type the following in a terminal;
rm -rf ~/.gconf/desktop/gnome/screen/*

Then logout and back in again.[/QUOTE]
 I don't have the "screen" directory in ~/.gconf/desktop

I've searched through all my config files and can't find anything related to the screen resolution.

---

### Post by bae22 on 2005-06-06
[QUOTE=bae22]I don't have the "screen" directory in ~/.gconf/desktop

I've searched through all my config files and can't find anything related to the screen resolution.[/QUOTE]
 PROBLEM SOLVED

In the end, Gnome was not at fault. It would appear that my xorg.conf file was incorrect.

After scouring the internet again for other people with the same laptop, I found someone else who had the same problem. He found that the display did not like the 60Hz refresh rate Hoary set up, but would run at 1280x800 at 50Hz

I tried changing the modeline in xorg.conf to

Modeline 	"1280x800_50.00"  68.56  1280 1336 1472 1664  800 801 804 824  -HSync +Vsync

as suggested by the gtf programme, and my laptop restarted in 1280x800 with no fuss.

I hope that helps anyone else out there with an Acer widescreen laptop.

And thanks Flanker for your help

---

### Post by danbert on 2006-09-03
I have this same problem where Gnome will not display my correct resolution.  I have a Tangent laptop (don't ask, my university made me buy it) with a widescreen display capable of 1680x1050.  xorg.conf lists the resolution under all color displays, but I cannot figure out how to display the widescreen resolution as the Gnome resolution changer only list 4:3 aspect ratios.  I also don't have a screen directory, and don't see anything similar to the previous post in my xorg.conf file.

---

