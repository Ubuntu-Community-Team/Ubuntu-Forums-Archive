---
title: "Samsung 906BW"
date: 2007-04-07
forum: Hardware &amp; Laptops
---

### Post by laytek on 2007-04-07
Hi everyone,

I just purchased a Samsung 906BW monitor to go with my HP Pavilion 753n running Dapper. Optimum screen resolution is 1440 x 900 @ 60Hz. I have edited xorg.conf to look like this:

```
Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
	HorizSync	30-81
	VertRefresh	56-75
	# 1440x900 @ 60.00 Hz (GTF) hsync: 55.92 kHz; pclk: 106.47 MHz
	Modeline "1440x900_60.00"  106.47  1440 1520 1672 1904  900 901 904 932  -HSync +Vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Monitor		"SyncMaster"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1440x900"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

```

System -> Preferences -> Screen Resolution shows my old settings such as 1280x1024, 640x480 and so. The only refresh rate offered is 75 Hz.

Please help - how do I switch to the new resolution?

---

### Post by laytek on 2007-04-12
Does anyone have any thoughts on how to make this work? Does it have to do with the video driver?

LayTek

---

### Post by laytek on 2007-04-20
This problem appears to be too hard for the group. Oh well. I would like to make this work without buying more new hardware. Answer appears to invovle the use of a program called 915resolution, but I have been unable to figure it out yet.

Thanks for trying,
LayTek

---

### Post by laytek on 2007-04-29
I am  pleased to announce that the solution to this problem was very simple, but took two steps.

Step 1: Upgrade from Dapper to Feisty.

Step 2: Install the xserver-xorg-video-intel package (which removes the xserver-xorg-video-i810 package) and run sudo dpkg-reconfigure -phigh xserver-xorg.

I restarted the X server (ctrl-alt-backspace) and I am now looking at a1440 x 900 pretty as you please display.

I hope this helps anybody else that may be experiencing this same problem.

LayTek

---

### Post by sweet_as_an_elf on 2008-01-15
Thanks so much. I'm having the same problem, and I really hope your solution will work. I'll let you know.

---

