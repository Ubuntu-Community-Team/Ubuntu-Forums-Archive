---
title: "cirrus logic GD 5480"
date: 2007-10-15
forum: Hardware &amp; Laptops
---

### Post by tshrinivasan on 2007-10-15
Friends.

I have Cirrus Logic GD 5480 video card.
P III PRocessor.
256 RAM.
Kubuntu 7.04


I get only 800x600 Resolution.

I tried with various monitors.
15" Samtron,LG monotors
19" LG monitor.

I tried with various settings using kde system settings->Display and monitor.

Please help me get 1024x768 Resolution.

Thanks,
T.Shrinivasan.

---

### Post by Jacquesmod on 2007-10-27
I have the same problem with the same hardware configuration.
My monitor is a 19 inch LG 77M
In XP PRO, i get a far better resolution.
The truth is that i am very new in this area.
I just installed UBUNTU 7.04 via WUBI.
It works but my screen resolution is only 600x800
Any help will be appreciated
Jacquesmod:guitar:

---

### Post by Jacquesmod on 2007-10-27
[COLOR="Red"][B]
This is wat i see in xorg[/B][/COLOR]


Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Cirrus Logic GD 5480"
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

---

### Post by metroside on 2008-03-10
I have the same problem with the same graphics card. Since this is the first time I have actually got this computer going, is the card actually capable of producing a higher resolution and if so what was the resolution it produced?

It would be great to move up in the world to a resolution of 1028x768 if this can be done.

---

