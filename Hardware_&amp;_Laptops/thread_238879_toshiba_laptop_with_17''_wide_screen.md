---
title: "toshiba laptop with 17'' wide screen"
date: 2006-08-18
forum: Hardware &amp; Laptops
---

### Post by sureshot on 2006-08-18
Hello

i am a ubuntu newbie just was wondering cant get 5.10 to reconize my wide screen on my toshiba m65 s9092 laptop it is a tft active matrix 17 inche wide screen with res of 1440 by 900 .. will dapper support this... i am runing solaris but it will not reconize my sound card or my wireless card bummers... 
[http://ubuntuforums.org/images/smilies/eusa_wall.gif](http://ubuntuforums.org/images/smilies/eusa_wall.gif)
Phil

---

### Post by patrickfromspain on 2006-08-18
get the live cd and try ;)

---

### Post by sureshot on 2006-08-18
i already have and i get the same thing i guess i am up the creek on this one 
phi

---

### Post by bcursor on 2006-10-14
I have a Toshiba laptop with an Ati card. The vesa drivers didn't work when I select wide screen resolution. Then I installed fglrx drivers and I added the modes to xorg.conf, that works.

Here is a section from my xorg.conf file

```
Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. Radeon Mobility X700 (RV410 PCIE)"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x1024" "1152x864" "1280x800" "1280x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x1024" "1152x864" "1280x800" "1280x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x1024" "1152x864" "1280x800" "1280x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x1024" "1152x864" "1280x800" "1280x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x1024" "1152x864" "1280x800" "1280x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x1024" "1152x864" "1280x800" "1280x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

---

