---
title: "Got WXGA Working, But..."
date: 2005-11-23
forum: General Help
---

### Post by fontosaurus on 2005-11-23
...I seem to have to re-run the process to get 1280x800 resolution every time I start up the system.  I've tried running dpkg-reconfigure in sudo mode, but to no avail.  Anyone have any thoughts?

---

### Post by hw-tph on 2005-11-23
What does your xorg.conf look like? And what is it you're doing to enable your resolution?

I have an nvidia video chip, but here are some bits from my xorg.conf that may or may not be useful to you:

```
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
	Modeline	"1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV17 [GeForce4 420 Go 32M]"
	Monitor		"Generic Monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection
EndSection
```

Håkan

---

### Post by quietglow on 2005-12-04
Alright, I am having the EXACT same problem you did originally with the same hardware. Please tell me how you solved it!!!

---

