---
title: "T30 Screen Resolution"
date: 2008-01-26
forum: Hardware &amp; Laptops
---

### Post by wtfbrb on 2008-01-26
I have searched all the forums and cannot find anything that works.

I am on an IBM T30 and running Gutsy, I cannot get above 1024x768 resolution I have done the  sudo dpkg-reconfigure xserver-xorg


And tried modifying my xorg.conf direclty, but I can't seem to get it.  Here is my current xorg.conf.  

Section "Device"
	Identifier	"ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"T30 LCD"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]"
	Monitor		"T30 LCD"
	DefaultDepth	16
	SubSection "Display"
		Modes		"1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768"
	EndSubSection
EndSection

Thanks in advance,
Mark

---

