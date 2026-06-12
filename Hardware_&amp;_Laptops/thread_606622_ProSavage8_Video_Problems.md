---
title: "ProSavage8 Video Problems"
date: 2007-11-08
forum: Hardware &amp; Laptops
---

### Post by luismendes on 2007-11-08
Hello, I have an on-board vide card identified as VT8375 [ProSavage8 KM266/KL266]. I'm having some problems with images. Screenshot is attached. Any ideas someone ???

---

### Post by overdrank on 2007-11-09
> **luismendes said:**
> Hello, I have an on-board vide card identified as VT8375 [ProSavage8 KM266/KL266]. I'm having some problems with images. Screenshot is attached. Any ideas someone ???

HI and welcome, you can try and use this command in the terminal ```
gksudo gedit /etc/X11/xorg.conf
``` terminal is located under applications, accessories, terminal. And change your default depth to 16. It will be under screens, Good luck!

---

### Post by luismendes on 2007-11-12
Hi overdrank ! The DefaultDepth is already 16, here's the Screen Section of my xorg.conf :

Section "Screen"
	Identifier	"Default Screen"
	Device		"S3 Inc. VT8375 [ProSavage8 KM266/KL266]"
	Monitor		"710E"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

---

