---
title: "Yet another screen resolution problem please help"
date: 2005-09-15
forum: Hardware &amp; Laptops
---

### Post by paTt3rN R3CoGnItIon on 2005-09-15
PROBLEM
I can't get my screen setting above 1024x768 so they look all big and chunky and the screen is horizontally skewed a little to the left (which requires that I use the hard buttons on my physical screen to move the picture a touch to the right everythime I reboot.)

I realise that this is a common problem and I've read the unofficial guide and search the heck out of this forum before posting.

DETAILS

I've configured my two hard driver to triple boot WinXP (for gaming), XANDROS (for convenience and day to day use for now) and Ubuntu64 (for learning and testing out a 64bit OS - seems a shame to have a 64bit cpu and only 32 bit OSes).

I'm running a 19 inch Samsung SyncMaster 913n LCD and an nvidia 6600 pci-e card. It works great in XANDROS and WinXP at 1240x1024 @75 Hz.

I succesfully installed the nvidia 64 drivers in Ubuntu using the apt get etc. It displays the nvidia white and green logo splash screen at start up and tux racer runs nice and fast so I know that 3d is enabled. I also installed the nvidia setting tools but these do not provide for changing resolution: just gama and stuff like that.

So... I tried editing my xorg.conf file and everytime I do and restart Gnome I get a garbagy text red and blue error screen and can only get back to my Gnome desktop by restoring my xorg.conf file thus: cp /var/backups/xorg/xorg.cong.2005-09-16.00:19:45 /etc/X11/xorg.conf  

I've even tried cutting and pasting the setting which work in XANDROS from my xandros xorg.conf file to my Ubuntu64 xorg.conf file. Here they are:



Section "Monitor"
	Identifier	"Monitor1"
	VendorName	"SAM"
	ModelName	"SyncMaster"
	HorizSync	30-81
EndSection

# res 1280 1024
Section "Screen"
	Identifier	"Screen1"
	Device	"Device1"
	Monitor	"Monitor1"
	DefaultDepth	16
	SubSection	"Display"
		Depth	4
		Modes	"1280x1024"	"1152x870"	"1152x864"	"1024x768"	"832x624"	"800x600"	"640x480"
	EndSubSection
	SubSection	"Display"
		Depth	8
		Modes	"1280x1024"	"1152x870"	"1152x864"	"1024x768"	"832x624"	"800x600"	"640x480"
	EndSubSection
	SubSection	"Display"
		Depth	15
		Modes	"1280x1024"	"1152x870"	"1152x864"	"1024x768"	"832x624"	"800x600"	"640x480"
	EndSubSection
	SubSection	"Display"
		Depth	16
		Modes	"1280x1024"	"1152x870"	"1152x864"	"1024x768"	"832x624"	"800x600"	"640x480"
	EndSubSection
	SubSection	"Display"
		Depth	24
		Modes	"1280x1024"	"1152x870"	"1152x864"	"1024x768"	"832x624"	"800x600"	"640x480"
	EndSubSection
	SubSection	"Display"
		Depth	32
		Modes	"1280x1024"	"1152x870"	"1152x864"	"1024x768"	"832x624"	"800x600"	"640x480"
	EndSubSection
EndSection



But even the above which works in XANDROS does NOT work in Ubuntu. When I restart Gnome I get the same command line and typing "startx" just gets me to the same error screen. I realise that XANDROS uses KDE and not GNOME but I don't see anything in the above settings that looks KDE specific.

Here are the settings from Gnome which in Ubuntu64 which work but only allow me to run at a max of 1024x768:


Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-49
	VertRefresh	43-72
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV43 [GeForce 6600]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
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

Is the problem that in Gnome you can't say:

Identifier	"Screen1"
	Device	"Device1"
	Monitor	"Monitor1"
	DefaultDepth	16



Can anyone suggest how I might edit my xorg.conf file? Thanks for any suggestions!

---

### Post by orev on 2005-09-15
I think that you will have to edit in the size of the screen in mm to get appropriate results:

Here is from my conf file:  (Notice the Display Size in mm)

```

Section "Monitor"
	Identifier	"DELL E173FP"
	Option		"DPMS"
	HorizSync	28-49
	VertRefresh	43-72
	DisplaySize	338 273
EndSection
```

AND also some changes here:

```
Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82865G Integrated Graphics Device"
	Monitor		"DELL E173FP"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection
```

Of course, you'll want to change my Dell stuff to your stuff.

I have used this format for xorg.conf in many different hardware setups and always had luck..

Hope it works for you!

---

