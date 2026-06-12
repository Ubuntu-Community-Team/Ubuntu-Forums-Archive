---
title: "Resolution changes when mirroring"
date: 2009-03-02
forum: Hardware
---

### Post by Mr.Carramba on 2009-03-02
Hi,

I run ubuntu 8.10 on thinkpad x200s.
When I dock it on ultrabase and connect second monitor, I mirror screen.
The resolution then is lower than standard. How do I restore to "real" resoliution?

xorg.conf

```
Section "Files"
    ModulePath "/usr/lib/xorg/modules"
    FontPath "/usr/share/fonts/misc/"
    FontPath "/usr/share/fonts/TTF/"
    FontPath "/usr/share/fonts/OTF"
    FontPath "/usr/share/fonts/Type1/"
    FontPath "/usr/share/fonts/100dpi/"
    FontPath "/usr/share/fonts/75dpi/"
    FontPath "/usr/share/fonts/corefonts/"
    FontPath "/usr/share/fonts/mathematica-fonts/"
EndSection

Section "Monitor"
    Identifier "Monitor0"
    VendorName "LEN"
    ModelName "4010"
    Option "DPMS"
    Option "PreferredMode" "1280x800"
EndSection

Section "Monitor"
    Identifier "FakeHDMI-1"
    Option "Ignore" "True"
EndSection

Section "Monitor"
    Identifier "FakeHDMI-2"
    Option "Ignore" "True"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device "Card0"
    Monitor "Monitor0"
    DefaultDepth 24
    SubSection "Display"
        Viewport 0 0
        Depth 24
        Modes "1280x800" "1024x768" "800x600"
        Virtual    1280 1568
    EndSubSection
EndSection

Section "Module"
    Load "dri"
    Load "extmod"
    Load "glx"
    Load "record"
    Load "xtrap"
    Load "dbe"
    Load "freetype"
EndSection

Section "ServerLayout"
    Identifier "X.org Configured"
    Screen 0 "Screen0" 0 0
EndSection

Section "Device"
    Option "DRI"
    Identifier "Card0"
    Driver "intel"
    VendorName "Intel Corporation"
    BoardName "Unknown Board"
    BusID "PCI:0:2:0"
    Option "monitor-HDMI-2" "FakeHDMI-2"
    Option "monitor-HDMI-1" "FakeHDMI-1"
    Option "monitor-LVDS" "Monitor0"
EndSection

```

---

