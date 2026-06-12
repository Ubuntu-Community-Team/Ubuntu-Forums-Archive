---
title: "Monitor Resolution Problem in Ubuntu 8.04 beta"
date: 2008-04-01
forum: Hardware &amp; Laptops
---

### Post by Futureking on 2008-04-01
I am big fan of ubuntu linux. I was using its version 7.10 with wubi. I have 17 inch monitor which can disply 1152x864 @75Hz. In ubuntu 7.10 I was using resoluton 1152x864 @ 75Hz. 

I installed ubuntu 8.04 beta with wubi. But it does not supports resolution at 1152x864. I mean I don't get any option of 1152x864.

I opend the Screen & Graphics and searched for my monitor model. But could not find it. I have Samsung SyncMaster 794MG monitor.

If I play more with monitor resolution then monitor resolution goes beyond to capability of my monitor and nothing displays. Finally I remove ubuntu and reinstall it with wubi.

I want to use ubuntu 8.04 please help



I use 1152x864 in windows. I want to use the same resolution in linux.

---

### Post by a1010100m on 2008-04-07
I have the same problem, but my resolution is 640*480.

I cant change resolution, please help.

---

### Post by Killer Cop on 2008-04-07
Same here, can't change resolution...

---

### Post by BRDoyle on 2008-04-07
Which graphics adapter do you use?

---

### Post by jmcwb on 2008-04-07
Ubuntu 8.04 uses the new Xorg 7.3 which is pretty dumb.  Unfortunately, this means that you will have to manually edit the xorg.conf in /etc/X11 to fix your display.  I had to change mine to add 

Subsection      "Display"
        Modes   "1152x864"
EndSubsection

in the Screen section.  As root (sudo -s), 
cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup

gedit /etc/X11/xorg.conf, scroll down to the Screen section and add the "Display" subsection  as above.   Type ctrl-alt-backspace to restart X, then reset your screen resolution.

I've complained about this to no avail.  They might fix it by final, but I doubt it.

:lolflag:

---

### Post by Futureking on 2008-04-07
..............................................................................................................

---

### Post by BRDoyle on 2008-04-07
Ubuntu prevents login with root by default. To get root access use command 

sudo gedit

---

### Post by Futureking on 2008-04-07
> **jmcwb said:**
> Ubuntu 8.04 uses the new Xorg 7.3 which is pretty dumb.  Unfortunately, this means that you will have to manually edit the xorg.conf in /etc/X11 to fix your display.  I had to change mine to add 

Subsection      "Display"
        Modes   "1152x864"
EndSubsection

in the Screen section.  As root (sudo -s), 
cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup

gedit /etc/X11/xorg.conf, scroll down to the Screen section and add the "Display" subsection  as above.   Type ctrl-alt-backspace to restart X, then reset your screen resolution.

I've complained about this to no avail.  They might fix it by final, but I doubt it.

:lolflag:


This worked for me.. Thank you so much... Problem solved!

Hello members.. Try this solution this worked for me. It may also work for you.:guitar:

---

### Post by hepcat on 2008-06-22
[B]I was going nuts trying to get my Nvidia card to be enabled. Plus higher resolutions for my E70 viewsonic. Finally started over from scratch with an 8.04 install.
This time with a little modification of xconfig file I got it all working fine.

This is my xorg.conf file that works for me... Hope it does for you also.

***************************************************************************

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV44 [GeForce 6200 TurboCache(TM)]"
	Monitor		"Configured Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1280x960"	"1152x864"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1280x960"	"1152x864"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1280x960"	"1152x864"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1280x960"	"1152x864"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1280x960"	"1152x864"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1280x960"	"1152x864"	"1024x768"	"800x600"	"640x480"
	EndSubSection
EndSection
Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection
Section "Module"
	Load		"glx"
EndSection[/B]

---

