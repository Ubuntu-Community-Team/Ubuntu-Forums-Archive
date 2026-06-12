---
title: "Throw screen output to external screen"
date: 2006-07-05
forum: Hardware &amp; Laptops
---

### Post by mr_crimp on 2006-07-05
Hi, 

I have a problem with my external monitor. I would like have my laptop screen output thrown to my external monitor. I have read a lots of different posts about how to get dual monitors to work. But when I put my laptop in my docking station I only want my external monitor to work and I can't find any information about how to do that.

At the moment the screen output are thrown to my external monitor but in a 1024x768 resolution and my external monitor should run 1600x1200.

I have tried to edit my xorg.conf the best way I can but I don't think it's right.

My hardware:
IBM T42 with ATI radeon 7500 32mbyte
20” LCD monitor 1600x1200: Dell UltraSharp 2001FP (See monitor [Specifications]("http://support.dell.com/support/edocs/monitors/2001fp/EN/specs.htm"))
 
Here are some of my xorg:
```
Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility M7 LW [Radeon Mobility 9000]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"External Monitor"
	Option		"DPMS"
	HorizSync 	31-80
	VertRefresh 	56-60
	# V-freq: 60.00 Hz  // h-freq: 74.69 KHz
	Modeline 	"1600x1200" 170.89  1600 1688 1896 2288  1200 1200 1203 1244 
	# V-freq: 57.96 Hz  // h-freq: 72.06 KHz
	Modeline 	"1600x1200" 162.00  1600 1688 1888 2248  1200 1200 1203 1243
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon Mobility M7 LW [Radeon Mobility 9000]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" 
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"External Screen"
	Device		"ATI Technologies, Inc. Radeon Mobility M7 LW [Radeon Mobility 9000]"
	Monitor		"External Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" 
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen	0	"Default Screen"
	Screen	1	"External Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

Please write if you need more information or logs.

I hope someone can help me to get my external monitor to work with the correct resolution. 

Thanks for all help.

---

### Post by jayemef on 2006-07-05
I'm not sure about exact instructions on getting 1600x1200 resolution, but your problem with outputting to an external monitor shouldn't require xorg.conf editing at all, as there should be a key on your laptop's keyboard for doing it. This is generally a combination of the function key (Fn) and one of the F's (on mine it's Fn + F7). This toggles between local monitor, external monitor, and S-video out if you have it, and is a good thing to be aware of if you give presentations off your laptop and need to connect it to a projector. Once you find the appropriate combination, jump though it a few times. One setting will likely output your display on both monitors, while another will only do the external.

Hope that helps.

---

### Post by mr_crimp on 2006-07-06
#2 Thanks for your post. It's not a problem to get the video output from the laptop transfered to my external monitor. That's done automaticly when I place my closed laptop in my docking station and turn it on. The problem is that the external monitor resolution is 1024x768 and not 1600x1200 which it should be. But thanks for your help and concern.

It's a bit strange because in Breezy it just worked perfectly when I added "1600x1200" in the front of my laptop screen resolution in my xorg.conf.

---

