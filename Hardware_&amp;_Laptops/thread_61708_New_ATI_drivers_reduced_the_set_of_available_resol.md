---
title: "New ATI drivers reduced the set of available resolutions"
date: 2005-09-01
forum: Hardware &amp; Laptops
---

### Post by zaubara on 2005-09-01
Hey there!

I just changed from the original Ubuntu-fglrx-drivers to the official 8.16.20 ones.

Everything is working fine, except for one thing: the available resolutions are broken.

I'd like to use 1280x960 (which i used before with no problems), but now I can only pick standard resolutions like 1280x1024 or 1024x768 with the "Screen Resolution" thingy.

Here's my screen section which looks fine to me :-? 
```
Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon 9800 XT (RV350 NJ)"
	Monitor		"Belinea"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection
```

Any ideas?  :-?
I already tried "sudo dpkg-reconfigure xserver-xorg", but with no luck ...


Thanks a lot for any ideas!

-- edit:

Yargghhh, sorry, I forgot to mention that I own a 9800Pro@XT ... and that I am absolutely clueless :(

---

### Post by zaubara on 2005-09-03
edit:

After quite some time of googling and playing around, I found out that manually adding modelines to the "Monitor"-section worked for me.

I added these lines (I used "gtf 1280 960 85 -x" to get those values) into my xorg.conf:

```
# 1280x960 @ 85.00 Hz (GTF) hsync: 85.68 kHz; pclk: 149.43 MHz
Modeline "1280x960_85.00"  149.43  1280 1376 1512 1744  960 961 964 1008  -HSync +Vsync
```

\\:D/  YARRRR! \\:D/
Bye!

---

