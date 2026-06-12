---
title: "[SOLVED] Twinview when dock, Internal LCD when undock"
date: 2008-08-03
forum: Hardware
---

### Post by Thinh on 2008-08-03
After googling and reading xorg a few times i figure how to setup my external monitor and internal monitor to work with twinview without replacing the xorg when switching from dock to undock. This guide is for nvidia people only as i believe twinview is only supported by nvidia drivers.For Ati you guys have a nice tool Xrandr.

i have a Dell d630 and regular docking station with 2 20" Dell monitors connected to it. Everything works including compiz in dock and undock mode. this xorg will make your twinview kick in when you are dock and internal lcd when you are undock.

Here is the important part of the xorg.

Section "ServerLayout"
    [INDENT]Identifier     "Default Layout"
    Screen      0  "DefaultScreen" 0 0
    InputDevice    "Synaptics Touchpad"[/INDENT]
EndSection

Section "Monitor"
   [INDENT] Identifier     "External"
    VendorName     "Unknown"
    ModelName      "DELL 2005FPW"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 75.0[/INDENT]
EndSection

Section "Device"
   [INDENT] Identifier     "DefaultCard"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro NVS 135M"[/INDENT]
EndSection

Section "Screen"
   [INDENT] Identifier     "DefaultScreen"
    Device         "DefaultCard"
    Monitor        "External"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-1"
   [COLOR="Red"]Option[/COLOR]        "UseDisplayDevice" "DFP-1, CRT"
    [COLOR="Red"]Option[/COLOR]         "metamodes" "DFP-1: nvidia-auto-select +0+0,CRT: nvidia-auto-select +1680+0,DFP-0: nvidia-auto-select +0+0"[/INDENT]
EndSection

Option "UseDisplayDevice"
will tell xorg to use the specify screen if they are available.

Option "Metamodes" 
contains a list viable options. if undock DFP-1 and CRT is unavialable but DFP-0 is available and will be used instead.

this work out great because at any given time i believe you can only have 2 monitor on or maybe it is the limitation of twinview hint twin.

[COLOR="Red"]Note:[/COLOR] nvidia-settings generate the Option "Metamodes" line for twinview. I manually added the DFP-0 for the internal lcd


Anyway hopefully this will help some people out.

:lolflag:

---

