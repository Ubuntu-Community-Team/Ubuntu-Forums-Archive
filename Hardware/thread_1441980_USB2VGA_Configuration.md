---
title: "USB2VGA Configuration"
date: 2010-03-29
forum: Hardware
---

### Post by EdwardMorris on 2010-03-29
Hi all,  I'm trying to get my USB2VGA adapter working using the SISUSB driver and having some problem. Using the config below, I got the SIS monitor to turn on, but it turns on starting its own gnome-session and once I move the mouse over, it gets stuck there and I can not bring it back to the main screen. Ideally I would like to have once long extended desktop across my laptop screen, a second monitor and a third monitor via the SIS USB2VGA. I can live with the USB2VGA monitor running its own session and not being a part of the extended desktop, as long as I can move the mouse back and forth. What is even more baffling is that when I hit log off on the USB2VGA's gnome session, it pops the "Are you sure?" dialog on the main screen's gnome-session where the mouse won't return to. Please help!!

```

Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	Screen      1  "Screen1" RightOf "Screen0"
        Screen      2  "Screen[SISUSBVGA]" LeftOf "Screen0"
#        Option         "Xinerama" "on"
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "Files"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "built-ins"
EndSection

Section "Module"
	Load  "glx"
	Load  "record"
	Load  "extmod"
	Load  "dbe"
	Load  "dri2"
	Load  "dri"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Monitor"
	Identifier   "Monitor1"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Device"
	Identifier  "Card0"
	Driver      "intel"
	VendorName  "Intel Corporation"
	BoardName   "Mobile 4 Series Chipset Integrated Graphics Controller"
	BusID       "PCI:0:2:0"
EndSection

Section "Device"
	Identifier  "Card1"
	Driver      "radeon"
	VendorName  "ATI Technologies Inc"
	BoardName   "Mobility Radeon HD 3650"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "Screen1"
	Device     "Card1"
	Monitor    "Monitor1"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection
### SISUSBVGA ###

Section "Device"
    Identifier "Device[SISUSBVGA]"
    VendorName "SiS" # Value does not matter
    BoardName "SiS" # Value does not matter
    Driver "sisusb"
    EndSection

    Section "Monitor"
    Identifier "Monitor[SISUSBVGA]"
    VendorName "Monitor Vendor" # value does not matter
    ModelName "Monitor Model" # value does not matter
    VertRefresh 50-75
    HorizSync 30-90
    EndSection

    Section "Screen"
    Identifier "Screen[SISUSBVGA]"
    Device "Device[SISUSBVGA]"
    Monitor "Monitor[SISUSBVGA]"
    DefaultDepth 24
    SubSection "Display"
        Depth 24
        Modes "1280x1024"
    EndSubSection
    EndSection

```

---

