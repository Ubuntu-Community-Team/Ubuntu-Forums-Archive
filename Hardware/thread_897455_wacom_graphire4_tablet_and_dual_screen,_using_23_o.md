---
title: "wacom graphire4 tablet and dual screen, using 2/3 of one screen, 1/3 of the other"
date: 2008-08-22
forum: Hardware
---

### Post by jonim8or on 2008-08-22
I've installed ubuntu hardy, and overwritten the xorg.conf with the one I used for previous linuxes. I have a dual-screen setup using Xinerama, where my 15"screen is rotated, and my 19" screen is normal. In Dapper this xorg.conf worked fine, but now Graphire4 tablet uses 2/3 of my big screen, and then jumps to 1/3 of my small screen.

On advice of the linuxwacom site I've checked the working of the tablet using xidump. There's no jumping in there. It appears that the left 2/3 of my tablet is mapped to the left 2/3 of my big screen, and the right 1/3 of my tablet is mapped to the right 1/3 of my small screen, leaving 1/3 of my big screen and 2/3 of my small screen unused. 

I doubt the mistake is in my xorg.conf, but I can't think where else it might be (except for a bug in gnome or so)

here's my xorg.conf:
```
Section "Files"
    InputDevices "/dev/gpmdata"
    InputDevices "/dev/input"
    RgbPath "/usr/lib/X11/rgb"
    FontPath 	"/usr/share/fonts/misc:unscaled"
    FontPath 	"/usr/share/fonts/75dpi:unscaled"
    FontPath 	"/usr/share/fonts/100dpi:unscaled"
    FontPath 	"/usr/share/fonts/Type1"
    FontPath 	"/usr/share/fonts/Speedo"
    FontPath 	"/usr/share/fonts/cyrillic"
    FontPath 	"/usr/local/share/fonts"
EndSection

Section "ServerFlags"
    Option "AllowMouseOpenFail" "on"
    Option "Xinerama" "1"
EndSection

Section "Module"
    Load "freetype"
    Load "type1"
    Load "dbe"
    Load "glx"
    Load "extmod"
EndSection

Section "InputDevice"
    Identifier "Keyboard1"
    Driver "kbd"
    Option "Protocol" "Standard"
    Option "XkbModel" "microsoftpro"
    Option "XkbLayout" "us"
    Option "XkbRules" "xfree86"
EndSection

Section "InputDevice"
	Identifier	"Mouse1"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ExplorerPS/2"
	Option		"Emulate3Buttons"	"false"
	Option		"Buttons" "7"
	Option		"ButtonMapping" "1 2 3 6 7"
	Option		"ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
#       Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
        Option          "USB"           "on"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
#       Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
        Option          "USB"           "on"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
#       Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
        Option          "USB"           "on"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "pad"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "pad"
        Option          "USB"           "on"
EndSection

Section "ServerLayout"
    Identifier "Layout[all]"
    InputDevice "Keyboard1" "CoreKeyboard"
    InputDevice "Mouse1" "CorePointer"
    InputDevice "stylus" "SendCoreEvents"
    InputDevice "eraser" "SendCoreEvents"
    InputDevice "cursor" "SendCoreEvents"
    InputDevice "pad"
    Screen 0  "Screen0" 0 0
    Screen 1  "Screen1" RightOf "Screen0"
EndSection

Section "DRI"
    Mode 0660
    Group "video"
EndSection

Section "Extensions"
    EndSection

Section "Monitor"
    # HorizSync source: xconfig, VertRefresh source: xconfig
    Identifier "Monitor0"
    VendorName "Unknown"
    ModelName "CRT-0"
    HorizSync 30.0 - 63.0
    VertRefresh 43.0 - 75.0
    Option "DPMS"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier "Monitor1"
    VendorName "Unknown"
    ModelName "LG FLATRON L1510S"
    
    # Option         "Rotate" "CW"
    HorizSync 31.0 - 63.0
    VertRefresh 56.0 - 75.0
    Option "DPMS"
EndSection

Section "Device"
    Identifier "Videocard0"
    VendorName "NVIDIA Corporation"
    BoardName "GeForce 6200"
    Driver "nvidia"
    Screen 0
    Option "NoLogo" "true"
    BusID "PCI:1:0:0"
EndSection

Section "Device"
    Identifier "Videocard1"
    VendorName "NVIDIA Corporation"
    BoardName "GeForce 6200"
    Driver "nvidia"
    Screen 1
    Option "NoLogo" "true"
    BusID "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier "Screen1"
    Device "Videocard0"
    Monitor "Monitor0"
    DefaultDepth 24
    
    Subsection "Display"
        Depth 24
    EndSubsection
    
    # Option         "TwinView" "1"
    # Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option "metamodes" "CRT-0: 1024x768 +0+0; CRT-0: 800x600 +0+0"
    Option "Rotate" "CW"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device "Videocard1"
    Monitor "Monitor1"
    DefaultDepth 24
    
    Subsection "Display"
        Depth 24
    EndSubsection
    
    # Option         "TwinView" "0"
    Option "metamodes" "CRT-1: 1280x1024 +0+0; CRT-1: 1024x768 +0+0; CRT-1: 800x600 +0+0"
    # Option "Rotate" "CW"
EndSection

```

---

### Post by ogden_freen on 2008-08-27
Same issue, but no answers.
And we aren't alone...
[http://ubuntuforums.org/showthread.php?t=787581]("http://ubuntuforums.org/showthread.php?t=787581")

Has anyone gotten this working?

---

