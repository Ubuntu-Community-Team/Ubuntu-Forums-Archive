---
title: "Help setting up 3 monitors on 2 video cards"
date: 2008-09-23
forum: General Help
---

### Post by sgtstadanko on 2008-09-23
Hey All,

I am trying to get the following setup running:

1 Nvidia Quadro Dual Head
1 Intel 945 integrated

I have two monitor spanning on the nvidia card no problem but cannot for the life of me get the third monitor plugged into the intel integrated to work.  

Here is my xorg.conf

```
Section "ServerLayout"

	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    Screen      2  "Screen2" RightOf "Screen1"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "glx"
    Load           "dri"
    Load           "v4l"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
EndSection

Section "ServerFlags"
# Removed Option "Xinerama" "true"
    Option         "Xinerama" "1"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection



Section "Monitor"
 # 
    Identifier     "monitor1"
    VendorName     "Unknown"
    ModelName      "HP L1706"
    HorizSync       30.0 - 83.0
    VertRefresh     50.0 - 76.0
    Gamma           1
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "HP L1706"
    HorizSync       30.0 - 83.0
    VertRefresh     50.0 - 76.0
EndSection

Section "Monitor"
    Identifier     "Monitor2"
    VendorName     "Plug 'n' Play"
    ModelName      "Plug 'n' Play"
    Gamma           1
    ModeLine       "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsy
nc
    ModeLine       "640x480@72" 31.5 640 664 704 832 480 489 491 520 -hsync -vsy
nc
    ModeLine       "640x480@75" 31.5 640 656 720 840 480 481 484 500 -hsync -vsy
nc
    ModeLine       "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vs
ync
    ModeLine       "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vs
ync
    ModeLine       "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vs
ync
    ModeLine       "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vs
ync
    ModeLine       "832x624@75" 57.3 832 864 928 1152 624 625 628 667 -hsync -vs
ync
    ModeLine       "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync
 +vsync
    ModeLine       "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -hsync
 -vsync
    ModeLine       "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync
 -vsync
    ModeLine       "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsyn
c +vsync
    ModeLine       "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 
+hsync +vsync
    ModeLine       "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsyn
c +vsync
    ModeLine       "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 
+hsync +vsync
    ModeLine       "1280x960@75" 129.9 1280 1368 1504 1728 960 961 964 1002 -hsy
nc +vsync
    ModeLine       "1400x1050@60" 122.6 1400 1488 1640 1880 1050 1051 1054 1087 
-hsync +vsync
    ModeLine       "1400x1050@75" 155.8 1400 1496 1648 1896 1050 1051 1054 1096 
-hsync +vsync
    ModeLine       "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 
+hsync +vsync
    ModeLine       "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 
+hsync +vsync
    ModeLine       "1792x1344@60" 204.8 1792 1920 2120 2448 1344 1345 1348 1394 
-hsync +vsync
EndSection


Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro NVS 55/280 PCI"
    BusID          "PCI:7:4:0"
    Screen          0
    Option "AddARGBGLXVisuals" "True"
    Option "RenderAccel" "True"
    Option "AllowGLXWithComposite" "True"
    Option "backingstore" "True"
    Option "TripleBuffer" "True"
    Option "DisableGLXRootClipping" "True" 
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro NVS 55/280 PCI"
    BusID          "PCI:7:4:0"
    Screen          1
    Option "AddARGBGLXVisuals" "True"
    Option "RenderAccel" "True"
    Option "AllowGLXWithComposite" "True"
    Option "backingstore" "True"
    Option "TripleBuffer" "True"
    Option "DisableGLXRootClipping" "True"
EndSection

Section "Device" 
    Identifier     "Videocard2"
    Driver         "intel"
    VendorName     "Intel"
    BoardName      "Intel 965"
    BusID          "PCI:0:2:0"
EndSection



Section "Screen"
 # 
    Identifier     "screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "CRT-1: nvidia-auto-select +0+0"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "CRT-0: 1280x1024@60 +0+0; CRT-0: 1280x960@75 +0+
0; CRT-0: 1280x960@60 +0+0; CRT-0: 1280x1024@75 +0+0; CRT-0: 1152x864@75 +0+0; C
RT-0: 1024x768@60 +0+0; CRT-0: 1024x768@70 +0+0; CRT-0: 1024x768@75 +0+0; CRT-0:
 832x624@75 +0+0; CRT-0: 800x600@60 +0+0; CRT-0: 800x600@75 +0+0; CRT-0: 800x600
@72 +0+0; CRT-0: 800x600@56 +0+0; CRT-0: 640x480@75 +0+0; CRT-0: 640x480@72 +0+0
; CRT-0: 640x480@60 +0+0"
EndSection

Section "Screen"
    Identifier     "Screen2"
    Device         "Videocard2"
    Monitor        "Monitor2"
    DefaultDepth    24
    SubSection     "Display"
        Virtual     1792 1344
        Depth       24
        Modes      "1280x1024@60" "1280x960@75" "1280x960@60" "1400x1050@60" "12
80x1024@75" "1400x1050@75" "1152x864@75" "1600x1200@65" "1024x768@60" "1600x1200
@60" "1024x768@70" "1792x1344@60" "1024x768@75" "832x624@75" "800x600@60" "800x6
00@75" "800x600@72" "800x600@56" "640x480@75" "640x480@72" "640x480@60"
    EndSubSection
EndSection


Section "Extensions"
Option "Composite" "Enable"
EndSection

```

I have googled all over the place and removed the Screen paramter from the device section and have tried commenting out the Screen placement in the server layout as it appears that is only valid for dual headed cards.

I turned off Xinerama and now I can get display on the 3rd monitor attached to the Intel card but cannot get mouse or keyboard access and cannot drag mouse over to it.  Also..since xinerama is off i cannot move windows or span desktop.  Is there a way around this?

Any help would be appreciated.

thanks.

---

