---
title: "external monitor with different resolution"
date: 2006-02-09
forum: Hardware &amp; Laptops
---

### Post by MrMinute on 2006-02-09
I bought a MSI S260 laptop which has an Intel 915GM chipset and works great  under Ubuntu beside of one problem: It has an integrated screen with a resolution of 1280x800 and I want to use an external flatpanel with a resolution of 1280x1024. Currently I can use the external flatpanel with 1280x800 only because "system -> preferences -> screen resolution" and "xrandr --query" don't offer me 1280x1024. (of course I can select a lower resolution) I installed [915Resolution]("http://www.geocities.com/stomljen/") but it seems to me it's not needed because "915resolution -l" tells me my prefered resolution is already available. Thus I hope to configure /etc/X11/xorg.conf correctly could be sufficient.

It would be fine for me to use only one panel a time and to switch between them by pressing <function key> + <display key> or so. 

Below is my /etc/X11/xorg.conf without the fonts- and input device-bla-bla.

> 
Section "Device"
	Identifier	"Intel Corporation Intel Default Card"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Standardbildschirm"
	Option		"DPMS"
	Modeline	"1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Intel Default Card"
	Monitor		"Standardbildschirm"
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
		Modes		"1280x800" "1280x1024"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection



Any suggestions are welcome!

---

### Post by MrMinute on 2006-02-12
ok, I found [this]("http://ozlabs.org/~jk/docs/mergefb/") desription of mergefb and tried to configure my xorg.conf respectively but without an noticeable effect. My xorg.conf is following:

```


Section "Device"
	Identifier	"Intel Corporation Intel Default Card (Internal)"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Device"
	Identifier	"Intel Corporation Intel Default Card (External)"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Screen		1
EndSection

Section "Monitor"
	Identifier	"Internal Monitor"
	Option		"DPMS"
	Modeline	"1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
EndSection

Section "Monitor"
	Identifier	"External Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Internal Screen"
	Device		"Intel Corporation Intel Default Card (Internal)"
	Monitor		"Internal Monitor"
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

Section "Screen"
	Identifier	"External Screen"
	Device		"Intel Corporation Intel Default Card (External)"
	Monitor		"External Monitor"
	DefaultDepth	32
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1280x800"
	EndSubSection
	SubSection "Display"
		Depth		32
		Modes		"1280x1024" "1280x800"
	EndSubSection
EndSection

Section "Device"
        Identifier	"Intel Corporation Intel Default Card (Internal)"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Option		"MergedFB" "true"
	Option		"MetaModes" "1280x800-1280x800 1280x800-1280x1024"
	Option		"MergedDPI" "100 100"
EndSection

#Section "ServerLayout"
#	Identifier	"Default Layout"
#	Screen		"Internal Screen"
#	InputDevice	"Generic Keyboard"
#	InputDevice	"Configured Mouse"
#	InputDevice	"Synaptics Touchpad"
#EndSection

Section "DRI"
	Mode	0666
EndSection

```

All help would be appreciated!

---

### Post by rre on 2006-08-08
Hi!

I have the same problem with my samsung x05 with an i810 card. I have also tried to follow the same howto you reference... and found the same problems... the list of available screen resolutions does not include 1280x1024, indeed it only includes the screen resolutions of my laptop tft: 640x480, 800x600 and 1024x768.

After a while playing with the xorg.conf file and outputting the video signal only to the external monitor, I have found how to use my external monitor in 1280x1024. These are the steps I follow:

- Recover my initial xorg.conf, adding 1280x1024 as a new mode in display subsection of the default screen
- Output the video signal only to the external monitor
- Restart X server
- Change the resolution to 1280x1024 (now it appears on the list)

et voilà! Im now using my external tft in 1280x1024. :-)

After doing that I understood what's going on wrong before, the problem is that my xorg.conf file doesn't include modelines for my monitor, so the X server detects automatically the resolutions and frequencies of my monitor via DDC. It seems X server only gets the information of my laptop monitor when it is activated, so the simplest solution is to deactive it and restart X server. Maybe, it is posible to make mergefb works properly including modeline info in the xorg.conf, but I have not tried it.

Hope it helps!

---

### Post by bomaka on 2007-02-23
Could you please be more specific in what line you added to your xorg.conf file, what you did to output the video signal to the external monitor and what exactly you mean by the  following lines:

> It seems X server only gets the information of my laptop monitor when it is activated, so > the simplest solution is to deactive it and restart X server.

Also: What do you do when sometimes you want to use the laptop without external monitor and then again with it.

Last question: Is there any possibility to use dualhead mode, which is no problem with Windows XP? 

Thank you!

---

