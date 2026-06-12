---
title: "Troubles using external monitor through laptop displayport"
date: 2016-09-17
forum: Hardware
---

### Post by luppoooo on 2016-09-17
[COLOR=#111111][FONT=Ubuntu]Ubuntu 16.04, Acer Predator with Nvidia GeForce 970M.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]My goal is to use the laptop through two external monitors (two Acer G247HYL) with the lid closed. The laptop has one HDMI and one DisplayPort output, and I'm using a simple DP - HDMI converter, as the monitors have no DP input. By booting the system with the HDMI connected, I had no problem using the HDMI output, but I could not get the DP output to work properly.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]When the monitor is connected to the DP, all the UI becomes poorly responsive, rough, "un-smooth". The best I could do was getting the external monitor mirroring the built-in one using Nvidia 361 drivers (still with poor UI response). I have tried many combinations of switching NVIDIA drivers / running nvidia-xconfig/ enabling and disabling the monitor from Nvidia X server settings, all without success.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]The additional drivers tab currently displays the following GPU drivers: Nvidia 358, 361, 364, 367, 370 and the Noveau one.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]This is the current content of /etc/X11/xorg.conf:

[/FONT][/COLOR]```
Section "ServerLayout"    
    Identifier     "layout"
    Screen      0  "nvidia" 0 0
    Inactive       "intel"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection


Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "keyboard"
EndSection


Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection


Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection


Section "Device"
    Identifier     "intel"
    Driver         "modesetting"
    Option         "AccelMethod" "None"
    BusID          "PCI:0@0:2:0"
EndSection


Section "Device"
    Identifier     "nvidia"
    Driver         "nvidia"
    BusID          "PCI:1@0:0:0"
EndSection


Section "Screen"
    Identifier     "intel"
    Device         "intel"
    Monitor        "Monitor0"
EndSection


Section "Screen"
    Identifier     "nvidia"
    Device         "nvidia"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "AllowEmptyInitialConfiguration" "on"
    Option         "IgnoreDisplayDevices" "CRT"
    Option         "ConstrainCursor" "off"
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select"
    EndSubSection

EndSection
```[COLOR=#111111][FONT=Ubuntu]

[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]Any help will be greatly appreciated


[/FONT][/COLOR]

---

### Post by serpent6877 on 2016-10-14
Did you find a solution? This looks to be related to displayport in general. I am using a GTX 980 on a AMD system using Nvidia 367 driver. I have tried 370 as well. The DVI port works fine. The displayport does not however. I can see the monitor plugged in through Nvidia X Server settings. But no matter what I can't get it to activate. If I reboot with the monitor plugged in I get the same symptoms as you do. Sometimes I lose my mouse completely or the display will not come on at all. I have to bootup without the displayport connected then plug it in. 

This worked great on my CentOS 6 machine. Luckily I saved it on a separate drive. Guess Ubuntu isn't the option I had hoped for after all.

---

