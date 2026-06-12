---
title: "Hardy Haron Doesn't Recognize My ViewSonic Vx2025 monitor"
date: 2008-08-04
forum: Hardware
---

### Post by kay_Eva on 2008-08-04
Hello, I'm a new Linux user. I have gotten help elsewhere and have properly installed my videocard device drivers in order to have 3d acceleration. However, Ubuntu will not give me the proper resolution.

I have tried nvidia-settings. But the dialogues will not go up pat 640 res. I have a widescreen 1680x1050 monitor LCD Viewsonic and it is not listed. 

So, yeah, basically I could use some help here. I've gotten NV. I've gotten the ones from Nvidia. They work fine. But even if my desktop is *somehow* set as 1680x1050, the actual screen size is only 1/4 of that so it has to pan around the desktop when I move my mouse.

Please is there any way to fix this?

---

### Post by Fire_Chief on 2008-08-04
You could try specifying your monitor in the screens and graphics utility. This is not the recommended approach for Hardy but it works well for me. Open the utility. Note: you may have to add it to the menu or just run ```
sudo displayconfig-gtk
```Specify the display as a Generic LCD monitor 1680x1050 with the widescreen option checked. You will have to restart but that may fix your resolution.

Alternatively and much more tedious...you can specify the refresh rates for your monitor in your xorg.conf file.

Cheers!

---

### Post by kay_Eva on 2008-08-04
Thanks but this is my issue. It would be fine if I could change this value somehow. in other words it already knows I'm at 1680x1050 becasue I have it set to that in the Screen Resolution and my desktop IS 1680x1050 it's just that I can only see 1/4 of that resolution at a time and it pans with my mouse.

[http://img523.imageshack.us/img523/1654/resuh2.png](http://img523.imageshack.us/img523/1654/resuh2.png)

[IMG]http://img523.imageshack.us/img523/1654/resuh2.png[/IMG]

---

### Post by kay_Eva on 2008-08-04
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Generic Keyboard" "CoreKeyboard"
    InputDevice    "Configured Mouse" "CorePointer"
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
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
    VendorName     "Generic LCD Display"
    ModelName      "LCD Panel 1680x1050"
    HorizSync       31.5 - 65.5
    VertRefresh     56.0 - 65.0
    Gamma           1
    ModeLine       "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
    ModeLine       "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
    ModeLine       "1280x768@60" 80.1 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
    ModeLine       "1280x720@60" 74.5 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
    ModeLine       "1280x800@60" 83.5 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
    ModeLine       "1440x900@60" 106.5 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
    ModeLine       "1600x1024@60" 136.4 1600 1704 1872 2144 1024 1025 1028 1060 -hsync +vsync
    ModeLine       "1680x1050@60" 147.1 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
EndSection

Section "Monitor"
    Identifier     "monitor1"
    VendorName     "Plug 'n' Play"
    ModelName      "Plug 'n' Play"
    Gamma           1
    ModeLine       "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "DFP-0"
    HorizSync       31.5 - 65.5
    VertRefresh     56.0 - 65.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    BoardName      "vesa"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "device1"
    Driver         "nvidia"
    BoardName      "VESA driver (generic)"
    BusID          "PCI:2:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8800 GT"
    BusID          "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Virtual     1680 1050
        Depth       24
        Modes      "1680x1050@60" "1600x1024@60" "1440x900@60" "1280x800@60" "1280x720@60" "1280x768@60" "800x600@60" "800x600@56"
    EndSubSection
EndSection

Section "Screen"

	# 
    Identifier     "screen1"
    Device         "device1"
    Monitor        "monitor1"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       24
        Modes      "640x480@60"
    EndSubSection
EndSection

Section "Screen"

# Removed Option "metamodes" "nvidia-auto-select +0+0"
# Removed Option "metamodes" "640x480_60 +0+0"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "nvidia-auto-select +0+0"
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

---

### Post by Fire_Chief on 2008-08-06
The nvidia-settings show the resolution for DFP-0 is set to auto. Also the panning resolution is set to 640x480. I would try setting the resolution manually (if other options are available in the pull down besides auto) and removing the panning resolution or setting it to the full resolution of the screen (1680x1050).

Cheers!

---

