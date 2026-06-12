---
title: "Windows larger than screen on thinkpad x60"
date: 2008-02-24
forum: Hardware &amp; Laptops
---

### Post by arist0tle on 2008-02-24
I have been searching around for a while and cannot seem to find an answer. When I open up certain applications (Geany, Evolution, Bluefish, etc.) the window of the application is larger than the screen. I usually just '<Alt>F10' it but I am finally just getting annoyed by the problem. Can anyone shoot me a tip or even a good link that would help me troubleshoot this issue. Thanks.

---

### Post by konungursvia on 2008-02-24
Did you try defining only your monitor resolution in xorg.conf, and selecting it in System > Preferences > Screens ?

---

### Post by arist0tle on 2008-02-25
Hey thanks for the response. The resolution in my xorg.conf file is listed correctly. 

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
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
		Modes		"1024x768"
	EndSubSection
EndSection

I tried altering the HorizSynch and VertRefresh (after backing up of course :-) ) but it did not work either.

---

