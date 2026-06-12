---
title: "xorg config - suspend to ram"
date: 2008-05-08
forum: Hardware
---

### Post by mathias__XYZ on 2008-05-08
Laptop: LG LW20 (LCD 1280x800) + external Monitor (19" with 1280x1024)
Pentium M 1,7Ghz


Hello,

I changed from Drapper Drake to Hardy Heron, but my self created xorg.conf (see below) doesn't work any more. The external Monitor have the correct native resolution, but the Laptop-LCD only 1024x768.

I obtain the same error, if I use the Monitor & Display tool from the System Settings.

For a total confusion, if I remove the unnecessary wacom-driver, kdm doesn't work and I have only the command line.

In addition, the first days with Hardy, the suspend to ram works fine but after some updates at Thuesday the supsend to ram fail, i.e. obtain only a black screen and need a cold reboot. I tried the hints from [URL="http://ubuntuforums.org/showthread.php?p=4885412#post4885412[/URL] without success.

Thanks for any help!

```

Section "Files"
  FontPath "/usr/share/X11/fonts/misc"
  FontPath "/usr/share/X11/fonts/cyrillic"
  FontPath "/usr/share/X11/fonts/100dpi/:unscaled"
  FontPath "/usr/share/X11/fonts/75dpi/:unscaled"
  FontPath "/usr/share/X11/fonts/Type1"
  FontPath "/usr/share/X11/fonts/100dpi"
  FontPath "/usr/share/X11/fonts/75dpi"
  # path to defoma fonts
  FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
  Load "bitmap"
  Load "ddc"
  Load "extmod"
  Load "freetype"
  Load "int10"
  Load "type1"
  Load "vbe"
  load "glx"
  load "GLcore"
  load "v4l"
EndSection

Section "InputDevice"
  Identifier "Generic Keyboard"
  Driver "kbd"
  option "CoreKeyboard"
  option "XkbRules" "xorg"
  option "XkbModel" "pc105"
  option "XkbLayout" "de"
  option "XkbVariant" "nodeadkeys"
  option "XkbOptions" "nodeadkeys"
EndSection

Section "InputDevice"
  Identifier "Configured Mouse"
  Driver "mouse"
  option "CorePointer"
  option "Device" "/dev/input/mice"
  option "Protocol" "ExplorerPS/2"
  option "ZAxisMapping" "4 5"
  option "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
  Identifier "Synaptics Touchpad"
  Driver "synaptics"
  option "SendCoreEvents" "true"
  option "Device" "/dev/psaux"
  option "Protocol" "auto-dev"
  option "HorizScrollDelta" "0"
EndSection

Section "InputDevice"
  Driver "wacom"
  Identifier "stylus"
  option "Device" "/dev/wacom"# Change to
  option "Type" "stylus"
  option "ForceDevice" "ISDV4"# Tablet PC ONLY
  # /dev/input/event
  # for USB
EndSection

Section "InputDevice"
  Driver "wacom"
  Identifier "eraser"
  option "Device" "/dev/wacom"# Change to
  option "Type" "eraser"
  option "ForceDevice" "ISDV4"# Tablet PC ONLY
  # /dev/input/event
  # for USB
EndSection

Section "InputDevice"
  Driver "wacom"
  Identifier "cursor"
  option "Device" "/dev/wacom"# Change to
  option "Type" "cursor"
  option "ForceDevice" "ISDV4"# Tablet PC ONLY
  # /dev/input/event
  # for USB
EndSection


Section "Device"
#  identifier "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
  identifier "intel0"
  driver    "i810"
  busid    "PCI:0:2:0"
  Option   "MonitorLayout" "CRT,LFP"   
  screen 0
  Option   "DevicePresence" "true"
#  boardname "Intel 915"
#  vendorname "Intel"
EndSection

Section "Device"
  identifier "intel1"
  driver    "i810"
  busid    "PCI:0:2:0"
  screen 1
  Option   "DevicePresence" "true"
EndSection

Section "Monitor"
  Identifier    "Internal"
  Option   "DPMS

   HorizSync   30-75
   VertRefresh   30-60
#  vendorname "Generic"
#  modelname "Flat Panel 1280x800"
#  HorizSync 31.5-90
#  VertRefresh 60
#  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
#  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
#  modeline  "1600x1024@60" 136.36 1600 1704 1872 2144 1024 1025 1028 1060 -hsync +vsync
#  modeline  "1680x1050@60" 147.14 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
#  modeline  "1920x1200@60" 193.16 1920 2048 2256 2592 1200 1201 1204 1242 -hsync +vsync
  gamma 1.0
EndSection


Section "Monitor"
  Identifier   "ADI"
  Option    "DPMS"
EndSection

Section "Screen"
  Identifier   "builtinlcd"
  Device    "intel0"
  Monitor    "Internal"
  DefaultDepth 24
  SubSection "Display"
   Depth      24
   Modes      "1280x800" 
  EndSubSection
#  SubSection "Display"
#    depth 24
#    modes "1280x768@60" "1600x1024@60" "800x600@60" "1680x1050@60" "1920x1200@60"
#  EndSubSection
#  SubSection   "Display"
#    Modes      "1200x800"
#  EndSubSection
EndSection

Section "Screen"
  Identifier   "externallcd"
  Device    "intel1"
  Monitor    "ADI"
  DefaultDepth   24
  SubSection   "Display"
    Modes      "1280x1024"
  EndSubSection
EndSection


Section "ServerLayout"
  Identifier "Xinerama"
  Screen 0 "builtinlcd" 0 0
  Screen 1 "externallcd" RightOf "builtinlcd"
  InputDevice "Generic Keyboard"
  InputDevice "Configured Mouse"
  InputDevice "stylus" "SendCoreEvents"
  InputDevice "cursor" "SendCoreEvents"
  InputDevice "eraser" "SendCoreEvents"
  InputDevice "Synaptics Touchpad"
  Option "Xinerama" "true"
EndSection
 
Section "DRI"
  Mode 0666
EndSection 

```

---

