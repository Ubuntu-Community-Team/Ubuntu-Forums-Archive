---
title: "Laptop VGA out different resolution than main LCD"
date: 2007-05-19
forum: Hardware &amp; Laptops
---

### Post by Migalicious on 2007-05-19
Hello all,

I'm trying to figure out how to make my laptop LCD display one res (1280x800) and have the VGA out display 1024x768 when I use the function buttons to enable the VGA out.

I have a Dell Inspiron 6000 with the Intel 915 chipset for graphics.

Here's the relevant parts of my xorg.conf
```

Section "Device"
        Identifier      "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
        Driver          "i810"
        BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
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

```

---

### Post by veloce on 2007-05-20
> **Migalicious said:**
> Hello all,

I'm trying to figure out how to make my laptop LCD display one res (1280x800) and have the VGA out display 1024x768 when I use the function buttons to enable the VGA out.

I have a Dell Inspiron 6000 with the Intel 915 chipset for graphics.

Here's the relevant parts of my xorg.conf


If you add the "1024x768" resolution to each modes line, what happens when you switch?

You might need to add:

       Option "MonitorLayout" "CRT,LFP"

to your device section.

What you are doing is half way towards a dual screen setup, I'm not sure how much of the dual screen stuff is required for what you want to do.

---

### Post by Sakaishi on 2007-05-25
Hi. I have a similar problem I have a Hp DV1000.  My laptop's monitor backlight stopped working months ago so i use a external lcd monitor. I live in japan, I found a lcd monitor for cheap, 25 bucks.  My laptop monitor is wide screen but my external is standard sized, apparently ubuntu doesn't know this.  it projects the wides screen size on the external lcd monitor.  help me fix this please,  I want linux back.

---

### Post by CyberCr33p on 2007-05-27
Any solution to that problem?

---

### Post by jrial on 2007-05-27
> **Sakaishi said:**
> Hi. I have a similar problem I have a Hp DV1000.  My laptop's monitor backlight stopped working months ago so i use a external lcd monitor. I live in japan, I found a lcd monitor for cheap, 25 bucks.  My laptop monitor is wide screen but my external is standard sized, apparently ubuntu doesn't know this.  it projects the wides screen size on the external lcd monitor.  help me fix this please,  I want linux back.

If the backlight stops working, it's usually the inverter that's broken. You don't need a completely new LCD; just swap out the inverter and you're set to go. It's a little PCB that's usually located somewhere down the bottom of the LCD when you take off the bezel.

However, an inverter costs more than what you're paying for the LCD, so you might want to buy that cheap LCD anyway, but just swap out the inverter (less work and less chances of breaking something).

As for your other problems, I'm sorry to say that I don't have a solution; perhaps somebody else can help you...

---

### Post by veloce on 2007-05-27
I saw on someone else's thread the suggestion to start the machine with the laptop closed.  That particular hardware "concentrated" on the vga out in setting resolutions etc.  YMMV.

---

### Post by pettijok on 2007-12-13
So i am rather new to ubuntu and linux in general and im really having some hard times getting my display on my samsung TFT-LCD LN-T4053H. I am working on a sony fs-660/w laptop (GeForce 6200 Go) with a VGA out. I know this is possible because i had it running in XP and loved it. I have been trying to follow the instructions in many different threads but with no success. 

Something that might be note worthy is my TV i think only supports the resolution of 1360x768 @60hz

Any help would be most welcomed. Thanks!

P.S i know my xorg.conf is a bit messy and i apologies. 






 ```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder3)  Wed Sep 12 14:30:30 PDT 2007

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Wed Sep 12 14:29:35 PDT 2007
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "glx"
    Load           "v4l"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
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
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizScrollDelta" "0"
EndSection

Section "Monitor"
    Identifier     "Failsafe Monitor"
    VendorName     "Generic LCD Display"
    ModelName      "LCD Panel 1280x800"
    HorizSync       31.5 - 50.0
    VertRefresh     56.0 - 65.0
    Gamma           1
    ModeLine       "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
    ModeLine       "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
    ModeLine       "1280x768@60" 80.1 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
    ModeLine       "1280x720@60" 74.5 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
    ModeLine       "1280x800@60" 83.5 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
EndSection

Section "Monitor"

 # 
    Identifier     "monitor1"
    Gamma           1
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Nvidia Default Flat Panel"
    HorizSync       29.0 - 49.0
    VertRefresh     0.0 - 61.0
EndSection

Section "Device"
    Identifier     "Failsafe Device"
    Driver         "nvidia"
    BoardName      "vesa"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device" # 
    Identifier     "device1"
    Driver         "nv"
    BoardName      "vesa"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce Go 6200"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Failsafe Device"
    Monitor        "Failsafe Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Virtual     1280 800
        Depth       24
        Modes      "800x600@60" "1280x768@60" "800x600@56" "1280x720@60" "1280x800@60"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1280x800 +0+0; 800x600@60 +0+0; 800x600@56 +0+0; 1280x720@60 +0+0"
EndSection

```

---

