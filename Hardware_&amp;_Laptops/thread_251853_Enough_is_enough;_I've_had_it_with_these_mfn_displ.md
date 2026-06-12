---
title: "Enough is enough; I've had it with these mfn display settings on this mfn laptop"
date: 2006-09-06
forum: Hardware &amp; Laptops
---

### Post by TommyMann on 2006-09-06
I've done everything here [http://doc.gwos.org/index.php/ChangeResolution](http://doc.gwos.org/index.php/ChangeResolution) that seems logical.

So that now my xorg.conf looks like this under monitor and screen:

Section "Monitor"
	Identifier	"Laptop Monitor"
	Option		"DPMS"
	HorizSync	28-50
	VertRefresh	43-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82852/855GM Integrated Graphics Device"
	Monitor		"Laptop Monitor"
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

But my display is still 1280x768. Everything is still warped and there's no way to change it in display options.

All I want is for the circles to not look like elipses to give my ocd mind peace.

Seriously, I think my laptop is a Decepticon trying to subversively cause me to commit suicide.

---

### Post by encompass on 2006-09-06
Have you tried those same settings with the vesa driver?

---

### Post by TommyMann on 2006-09-06
What's a vesa driver?

---

### Post by azraelx401 on 2006-09-06
question....did you download the 915resolution driver from synaptic?  i have a Dell XPS M140 and my resolution was only showing 800x600 when i first installed Ubuntu but once i downloaded the driver i was back to the normal 1280x800.


Just a tip, I wouldn't go editing anything but the source.list without making sure that there is or isn't a driver for the problem.  you might end up messing other things up.

---

### Post by encompass on 2006-09-06
Vesa is a very basic driver nothing fancy but it may fix your problem...
```
sudo dpkg-reconfigure xserver-xorg
```
Press enter for all defaults except for the monitor set that up they way it should be. and your driver... try setting that up with vesa driver not the intel or what ever driver it is on.

---

### Post by TommyMann on 2006-09-06
Thanks everybody.

The 915Driver has done the trick!

Excellent!

---

### Post by azraelx401 on 2006-09-07
> **TommyMann said:**
> Thanks everybody.

The 915Driver has done the trick!

Excellent!

No problem man, just remember that before you go editing anything to make sure that it just isn't a driver issue.

---

