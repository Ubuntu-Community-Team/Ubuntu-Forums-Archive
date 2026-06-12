---
title: "TV-out in black-and-white!"
date: 2006-02-17
forum: Hardware &amp; Laptops
---

### Post by guano on 2006-02-17
Hello all,

After some time, I managed to get TV-out working in my HP DV-4170 notebook, with a intel 900 Graphics (using driver i810) with 1280x768 resolution (see xorg.conf at the end of msg), but there's one thing: Image is in black and white!!! no colors at all. I tried on more than one TV.. Searching around, one told me it is a drivers problem, I contact Intel and they told me is a problem with the linux distro, since the driver should produce color output. 
BTW, TVStandard is set to PAL-M, since it is default for Brazil.

thanks for help.

```

Section "Device"
	Identifier	"Intel Corporation Intel Default Card"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Device"
	Identifier "LCD_CRT"
	Driver "i810"
	Option "MonitorLayout" "CRT,LFP"
	Screen 0
	BusId "PCI:0:2:0"
EndSection

Section "Device"
	Identifier "CRT"
	Driver "i810"
	Option "MonitorLayout" "CRT,LFP"
	Screen 1
	BusId "PCI:0:2:0"
EndSection

Section "Device"
	Identifier "LCD_TV"
	Driver "i810"
	Option "MonitorLayout" "TV,LFP"
	Screen 0
	BusId "PCI:0:2:0"
EndSection

Section "Device"
	Identifier "TV"
	Driver "i810"
	Option "MonitorLayout" "TV,LFP"
	Option "TVStandard" "PAL-M"
	Option "TVOutFormat" "SVIDEO" # "Composite" or "SVIDEO" or "RBG"
	Option "ConnectedMonitor" "TV" 
	Screen 1
	BusId "PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"LCD"
	Option		"DPMS"
	Modeline	"1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
EndSection

Section "Monitor"
	Identifier	"CRT"
	Option		"DPMS"
EndSection


Section "Monitor"
	Identifier "TV"
	HorizSync	30-50
	VertRefresh 60
EndSection

Section "Screen"
	Identifier	"LCD_CRT"
	Device		"LCD_CRT"
	Monitor		"LCD"
	DefaultDepth	24
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
	Identifier	"LCD_TV"
	Device		"LCD_TV"
	Monitor		"LCD"
	DefaultDepth	24
	Subsection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection
EndSection

Section "Screen"
	Identifier "CRT"
	Device "CRT"
	Monitor "CRT"
	DefaultDepth 24
	Subsection "Display"
		Depth 24
		Modes "1024x768"
	EndSubsection
EndSection

Section "Screen"
	Identifier "TV"
	Device "TV"
	Monitor "TV"
	DefaultDepth 24
	Subsection "Display"
		Depth 24
		Modes "1024x768" "800x600"
	EndSubsection
EndSection

Section "ServerLayout"
	Identifier "LCDandTV"
	Screen 0 "LCD_TV"
	Screen 1 "TV" RightOf "LCD_TV"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "ServerLayout"
	Identifier "LCDandCRT"
	Screen 0 "LCD_CRT"
	Screen 1 "CRT" RightOf "LCD_CRT"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "ServerFlags"
	Option "DefaultServerLayout" "LCDandTV"
#	Option "DefaultServerLayout" "LCDandCRT"
EndSection



```

---

### Post by el3ktro on 2006-02-17
Try playing around with the "TVStandard" and "TVOutFormat" options. For the first, there's PAL-M, PAL-G, PAL-B and a few others, for TVOutFormat there's SVIDEO & COMPOSITE for example.

Tom

---

### Post by guano on 2006-02-17
I tried with all "TVOutFormat" s, without success. I will try some others "PAL-??" options, but I really think it won't make a difference, since standard in Brazil is PAL-M..

---

### Post by guano on 2006-03-05
Hey, guess what! I've upgraded to Dapper last week, and today I remembered to try the tv-out with the new install, and it worked! I have colors now!
Dapper to the rescue!

---

