---
title: "Support in Ubuntu for WXGA?"
date: 2005-11-19
forum: General Help
---

### Post by fontosaurus on 2005-11-19
Alright...here's another one!  The new laptop has a WXGA screen -- 1280 x 800 resolution.  It's looking like, when booting off the Live CD, I can only set screen resolutions of 1024 x 768.  Leaves quite the stretched appearance on graphics.

Is there a way to get WXGA support?

---

### Post by campusloop on 2005-11-19
live cd probably doesn't use the hardware specific drivers for your video card, but once ubuntu is installed most probably you can adjust the screen resolution properly.

---

### Post by fontosaurus on 2005-11-19
Even after getting the full install, I still can't get it to switch to 1280x800 (WXGA).  Any more thoughts?

---

### Post by Bachstelze on 2005-11-19
You have to edit your /etc/X11/xorg.conf file. But it's strange for me it worked just fine even with the Live CD...

If it can help you, here's how mine looks : 

```
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Modeline	"1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon Mobility 9100 U3 (R200 IGP)"
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

```

---

### Post by fontosaurus on 2005-11-19
Okay, still not working, and here's what I've got:

```

Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/CID"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
        Load    "GLcore"
        Load    "i2c"
        Load    "bitmap"
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
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "Emulate3Buttons"       "true"
        Option          "ZAxisMapping"          "4 5"
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
        Identifier      "Intel Corporation Intel Default Card"
        Driver          "i810"
        BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        Modeline        "1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation Intel Default Card"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x800"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "Synaptics Touchpad"
EndSection

Section "DRI"
        Mode    0666
EndSection


```

---

### Post by everdred on 2005-11-20
This isn't very helpful, but Breezy auto-detects my WXGA on both LiveCD and install versions, whereas previous versions wouldn't even offer it as an option. So, if anything, they seem to be improving on that front.

---

### Post by fontosaurus on 2005-11-20
[QUOTE=everdred]This isn't very helpful, but Breezy auto-detects my WXGA on both LiveCD and install versions, whereas previous versions wouldn't even offer it as an option. So, if anything, they seem to be improving on that front.[/QUOTE]

I'm wondering if it doesn't have something to do with my onboard video card.  I've got a new Dell XPS M140, which seems to have the Intel i900.  However, I find it odd that the xorg.conf was able to get the right resolution.
It just doesn't want to put the screen into that resolution.  Is there a way to force-change screen resolution from the command line?  If so, I'll just put it in my .xinitrc file.

---

