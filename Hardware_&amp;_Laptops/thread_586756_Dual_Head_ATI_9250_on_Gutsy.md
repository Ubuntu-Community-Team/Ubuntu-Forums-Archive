---
title: "Dual Head ATI 9250 on Gutsy"
date: 2007-10-22
forum: Hardware &amp; Laptops
---

### Post by DaveEaseman on 2007-10-22
Just upgraded to 7.10 from 7.04 and dual head no longer working. Looked at other posts for this problem but cannot find a solution.

Video card is ATI Radeon 9250. I'm using the open source driver not the ATI fglrx driver. I get the logon screen on the screen attached to the VGA but the screen attached to the DVI port says 'Input Not Supported'. I've tried configuring xorg.conf according to the various posts on this subject, but with no success.

xrandr output shows:-

Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 2560 x 1024
VGA-0 connected 1280x1024+0+0 (normal left inverted right) 377mm x 302mm
   1280x1024      59.9* 
   1280x960       59.9  
   1280x720       59.9  
   800x600        56.2  
   640x480        60.0  
DVI-0 connected 1280x1024+0+0 (normal left inverted right) 377mm x 302mm
   1280x1024      60.0*+   75.0     59.9  
   1280x960       59.9  
   1152x864       75.0     74.8  
   1280x720       59.9  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     66.7     60.0  
   720x400        70.1  
S-video disconnected (normal left inverted right)

This seems to show one screen on top of the other. If I do xrandr --output VGA-0 --right-of DVI-0, then it moves one screen to the left OK, but I'm still left with my left hand screen showing 'Input Not Supported' so the left hand desktop is now hidden!

The screens are identical, Acer AL1916, but xrandr shows more options for the screen connected to the DVI port.

Here's my xorg.conf; it's an edited version of the xorg.conf that was working in 7.04.

Section "Files"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "gb"
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

Section "Monitor"
        Identifier      "Left Monitor"
        HorizSync       28-64
        VertRefresh     43-60
        Option          "DPMS"
EndSection

Section "Monitor"
        Identifier      "Right Monitor"
        HorizSync       28-64
        VertRefresh     43-60
        Option          "DPMS"
EndSection

Section "Device"
        Identifier      "ATI Radeon - Left"
        Driver          "radeon"
        Option          "LVDSBiosNativeMode" "false"
        BusID           "PCI:5:2:0"
EndSection

Section "Device"
        Identifier      "ATI Radeon - Right"
        Driver          "radeon"
        BusID           "PCI:5:2:0"
EndSection

Section "Screen"
        Identifier      "Left Screen"
        Device          "ATI Radeon - Left"
        Monitor         "Left Monitor"
        DefaultDepth    24
        SubSection "Display"
                Viewport        0 0
                Depth           24
                Modes           "1024x768" "800x600"
                Virtual         2560 1024
        EndSubSection
EndSection

Section "DRI"
        Mode    0666
EndSection

Section "ServerLayout"
        Identifier      "Dual ATI"
        Screen          "Left Screen" 0 0
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

Section "Module"
        Load    "i2c"
        Load    "glx"
        Load    "dri"
        Load    "bitmap"
        Load    "ddc"
        Load    "extmod"
        Load    "freetype"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection

Section "Extensions"
        Option      "Composite" "1"
EndSection

---

