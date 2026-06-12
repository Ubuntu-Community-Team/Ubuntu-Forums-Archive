---
title: "Split Screen instead of Mirroring"
date: 2007-04-28
forum: Hardware &amp; Laptops
---

### Post by johntelthorst on 2007-04-28
I've got an Acer TravelMate 2440, I've got a second monitor hooked up to it and after restarting the xserver it was recognized, however, it's mirrored and not a split screen and I would prefer the latter.

xorg.conf:

```
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RC410 [Radeon Xpress 200M]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1280x800"
	EndSubSection
EndSection
```

I'm guessing I need to add some option under the generic monitor, but I don't know what that would be.  Any help would be appreciated.

---

