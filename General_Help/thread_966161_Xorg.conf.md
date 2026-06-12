---
title: "Xorg.conf"
date: 2008-11-01
forum: General Help
---

### Post by wfp on 2008-11-01
So i need to put in my own input. I have never edited xorg.conf before here's what i have so far can some one show me where i have gone wrong.  Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
SubSection "Display"
                Modes   "1280x1024" "1024x768" "640x480"
        EndSubSection
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

---

### Post by mooha on 2008-11-01
This is one of the problems in current ubuntu, no gui to setup xorg. We need something like Yast, it"s opensource anyway.

---

