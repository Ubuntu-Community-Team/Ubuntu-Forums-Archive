---
title: "Lg 700e Monitor"
date: 2007-07-07
forum: Hardware &amp; Laptops
---

### Post by Balvinder25 on 2007-07-07
hi all,
        ive just purchased a new flashy lg monitor 700e..the prob now is that i cant set the resolution to 1024*768 at a refresh rate of 85 herts..i have read the manual for the monitor but there is nothing there..im currently suing it at 800.600 @ 85 .>but just cant get the option 1024*768 in the screen resolution ..??this is xorg.conf file..


Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	35.5-55.5
	VertRefresh	65.5-85.5

Section "Screen"
	Identifier	"Default Screen"
	Device		"intel i801e"
	Monitor		"Generic Monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"

any help would be appreciated..

thanks..

balvinder

---

