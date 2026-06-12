---
title: "Dual screen FGLRX config not using monitor widescreen mode"
date: 2008-01-12
forum: Hardware &amp; Laptops
---

### Post by rgladwell on 2008-01-12
I've configured my Dell Dimension 5150 running Ubuntu 7.10 (fglrx-8.443.1) with Radeon X600 video card to dual screen. However, my primary, widescreen monitor, an HP L2045w (1680x1050) seems to be stuck on the lower resolution of my secondary monitor (1280x1024) - a Dell 1907FP - and I can't seem to get DRI or enable compiz. Playing with the resolutions in the system-config-display manager does not seem to modify anything.

Please see my xorg.conf:

```
Section "ServerLayout"
    Identifier     "Multihead layout"
    Screen      0  "Screen0" LeftOf "Screen1"
    Screen      1  "Screen1" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    Option        "Xinerama" "on"
    Option        "Clone" "off"
EndSection

Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
EndSection

Section "ServerFlags"
    Option        "AIGLX" "on"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
    Option        "XkbModel" "pc105"
    Option        "XkbLayout" "gb"
EndSection

Section "Monitor"
    Identifier   "Monitor0"
    ModelName    "LCD Panel 1680x1050"
    HorizSync    31.5 - 90.0
    VertRefresh  59.9 - 60.1
    Option        "dpms"
EndSection

Section "Monitor"
    Identifier   "Monitor1"
    VendorName   "Monitor Vendor"
    ModelName    "Dell 1907FP (Analog)"
    HorizSync    30.0 - 81.0
    VertRefresh  56.0 - 76.0
    Option        "dpms"
EndSection

Section "Device"
    Identifier  "Videocard0"
    Driver      "fglrx"
    Option        "OpenGLOverlay" "off"
    Option        "VideoOverlay" "on"
EndSection

Section "Device"
    Identifier  "Videocard1"
    Driver      "fglrx"
    VendorName  "Videocard Vendor"
    BoardName   "ATI Technologies Inc RV380 [Radeon X600 (PCIE)]"
    Option        "OpenGLOverlay" "off"
    Option        "VideoOverlay" "on"
    BusID       "PCI:1:0:0"
    Screen      1
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Videocard0"
    Monitor    "Monitor0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
        Modes    "1680x1050" "1600x1200" "1600x1024" "1440x900" "1400x1050" "1360x768" "1280x1024" "1280x960" "1280x800" "1280x720" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Screen"
    Identifier "Screen1"
    Device     "Videocard1"
    Monitor    "Monitor1"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
        Modes    "1280x1024"
    EndSubSection
EndSection

Section "Extensions"
    Option        "Composite" "Enable"
EndSection
```

If anyone could please advise what I'm doing wrong I would be most grateful.

TIA
Ricardo

---

### Post by overdrank on 2008-01-12
> **rgladwell said:**
> I've configured my Dell Dimension 5150 running Ubuntu 7.10 (fglrx-8.443.1) with Radeon X600 video card to dual screen. However, my primary, widescreen monitor, an HP L2045w (1680x1050) seems to be stuck on the lower resolution of my secondary monitor (1280x1024) - a Dell 1907FP - and I can't seem to get DRI or enable compiz. Playing with the resolutions in the system-config-display manager does not seem to modify anything.

Please see my xorg.conf:

```
Section "ServerLayout"
    Identifier     "Multihead layout"
    Screen      0  "Screen0" LeftOf "Screen1"
    Screen      1  "Screen1" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    Option        "Xinerama" "on"
    Option        "Clone" "off"
EndSection

Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
EndSection

Section "ServerFlags"
    Option        "AIGLX" "on"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
    Option        "XkbModel" "pc105"
    Option        "XkbLayout" "gb"
EndSection

Section "Monitor"
    Identifier   "Monitor0"
    ModelName    "LCD Panel 1680x1050"
    HorizSync    31.5 - 90.0
    VertRefresh  59.9 - 60.1
    Option        "dpms"
EndSection

Section "Monitor"
    Identifier   "Monitor1"
    VendorName   "Monitor Vendor"
    ModelName    "Dell 1907FP (Analog)"
    HorizSync    30.0 - 81.0
    VertRefresh  56.0 - 76.0
    Option        "dpms"
EndSection

Section "Device"
    Identifier  "Videocard0"
    Driver      "fglrx"
    Option        "OpenGLOverlay" "off"
    Option        "VideoOverlay" "on"
EndSection

Section "Device"
    Identifier  "Videocard1"
    Driver      "fglrx"
    VendorName  "Videocard Vendor"
    BoardName   "ATI Technologies Inc RV380 [Radeon X600 (PCIE)]"
    Option        "OpenGLOverlay" "off"
    Option        "VideoOverlay" "on"
    BusID       "PCI:1:0:0"
    Screen      1
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Videocard0"
    Monitor    "Monitor0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
        Modes    "1680x1050" "1600x1200" "1600x1024" "1440x900" "1400x1050" "1360x768" "1280x1024" "1280x960" "1280x800" "1280x720" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Screen"
    Identifier "Screen1"
    Device     "Videocard1"
    Monitor    "Monitor1"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    [COLOR="Red"]    Modes    "1280x1024"[/COLOR]
    EndSubSection
EndSection

Section "Extensions"
    Option        "Composite" "Enable"
EndSection
```

If anyone could please advise what I'm doing wrong I would be most grateful.

TIA
Ricardo

Hi and could it be that you only have that resolution mode in your xorg. I have highlighted your Monitor1 and that is the only mode available.

---

