---
title: "27&quot; Dual-DVI with Dual Displays - 5120x1440 pixels."
date: 2013-08-28
forum: Hardware
---

### Post by sami-mattila on 2013-08-28
I finally got it to work.
I'm posting my xorg.conf file for those of you that want to get a working dual display for a HD+ resolution.
This config is for 2 Dell 27" displays with 2560x1440 resolutions on ATI AMD Radeon PRO 6950 card.
I could not get the max resolutions with out the proprietary drivers and even then it took quite a while and a lot of sweat.
You probably have to copy paste this to your own xorg.conf file as a root and reboot.

PS. The monitors have to be identical and use dual-dvi cables.

> Section "ServerLayout"    Identifier     "amdcccle Layout"
    Screen      0  "amdcccle-Screen[1]-0" 0 0
EndSection


Section "Monitor"
    Identifier   "0-DFP17"
    HorizSync    28.0 - 50.0
    VertRefresh  29.0 - 72.0
    ModeLine     "2560x1440" 311.83 2560 2744 3024 3488 1440 1441 1444 1490 -HSync +Vsync
    Option        "VendorName" "DELL"
    Option        "ModelName" "U2713HM - ULTRASHARP"
    Option        "DPMS" "true"
    Option        "PreferredMode" "2560x1440"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
# Tweaked values to get a 30Hz refresh rate to work:
    Option        "ModeDebug" "TRUE"
    Option        "UseEdid" "FALSE"
    Option        "ExactModeTimingsDVI" "True"
    Option        "ModeValidation" "NoDFPNativeResolutionCheck"
EndSection


Section "Monitor"
    Identifier   "0-DFP18"
    HorizSync    28.0 - 50.0
    VertRefresh  29.0 - 72.0
    ModeLine     "2560x1440" 311.83 2560 2744 3024 3488 1440 1441 1444 1490 -HSync +Vsync
    Option        "VendorName" "DELL"
    Option        "ModelName" "U2713HM - ULTRASHARP"
    Option        "DPMS" "true"
    Option        "PreferredMode" "2560x1440"
    Option        "TargetRefresh" "60"
    Option        "Position" "2560 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
# Tweaked values to get a 30Hz refresh rate to work:
    Option        "ModeDebug" "TRUE"
    Option        "UseEdid" "FALSE"
    Option        "ExactModeTimingsDVI" "True"
    Option        "ModeValidation" "NoDFPNativeResolutionCheck"
EndSection


Section "Device"
    Identifier  "amdcccle-Device[1]-0"
    Driver      "fglrx"
    Option        "Monitor-DFP17" "0-DFP17"
    Option        "Monitor-DFP18" "0-DFP18"
    BusID       "PCI:1:0:0"
EndSection


Section "Screen"
    Identifier "amdcccle-Screen[1]-0"
    Device     "amdcccle-Device[1]-0"
    DefaultDepth    24 
    SubSection "Display"
        Viewport   0 0
        Virtual   5120 1440 
        Depth    24 
    EndSubSection
EndSection




---

