---
title: "Please help in modifying xorg.conf for second monitor"
date: 2006-12-25
forum: Hardware &amp; Laptops
---

### Post by 1002285 on 2006-12-25
I want to make my Dell laptop send proper signal to the other monitor just by clicking on Fn+F8 - that is Dell's default shortcut for switching etween monitors.
Dell itself is a widescreen laptop with 1280x800 resolution (at least that's currently in xorg.conf) and the other monitor is LG L1952T with 1280x1024 resolution.
When I press Fn+F8, it sends picture with wrong layout to the other monitor.

I understand that the information about the other monitor should somehow be added to xorg.conf. I have even tried, but I don't know how to do it right so I have not succeeded. For example I copied and pasted the "Screen" section and wrote another identifier (nr 1 or 2) and changed resolutions to 1280x1024, but then X just didn't start at all anymore.

The Monitor section (made by the OS install itself) currently looks like this, and this configuration works for the laptops screen:

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
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

---

### Post by dbbolton on 2006-12-25
not sure,but this might help you out 

[http://sourceforge.net/projects/i855crt](http://sourceforge.net/projects/i855crt)

---

### Post by 1002285 on 2006-12-26
> **dbbolton said:**
> not sure,but this might help you out 

[http://sourceforge.net/projects/i855crt](http://sourceforge.net/projects/i855crt)

That seems like difficult and may-be for some other purpose, too.
I only want to know how to write another "screen" (sub)section for the other monitor to xorg.conf. I think this is what needs to be done, but I can't e sure either.

---

