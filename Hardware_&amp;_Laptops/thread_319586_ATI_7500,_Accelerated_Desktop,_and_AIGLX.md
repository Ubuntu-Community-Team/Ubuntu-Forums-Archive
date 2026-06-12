---
title: "ATI 7500, Accelerated Desktop, and AIGLX?"
date: 2006-12-15
forum: Hardware &amp; Laptops
---

### Post by talkingwires on 2006-12-15
The other day, I inherited a Dell Latitude laptop with an ATI Radeon 7500 graphics chip. I've been an Ubuntu user for years, but have always used Nvidia hardware. So, this is my first experience with ATI chips.

I am trying to use AIGLX to get an accelerated desktop . Scouring the forums, the 7500 is apparently fully supported by open source drivers, capable of running AIGLX. That as far as the consensus goes. Each tutorial seems to have a different method for getting an accelerated desktop. Most claim the binary driver won't work with such an early chip. Many recommend the "ati" or "radeon" drivers, never mentioning the other, never explaining the difference. Each one has dozens of different configurations for the /etc/X11/xorg.conf file, some recommending obscure AGP settings, others alternating between turning the Composite and DRI extensions on or off. Occasionally, a user logs on to say "I got it working!!1!", never to return to the forum again to explain *exactly* how they did it.

Whiskey. Tango. Foxtrot.

I knew ATI cards were supposed to problematic under Linux, and I didn't *ask* for this laptop, but seriously: this chip is at least five years old. Someone must've figured this out. How can I get a mobile ATI 7500 GPU to work with X, AIGLX, and (be still, my heart!), Compiz?

(Oh, and the system is running Edgy. My others are running Feisty and Dapper, and I can switch if setting this up would be easier on another release.)

---

### Post by elmace on 2006-12-30
I would like to know it too, because I have a ATI Radeon 7500 agp card in my desktop, and I would like to be able to use beryl or compiz.  Thanks in advance.

---

### Post by Jack_The_Ripper on 2006-12-31
Hi!

I have Ati Radeon 7500 32 MB in my IBM T41.
I use AIGLX with Beryl ( I think Beryl is much better than Compiz ).
I post my xorg.conf:

+++++++++++++++

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
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "pl"
        Option          "XkbOptions"    "lv3:ralt_switch"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ExplorerPS/2"
Option "ZAxisMapping" "4 5"
Option "YAxisMapping" "4 5"
Option "XAxisMapping" "6 7"
Option "EmulateWheel" "true"
Option "EmulateWheelButton" "2"
Option "Emulate3Buttons" "true"
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
        Identifier      "ATI Technologies, Inc. Radeon Mobility M7 LW [Radeon Mobility 9000]"
        Driver          "radeon"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. Radeon Mobility M7 LW [Radeon Mobility 9000]"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768"
        EndSubSection
        Option          "RendelAccel" "true"
EndSection

Section "ServerLayout"
        Option "AIGLX" "true"
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

Section "Extensions"
Option "Composite" "Enable"
EndSection


++++++++++++

This works fine with Beryl. I haven't tried Compiz with this configuration.

JTR

---

