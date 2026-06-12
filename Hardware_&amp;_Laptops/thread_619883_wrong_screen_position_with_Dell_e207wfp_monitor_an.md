---
title: "wrong screen position with Dell e207wfp monitor and ATI Radeon 9000 using Gutsy"
date: 2007-11-21
forum: Hardware &amp; Laptops
---

### Post by erik00h2o on 2007-11-21
After upgrading from Feisty to Gutsy my screen is now positioned incorrectly for my monitor  the left 1/3 of the monitor is blank and the desktop goes off to the right of the monitor.  Under Feisty, I fixed this problem by using the "xvidtune" utility to determine a custom modeline and entered its output in my xorg.conf file.  With Gutsy however, changes to the modeline do not appear to have any effect on the screen position, and when I try using xvidtune, I get an error "Sorry: You have requested a modeline that is not posxsible, or not supported by your hardware configuration.  I am using a Dell E207WFP at 1680x1050 with a Radeon 9000 card.
My operating modeline (from xvidtune):
  "1680x1050"   146.25   1680 1784 1960 2240   1050 1053 1059 1089 +hsync -vsync

The relevant lines from my xorg.conf file:
Section "Monitor"
	Identifier	"DELL E207WFP"
	Option		"DPMS"
	Modeline	"1680x1050"   147.14   1680 1972 2156 2248   1050 1051 1054 1087
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon RV250 If [Radeon 9000]"
	Monitor		"DELL E207WFP"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1680x1050" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1680x1050" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1680x1050" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1680x1050" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1680x1050" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1680x1050" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection


I have attached output from Xorg.log

Thanks.

---

