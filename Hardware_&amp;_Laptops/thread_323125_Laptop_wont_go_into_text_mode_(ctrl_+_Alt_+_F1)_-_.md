---
title: "Laptop wont go into text mode (ctrl + Alt + F1) - screen goes really weird"
date: 2006-12-21
forum: Hardware &amp; Laptops
---

### Post by sideshowb0b on 2006-12-21
I have xubuntu edgy running on a toshiba satellite 310CDT laptop. 

It boots fine into GDM. However when I want to go into text mode (i.e. access the tty terminal by pressing CTRL + ALT + F1) the screen goes really strange. You can see the old gdm login faintly in the background and blobs/clouds of white start to appear until the whole screen is white and then it will fade to black - I swear i'm not on any drugs!

I've tried all the ttys and when I hit the keys to change the screen does flicker a bit. Also I cant return to gdm (CTRL + ALT + F7). Its almost as it the LCD display is not being fed any data and so its just displaying noise of some sort (a bit like a TV out of tune but clouds instead of snow).

It is displaying text during the boot.

I've tried /etc/init.d/gdm stop from xfce and the same thing happens.

It must be that its not switching to the text mode correctly.

Here's my xorg.conf bits

Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        FontPath        "/usr/share/fonts/X11/misc"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
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

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
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
        Identifier      "Chips and Technologies F65555 HiQVPro"
        Driver          "chips"
        BusID           "PCI:0:4:0"
        Option          "UseFBDev"              "true"
EndSection

Section "Monitor"
        Identifier      "LCD Monitor"
        Option          "DPMS"
        HorizSync       28-100
        VertRefresh     43-72
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Chips and Technologies F65555 HiQVPro"
        Monitor         "LCD Monitor"
        DefaultDepth    16
        SubSection "Display"
                Depth           1
                Modes           "800x600"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "800x600"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "800x600"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "800x600"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "800x600"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "800x600"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus" "SendCoreEvents"
        InputDevice     "cursor" "SendCoreEvents"
        InputDevice     "eraser" "SendCoreEvents"
        InputDevice     "Synaptics Touchpad"
EndSection

Section "DRI"
        Mode    0666
EndSection

---

