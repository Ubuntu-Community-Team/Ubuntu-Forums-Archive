---
title: "Two X servers, one on hdmi and the other on vga."
date: 2009-06-24
forum: Hardware
---

### Post by philipJfry on 2009-06-24
Hi

I'm trying to configure xorg.conf to be able to start two X servers. One (HDMI) is connected to my Panasonic PX80 television and the other (VGA) to my HP w2207 monitor.

I want to run XBMC on the televison at the same time I can use the computer with the monitor. XBMC will be controlled by Sony Ericsson phone and the normal keyboard and mouse is used to the oter screen. Below you can see the xorg.conf I've used to test to start the second screen via HDMI (-layout hdmi). It always report "No Screens found" and the X server dies. Is what I'm trying to do possible, what am I doing wrong?

HW
CPU: AMD64 5050e 
Main board: ASUS M2N68-VM, built-in GeForce 7050PV

SW
Ubuntu Jaunty (64-bit)

Thank you!


/etc/X11/xorg.conf

Section "ServerLayout"
    Identifier     "vga"
    Screen      0  "ScreenVGA" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "ServerLayout"
    Identifier     "hdmi"
    Screen      0  "ScreenHDMI" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "ServerLayout"
    Identifier     "hdmivga"
    Screen      0  "ScreenVGA" 0 0
    Screen    1  "ScreenHDMI" RightOf "ScreenVGA"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
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

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "HP w2207"
    HorizSync       24.0 - 82.0
    VertRefresh     48.0 - 76.0
    Option         "DPMS"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "Panasonic-TV"
    HorizSync       15.0 - 68.0
    VertRefresh     23.0 - 61.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7050 PV / NVIDIA nForce 630a"
    BusID          "PCI:0:18:0"
#    Screen        0
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7050 PV / NVIDIA nForce 630a"
    BusID          "PCI:0:18:0"
#    Screen       1
EndSection

Section "Screen"
    Identifier     "ScreenVGA"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "ScreenHDMI"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Serverflags"
    Option "DefaultServerLayout"  "vga"
EndSection

---

### Post by philipJfry on 2009-06-27
anyone?

---

