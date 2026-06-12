---
title: "Intel GMA 950 + 1080p TV"
date: 2007-06-16
forum: Hardware &amp; Laptops
---

### Post by verevi on 2007-06-16
I've setup a sweet MythTv* setup, but now that I've got it hooked up to my Vizio GV47L 1080p TV, I can not get a decent resolution. 

When I boot, I believe my resolution is 1280x720.  It cuts off both the top and bottom of the screen. (The VGA-input resolution for the monitor is recommended to be 1360x768, which is why the top is and bottom is cut-off I think).

I'm hooked in via DVI-HDMI. 

According to something I found, the proper modeline is:

```
##  Modeline for 1080p -- 1920x1080_60 for the Vizio GV47L
#    ModeLine "1920x1080_60-GV47L" 148.35 1920 2008 2052 2200 1080 1085 1090 1125 +hsync +vsync
```I've tried using the "i810" driver with 915resolution and the "intel" driver and neither does allow me to get the resolution right.  

Here is my current xorg.conf (with input devices and fonts removed for brevity):

```
Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "vnc"
        Load    "vbe"
EndSection

Section "Device"
        Identifier      "Intel Corporation 82945G/GZ Integrated Graphics Controller"
        Driver          "intel"
        BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
        Identifier      "Vizio GV47L"
        #  Modeline for 1080p -- 1920x1080_60 for the Vizio GV47L
        ModeLine "1920x1080" 148.35 1920 2008 2052 2200 1080 1085 1090 1125 +hsync +vsync
         Option         "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation 82945G/GZ Integrated Graphics Controller"
        Monitor         "Vizio GV47L"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1920x1080"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1920x1080"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1920x1080"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1920x1080"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1920x1080"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1920x1080"
        EndSubSection
        Option "SecurityTypes" "VncAuth"
        Option "UserPasswdVerifier" "VncAuth"
        Option "PasswordFile" "/root/.vnc/passwd"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

Section "DRI"
        Mode    0666
EndSection

```
It seems like using the modeline does nothing.  Even when I try dpkg-reconfigure xserver-xorg, it lets me choose some resolutions, but I don't have an option for 1920x1080 or 1360x768.

Any suggestions would be greatly appreciated--because I'm about to go crazy working with this!  

Thanks for listening.




*(By the way, the MythTv documentation here at help.ubuntu.com is *really* good and makes it very easy.  I'm getting nice HDTV in this small-form factor using the HDHomeRun device hooked up to my network).

---

### Post by anton_pm on 2007-06-22
Try adding this in the Screen section:


Option "ModeValidation" "NoEdidDFPMaxSizeCheck"
Option "ModeValidation" "NoMaxPClkCheck"
Option "ModeValidation" "NoDFPNativeResolutionCheck"

Helped me get 1360x768, as my screens EDID was saying the max was 1280x1024, this forces it to use the res you specify, hopefully!

---

