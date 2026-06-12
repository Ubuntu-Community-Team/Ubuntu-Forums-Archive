---
title: "Component Out to HDTV"
date: 2007-04-23
forum: Hardware &amp; Laptops
---

### Post by EnderTheThird on 2007-04-23
After building a new computer and spending $250 on HD tuner cards, I'd really like to get MythTV running on my old PC in the living room.  Myth runs GREAT on the new computer and I have no complaints so far.  But I'm running into some trouble with getting the correct resolution output via the component out on my frontend.  I'm using a Gigabyte GeForce 7600 GS on that computer and here's the relevent portion of my xorg.conf:

```

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"TVStandard"	"HD1080i"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	28-84
	Vertrefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1920x1080"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1920x1080"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1920x1080"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1920x1080"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1920x1080"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1920x1080"
	EndSubSection
EndSection

```

At first I thought it was just overscan on my TV's part because I'm missing the top gnome-panel and probably about 1/16th of the screen on both sides (bottom gnome-panel is fine vertically).  I adjusted the height and width settings for my TV, and realized that those parts of the image just weren't being sent to the TV at all with the current output settings.

I've tried messing with the resolution modes in my xorg.conf, but it just defaults to a lower resolution (1024x768 most of the time).  Does anyone have any information I could use to help get this fixed?  Is there any sort of setting in Ubuntu to adjust for 1080i sets or a tool online that could help me figure out the correct resolution?

Thanks in advance

---

### Post by EnderTheThird on 2007-04-23
Any thoughts?  I'm hoping to get to the root of this when I get back home after work today.

---

### Post by Alvinius on 2007-04-23
hope it is ok to post a link to another forum, but there are a lot of experts here [http://www.avsforum.com/](http://www.avsforum.com/)

---

