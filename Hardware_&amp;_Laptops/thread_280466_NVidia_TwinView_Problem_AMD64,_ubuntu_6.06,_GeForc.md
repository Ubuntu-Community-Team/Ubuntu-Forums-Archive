---
title: "NVidia TwinView Problem: AMD64, ubuntu 6.06, GeForce 6800XT"
date: 2006-10-19
forum: Hardware &amp; Laptops
---

### Post by kakyoism on 2006-10-19
Hi All,

Newbie to ubuntu and linux in general..:P
My desktop is as title and I've tried the two
most popular How-To's. They both didn't work for me.
The nVidia driver is succesfully installed, and
Below are my xorg.conf after being edited according
to the How-To's: bolded part is my edit.
-----
Section "Files"
    FontPath    "/usr/share/X11/fonts/misc"
    FontPath    "/usr/share/X11/fonts/cyrillic"
    FontPath    "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath    "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath    "/usr/share/X11/fonts/Type1"
    FontPath    "/usr/share/X11/fonts/100dpi"
    FontPath    "/usr/share/X11/fonts/75dpi"
    # path to defoma fonts
    FontPath    "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
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
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "CoreKeyboard"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc104"
    Option        "XkbLayout"    "us"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"        "/dev/input/mice"
    Option        "Protocol"        "ExplorerPS/2"
    Option        "ZAxisMapping"        "4 5"
    Option        "Emulate3Buttons"    "true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
    Identifier    "NVIDIA Corporation NVIDIA Default Card"
    Driver        "nvidia"
    BusID        "PCI:1:0:0"
    Option "TwinView" "True"
    Option "TwinViewOrientation" "LeftOf"
    Option "UseEdidFreqs" "True"
    Option "Metamodes" "1280x1024,1280x1024; 1280x960,1280x960; 1152x864,1152x864; 1024x768,1024x768; 800x600,800x600; 1280x1024,NULL; 1024x768,NULL"
    Option "ConnectedMonitor" "DFP, DFP"
    Option "UseDisplayDevice" "DFP"
    Option "NoPowerConnectorCheck"
    Option "SecondMonitorHorizSync" "31-82"
    Option "SecondMonitorVertRefresh" "56-76"
    Option "NoTwinViewXineramaInfo"
EndSection

Section "Monitor"
    Identifier    "DTECH9151"
    Option        "DPMS"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "NVIDIA Corporation NVIDIA Default Card"
    Monitor        "DTECH9151"
    DefaultDepth    24
    SubSection "Display"
        Viewport 0 0
        Depth        1
        Modes        "1280x1024" "1280x960" "1152x864" "1024x768" "800x600"
    EndSubSection
    SubSection "Display"
        Viewport 0 0
        Depth        4
        Modes        "1280x1024" "1280x960" "1152x864" "1024x768" "800x600"
    EndSubSection
    SubSection "Display"
        Viewport 0 0
        Depth        8
        Modes        "1280x1024" "1280x960" "1152x864" "1024x768" "800x600"
    EndSubSection
    SubSection "Display"
        Viewport 0 0
        Depth        15
        Modes        "1280x1024" "1280x960" "1152x864" "1024x768" "800x600"
    EndSubSection
    SubSection "Display"
        Viewport 0 0
        Depth        16
        Modes        "1280x1024" "1280x960" "1152x864" "1024x768" "800x600"
    EndSubSection
    SubSection "Display"
        Viewport 0 0
        Depth        24
        Modes        "1280x1024" "1280x960" "1152x864" "1024x768" "800x600"
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen    0 "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice     "stylus" "SendCoreEvents"
    InputDevice     "cursor" "SendCoreEvents"
    InputDevice     "eraser" "SendCoreEvents"
    Option "Xinerama" "Off"
    Option "Clone" "Off"
EndSection

Section "DRI"
    Mode    0666
EndSection
-----

And below is my xorg.conf backup
-----
Section "Files"
    FontPath    "/usr/share/X11/fonts/misc"
    FontPath    "/usr/share/X11/fonts/cyrillic"
    FontPath    "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath    "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath    "/usr/share/X11/fonts/Type1"
    FontPath    "/usr/share/X11/fonts/100dpi"
    FontPath    "/usr/share/X11/fonts/75dpi"
    # path to defoma fonts
    FontPath    "/var/lib/defoma/x- ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
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
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "CoreKeyboard"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc104"
    Option        "XkbLayout"    "us"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"        "/dev/input/mice"
    Option        "Protocol"        "ExplorerPS/2"
    Option        "ZAxisMapping"        "4 5"
    Option        "Emulate3Buttons"    "true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
    Identifier    "NVIDIA Corporation NVIDIA Default Card"
    Driver        "nv"
    BusID        "PCI:1:0:0"
EndSection

Section "Monitor"
    Identifier    "DTECH9151"
    Option        "DPMS"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "NVIDIA Corporation NVIDIA Default Card"
    Monitor        "DTECH9151"
    DefaultDepth    24
    SubSection "Display"
        Depth        1
        Modes        "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x640" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        4
        Modes        "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x640" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        8
        Modes        "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x640" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        15
        Modes        "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x640" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        16
        Modes        "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x640" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        24
        Modes        "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x640" "640x480"
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice     "stylus" "SendCoreEvents"
    InputDevice     "cursor" "SendCoreEvents"
    InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
    Mode    0666
EndSection
-----

After reboot, the right screen is working properly with the nVidia logo visible.
But the left one is completely dark. The official weblink for the left one is
here:[http://www.lge.com/products/model/detail/l1917s_1_6.jhtml](http://www.lge.com/products/model/detail/l1917s_1_6.jhtml)

I don't know if tuning resolution would help but the max reso I could get from the system preference is 1280x1024 instead of the double size said in the How-To's.

I have tried almost everything on the net by even installed core for k7 but it still wouldn't work. Any idea is appreciated.

Beinan

---

