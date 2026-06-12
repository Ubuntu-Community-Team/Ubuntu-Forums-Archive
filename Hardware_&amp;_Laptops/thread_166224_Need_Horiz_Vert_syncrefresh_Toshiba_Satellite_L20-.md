---
title: "Need Horiz Vert sync/refresh Toshiba Satellite L20-C430"
date: 2006-04-26
forum: Hardware &amp; Laptops
---

### Post by lancest on 2006-04-26
Anybody know? Need to improve 60 Hz refresh in Xorg.conf,Breezy.
I can't find H/V sync and refresh for Toshiba laptop anyplace on internet. 
Breezy, Xorg.conf with glfx (ATI radeon 200m) working.  
Toshiba Satellite L20-C430 (Celeron M processor 380 1.6GHz, 256MB RAM)

---

### Post by Tom Tiger on 2006-04-26
What is wrong?  Why would you want to change the refresh rate of a TFT display?  Or are you working with an external CRT?

---

### Post by lancest on 2006-04-28
Breezy. I can't change resolution higher than 60 Hz! I can't find Toshiba L-20 H/V specs anyplace on internet either.
oshiba Satellite L20-C430 (Celeron M processor 380 1.6GHz. See xorg below



Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Xpress 200M (RC410)"
	Driver		"fglrx"
	BusID		"PCI:1:5:0"
EndSection

Section "Monitor"
        HorizSync       30-80
	Identifier	"Generic Monitor"
	Option		"DPMS"
        VertRefresh     50-85
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon Xpress 200M (RC410)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768_85"
	EndSubSection
EndSection

---

