---
title: "External Display with (un-docked)Laptop! Please please help!"
date: 2008-01-31
forum: Hardware &amp; Laptops
---

### Post by Nijmegenaar on 2008-01-31
Hello All,
Am using Ubuntu for over an year now and its really the most brilliant distro I have seen. But now something's driving me crazy here. I want to connect a 22" wide screen LCD display with a max. resolution of 1680x1050@60Hz to the DVI port of my 1280x800 laptop. I have ATI Radeon9700se and am using the fglrx driver. 
I want to use the external display at the max. resolution of 1680x1050 when its connected and the normal LCD of laptop otherwise. 
Till now I was able to get the external working either #1) at 1680x1050 but with only1200x800 being visible?? OR #2)1280x800 with full screen of the external being accessible. 
I  have already tried lot of the tricks and techniques mentioned in this forum and elsewhere but am nowhere close to getting what I want. In XP  these things things seem to be working just straight out. Can somebody please help. Am tied to solve this for the last week but couldn't and I know that there are some very knowledgeable guys out here who should know this. Many thanks in advance. am attaching my xorg.conf below

####
Section "Device"
	Identifier	"ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-81
	VertRefresh	55-76
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1680x1050" "1280x800"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

---

