---
title: "Dual Screens with Ati Card not possible"
date: 2012-03-05
forum: Hardware
---

### Post by achatzb on 2012-03-05
Hello,

I am having a problem with dual screens on my Dell Studio Laptop; with amdcccle I have configured both screens to be ON, but the secondary screen is no use to me - apart from displaying the wallpaper. Activating xinerama helps the issue, but breaks Unity. Is there any way to get a Xinerama like functionality without making Unity impossible to use?

My xorg.conf is as follows, if it helps:

```

Section "ServerLayout"
    Identifier     "amdcccle Layout"
    Screen      0  "amdcccle-Screen[1]-0" 0 0
    Screen         "amdcccle-Screen[1]-1" 1920 432
EndSection

Section "ServerFlags"
    Option        "Xinerama" "off"
EndSection

Section "Monitor"
    Identifier   "0-LVDS"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1366x768"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Monitor"
    Identifier   "0-DFP1"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1920x1200"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Device"
    Identifier  "amdcccle-Device[1]-0"
    Driver      "fglrx"
    Option        "Monitor-DFP1" "0-DFP1"
    BusID       "PCI:1:0:0"
EndSection

Section "Device"
    Identifier  "amdcccle-Device[1]-1"
    Driver      "fglrx"
    Option        "Monitor-LVDS" "0-LVDS"
    BusID       "PCI:1:0:0"
    Screen      1
EndSection

Section "Screen"
    Identifier "Default Screen"
    Device     "Default Video Device"
    SubSection "Display"
        Virtual   3286 1200
    EndSubSection
EndSection

Section "Screen"
    Identifier "amdcccle-Screen[1]-0"
    Device     "amdcccle-Device[1]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "amdcccle-Screen[1]-1"
    Device     "amdcccle-Device[1]-1"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

```

---

### Post by gordintoronto on 2012-03-05
You have some problem with monitors, but you have not told us the exact brand and model of the monitors, or the exact model of the computer. "Dell Studio" is like saying, "IBM PC." There are hundreds of variations.

---

### Post by achatzb on 2012-03-06
Sorry, I thought it might be a general problem with Ati Cards, and there would be some kind of generic solution. 
I have a Dell Studio 1555, the primary screen is a Medion Akoya P56001. The graphics chip I am running on is an Ati Mobility Radon HD 4500 series.

---

### Post by gordintoronto on 2012-03-06
Sorry, I don't know what to suggest. My HP G62 has HD Radeon 4200 graphics, I plugged my TV into the HDMI port, it worked. At the local Uni, I plugged a projector into the VGA port and it worked, once I downgraded the resolution to what the projector supported.

I'm running Ubuntu 11.10 with the FGLRX video driver installed using Additional Drivers. My xorg.conf is minimal:

Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

I don't know what Xinerama is.

---

