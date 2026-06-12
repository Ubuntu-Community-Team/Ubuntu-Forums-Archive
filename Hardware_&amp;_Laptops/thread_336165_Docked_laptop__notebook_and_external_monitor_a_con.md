---
title: "Docked laptop / notebook and external monitor: a consideration"
date: 2007-01-11
forum: Hardware &amp; Laptops
---

### Post by filippod on 2007-01-11
[SIZE="2"]I noticed several threads about screen resolution (especially with notebooks and external screens) detailing problems I had myself. 
The solution is generally quite straightforward but I'm left with a doubt, so I thought I'd share my experience and make a consideration. 

Maybe someone will want to correct me and / or elaborate further.

First of all: my environment.
[LIST]
[*]Laptops: IBM T42 and X60s - both 1024x768
[*]External monitor: Samsung SyncMaster 960BF - 1280x1024
[*]OS: Ubuntu Edgy 6.10
[/LIST]

**Experiment #1: **T42 + SyncMaster 960BF (with DVI cable)

This was quite smooth. The T42 screen worked out of the box.
Then I docked the T42 and tested the 960BF connected with a DVI cable. 

PROBLEM: The960BF would display resolutions only up to 1024x768. 
SOLUTION: All I had to do was to edit *xorg.conf* and add 1280x1024 to the *Modes* in the *Display* subsections of the *Screen* section:

```

[FONT="Courier New"]Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon Mobility M7 LW [Radeon Mobility 9000]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection
[/FONT]

```


**Experiment #2: **X60s + SyncMaster 960BF (with VGA cable)

Again the laptop screen worked out of the box.
Then I docked the X60s and tested the 960BF connected with a VGA cable (there is no DVI out on the X60s docking station). 

PROBLEM: The960BF would display resolutions only up to 640x480. Adding proper *Modes* in the *Display* subsections of the *Screen* section was not enough.
SOLUTION: I specified proper *HorizSync* and *VertRefresh* values in the *Monitor* section of *xorg.conf*

```

[FONT="Courier New"]Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-81
	VertRefresh	56-75
EndSection[/FONT]

```


**Conclusion / consideration:**

While I was able to solve my problem quite easily in both cases, I'm still left with a doubt.

If I understand it correctly in xorg.conf you can have multiple monitors (*Monitor* section), multiple display adapters (*Device* section) but _apparently you can only associate one monitor to each display adapter (*Screen* section). Is this correct?_

If you really can associate only one monitor to each device, then there is a problem because with a laptop and an external screen you have two monitors used by the same device. The internal and the external monitors will probably have different specs and providing wrong *HorizSync* and *VertRefresh* values can be dangerous. One possibility could be to provide value ranges which are valid both for the internal and the external screen.

It would also appear that with a DVI cable the system is able to determine *HorizSync* and *VertRefresh* itself (or maybe with a DVI cable the default values just work better). 


Any correction or further insight will be greatly appreciated.[/SIZE]

---

### Post by diresu on 2007-01-30
Hi filippod,

Does your posting mean that you have managed to run your x60s with two screens in parallel?

I also have a x60s with Debian etch installed, sitting on a docking station connected to an external monitor (eizo FlexScan S1901).  The external monitor works - but not the laptop screen.  I tried all kind of things to make them work both - ideally showing different windows by using something like Xinerama - but the laptop screen always remains black :(

Best wishes, Dietrich

---

### Post by viz_e on 2007-07-10
Same issue here: blank internal LCD in a IBM T43p while connected to a docking station. Any solutions?

---

### Post by filippod on 2007-07-12
> **diresu said:**
> 
Does your posting mean that you have managed to run your x60s with two screens in parallel?


No, my posting was about using seamlessly one or the other monitor, depending on the need. I never tried to run them in parallel. Sorry.

---

### Post by viz_e on 2007-07-12
I solved my problem, but only with the VGA connection and not the DVI. The following xorg.conf enables the parallel functioning of a T43p (being able to move windows from one screen to the other and running compiz fusion) with docking station and an external monitor.
I hope this can be useful.
```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
        FontPath        "/usr/share/fonts/X11/misc"
        FontPath        "/usr/share/fonts/X11/cyrillic"
        FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/Type1"
        FontPath        "/usr/share/fonts/X11/100dpi"
        FontPath        "/usr/share/fonts/X11/75dpi"
        FontPath        "/usr/share/fonts/X11/misc"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "bitmap"
        Load    "dbe"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
        Option          "XkbOptions"    "lv3:ralt_switch"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
EndSection

Section "Device"
        Identifier      "Generic Video Card"
        Driver          "radeon"
        BusID           "PCI:1:0:0"
# accelration
        Option          "AGPMode" "4"
        Option          "EnablePageFlip" "on"
        Option          "RenderAccel" "on"
        # enable (partial) PowerPlay features
        Option          "DynamicClocks" "on"
        # use bios hot keys on thinkpad (aka fn+f7)
        Option          "BIOSHotkeys" "on"
        # enable radeon specific xinerama
        Option          "MonitorLayout" "LVDS, TMDS"
        Option          "MergedFB" "true"
        Option          "CRT2Position" "LeftOf"
        Option          "CRT2Hsync" "50-75"
        Option          "CRT2VRefresh" "30-82"
        Option          "MetaModes" "1400x1050-1280x1024"
        Option          "MergedNonRectangular" "true"
#       Option          "AddARGBGLXVisuals" "True"
#
        Option "ColorTiling" "on"
        Option "AccelMethod" "XAA"
#       Option "AccelMethod" "EXA"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       30-100
        VertRefresh     50-160
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Card"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1400x1050" "1280x1024"
        EndSubSection
#       Option "AddARGBGLXVisuals" "True"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "Synaptics Touchpad"
        Option          "AIGLX"         "true"
EndSection

Section "DRI"
        Mode    0666
EndSection

```

---

