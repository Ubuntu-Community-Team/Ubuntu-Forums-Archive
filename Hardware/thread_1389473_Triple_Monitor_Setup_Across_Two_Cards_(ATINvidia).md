---
title: "Triple Monitor Setup Across Two Cards (ATI/Nvidia)"
date: 2010-01-24
forum: Hardware
---

### Post by merrak on 2010-01-24
I have another twist to an issue I've seen quite a bit about (but no existing solutions seem to work). Any insights would be greatly appreciated :)

The question is how to get three monitors to work across two cards. I have 2 out of 3 working now. I have an ATI Radeon HD4350 (PCI Express x16) in which two monitors are attached (one on the DVI port and one on the VGA). This works perfectly (they act as one big desktop). The second card is an older Nvidia GEForce MX4000 (in PCI slot). Attached to it is an older CRT monitor. Ubuntu does not seem to recognize it very well. If I run lspci, then the card is recognized, but the monitor is not recognized at all if I look at the display preferences utility. The best outcome would be if this monitor ran in its own X session  (it is a different resolution than the other two monitors, so I'm actually trying to avoid having a big desktop span across all three).  For what it's worth, the xorg.conf is below

```

# first video card
# second video card
# third video card
#Section "Device"
#	Identifier	"Default Device"
#	Driver	"fglrx"
#EndSection

Section "Monitor"
	Identifier     "Monitor0"
	VendorName     "Acer"
	ModelName      "Acer x223w"
	HorizSync       30.0 - 83.0
	VertRefresh     56.0 - 76.0
EndSection

Section "Monitor"
	Identifier     "Monitor1"
	VendorName     "Acer"
	ModelName      "Acer x223w"
	HorizSync       30.0 - 83.0
	VertRefresh     56.0 - 76.0
	Option	       "RightOf" "Monitor0"
EndSection

Section "Monitor"
	Identifier     "Monitor2"
	VendorName     "NEC"
	ModelName      "MultiSync FE991SB"
	HorizSync       91.2
	VertRefresh     85.2
	Option	       "RightOf" "Monitor1"
EndSection

Section "Screen"
	Identifier	"Screen0"
	DefaultDepth	24
	Monitor		"Monitor0"
	Device		"Videocard0"
	SubSection "Display"
		Depth		24
		Modes		"1680x1050"
		Virtual	3360 1050
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Screen1"
	DefaultDepth	24
	Monitor		"Monitor2"
	Device		"Videocard1"
	SubSection "Display"
		Depth		24
		Modes		"1280x1024"
	EndSubSection
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Extensions"
	Option		"Composite" "Enable"
EndSection

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "Screen0" 0 0
	Screen      1  "Screen1" RightOf "Screen0"
EndSection

Section "Device"
	Identifier     "Videocard0"
	Driver         "fglrx"
	VendorName     "ATI"
	BoardName      "Radeon HD4350"
	BusID          "PCI:1:0:0"
	Screen         0
	Option	       "monitor-DVI-0" "Monitor0"
	Option	       "monitor-VGA-0" "Monitor1"
EndSection

Section "Device"
	Identifier     "Videocard1"
#	Driver         "nvidia"
	Driver	       "xorg"
	VideoRam	   131072
	VendorName     "nvidia"
	BoardName      "GeForceMX4000128"
	BusID          "PCI:5:6:0"
	Screen         1
	Option	       "monitor-VGA-0" "Monitor2"
EndSection

#Section "Device"
#	Identifier     "Videocard2"
#	Driver         "nvidia"
#	VideoRam	   65536
#	VendorName     "nvidia"
#	BoardName      "GeForceMX400064"
#	BusID          "PCI:5:8:0"
#	Screen         2
#EndSection

```

---

### Post by Cain67 on 2010-02-17
am very keen to hear of a solution to this problem.
im currently running 2 monitors from an Nvidia 250 GTS, with a third monitor running from a Ati 9200.

so any help on this topic would be great :D

---

### Post by jeremybender34 on 2010-02-24
I have a triple monitor setup running across two video cards. One monitor is on a onboard Via video card and the other two run off a Nvidia card. The best soultion I have come up with so far is to run the single monitor on the via card as a seperate x screen while running the two nvidia screens in twinview.  This yeilds a single screen upon a single monitor and a single screen stretched across two monitors. The only drawback is that there is no freedom of movement between the two separate x screens. I post my xorg.conf below. I hope this will help you some.


```
18:33:37 PDT 2009

Section "Module"
    Load           "glx"
EndSection

Section "ServerLayout"
    Identifier     "Multihead"
    Screen        0 "Screen0" 0 0 
    Screen	  1 "Screen1" LeftOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "ServerFlags"
    Option        "Multihead"
EndSection

Section "Files"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    Option         "DPMS"
    HorizSync	   30-60
    VertRefresh    50-110
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BusID   	   "PCI:2:0:0"
    Option	   "TwinView" "true"
    Option 	   "SecondMonitorHorizSync" "40-60"
    Option 	   "SecondMonitorVertRefresh" "60-80"
    Option	   "TwinViewOrientation" "LeftOf"
EndSection

Section "Device"
    Identifier	   "Device1"
    Driver         "vesa"
    VendorName     "Via"
    BusID          "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
	Modes      "1024x768
    EndSubSection
EndSection

Section "Screen"
    Identifier	   "Screen1"
    Device         "Device1"
    Monitor	   "Monitor1"
    DefaultDepth   24
    SubSection     "Display"
	Depth      24
	Modes      "1280x960"
    EndSubSection
EndSection

Section "Extensions"
    Option       "Composite" "Enable"
EndSection

```

---

### Post by maadmaxxer on 2010-06-02
I have a similar setup, two screens running off one card (DVI & VGA) using twinview and a tv off a another card that has a HDMI port as a seperate x-screen...

what i really liked about twin view with 2 screens was that the windows used to maximise to the size of the screen, but now a window will maximise across the 2.

i spent hours reading on here and other resources trying to modify my xorg.conf to get twin view across the 3 screens in the same way that twinview worked as before, in effect creating triple view... no such luck :(

if someone could create 'multiview' i would love them forever, they would actually be a hero :D

---

