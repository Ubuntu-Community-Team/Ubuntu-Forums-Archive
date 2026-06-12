---
title: "LCD doesn't like enabling nvidia acceleration driver"
date: 2007-10-08
forum: Hardware &amp; Laptops
---

### Post by Moo-buntu on 2007-10-08
For the last few days, I've been trying to get WoW on Ubuntu. Partially for giggles but more because I wanted to do something that my Linux-loving buddy didn't and made an XP box for.  Unfortunately, the change to xorg.conf killed my ability to see the GUI. I've searched for hours and came up with nothing in forums or help guides so I wiped the drive and started over. Sadly on a new drive (old one toasted last night). 

After first backing up xorg.conf this time, I tried using the restricted drivers manager this time and ended up with the same blank white screen (sound audible in the background, though). Looking at the differences in the backup and the changed file, I noticed a difference I (even being a total newb) figured I could safely change.

The LCD default resolution is 1600x1200 with a depth of 16.

> Original:

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV17 [GeForce4 420 Go]"
	Monitor		"Generic Monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1600x1200"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200"
	EndSubSection
EndSection

> Changed after install:

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV17 [GeForce4 420 Go]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200"
	EndSubSection

changing > DefaultDepth	24 to 16 allowed me to boot back to GUI login, but decreased my resolution, though the acceleration driver is still enabled. Which is, so far, good in my mind. It seems the LCD can't handle 24bit depth at 1600x1200 which is nice considering I thought the driver seriously mucked things up.

I'll continue playing around with screen settings until I find something I like and try and update (but I get seriously lazy about writing). I do hope someone can use this info, it certainly would've saved me a few hours internet surfing. I'll also welcome any tips to help me along my current path.

Thanks for reading and please don't chase me out of town with torches and pitchforks. Or their digital equivalents, lol.

Moo

---

