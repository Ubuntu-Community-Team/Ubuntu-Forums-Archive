---
title: "ATI X700 and screen flickering"
date: 2005-05-14
forum: Hardware &amp; Laptops
---

### Post by Psy31 on 2005-05-14
Hi all,
 so i've got an Acer Travelmate 8104 WLMi with an X700 128Mo.

I have just install fglrx 8.12.10 from source. X start good but i've got flickering on screen and don't know why  ](*,) 

Here is my xorg.conf :
 ```
Section "Files"
        FontPath        "unix/:7100"                    # local font server
        # if the local font server has problems, we can fall back on these
        FontPath        "/usr/lib/X11/fonts/misc"
        FontPath        "/usr/lib/X11/fonts/cyrillic"
        FontPath        "/usr/lib/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/lib/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/lib/X11/fonts/Type1"
        FontPath        "/usr/lib/X11/fonts/CID"
        FontPath        "/usr/lib/X11/fonts/100dpi"
        FontPath        "/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
        Load    "GLcore"
        Load    "bitmap"
        Load    "dbe"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        #SubSection "extmod"
        #Option "omit xfree86-dga"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "record"
        Load    "type1"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "keyboard"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "fr-latin9"
EndSection


Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "Emulate3Buttons"       "true"
        Option          "ZAxisMapping"          "4 5"
EndSection
Section "InputDevice"
        Identifier  "Synaptics Touchpad"
        Driver      "synaptics"
        Option      "CorePointer"
        Option      "Device" "/dev/psaux"
        Option      "Protocol" "auto-dev"
        Option      "LeftEdge" "1700"
        Option      "RightEdge" "5300"
        Option      "TopEdge" "1700"
        Option      "BottomEdge" "4200"
        Option      "FingerLow" "25"
        Option      "FingerHigh" "30"
        Option      "MaxTapTime" "180"
        Option      "MaxTapMove" "220"
        Option      "VertScrollDelta" "100"
        Option      "MinSpeed" "0.06"
        Option      "MaxSpeed" "0.12"
        Option      "AccelFactor" "0.0010"
        Option      "SHMConfig" "on"
#  Option       "Repeater"      "/dev/ps2mouse"
EndSection


Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon Mobility X700 (RV410)"
        Driver          "fglrx"
        #Option         "MonitorLayout" "LVDS,AUTO"
        Option          "MonitorLayout" "LVDS,STV"
        BusID           "PCI:1:0:0"
        Option          "UseInternalAGPGART"    "no"
        Option          "VideoOverlay"  "on"
        Option          "OpenGLOverlay" "off"
        Option          "DynamicPM"     "true"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
#       HorizSync       28-96
#       VertRefresh     50-75
        #Modeline       "1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. Radeon Mobility X700 (RV410)"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1680x1050" "1280x800" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1680x1050" "1280x800" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1680x1050" "1280x800" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1680x1050" "1280x800" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1680x1050" "1280x800" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1680x1050" "1280x800" "1024x768" "800x600" "640x480"
                #Modes          "1280x1024" "1280x800" "1024x768" "800x600" "640x480"
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

Please help me, i'm gonna be crazy ... for the moment i'm using VESA driver ...  :cry:  :cry: 

Thx 
 - Psy -

---

