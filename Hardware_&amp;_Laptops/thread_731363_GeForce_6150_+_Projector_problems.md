---
title: "GeForce 6150 + Projector problems"
date: 2008-03-21
forum: Hardware &amp; Laptops
---

### Post by richw on 2008-03-21
I'm trying to get my projector (Infoucs In72) in a better resolution on a Geforce 6150 via DVI.

Everytime Xorg probes the projector, it believes the resolution should be 640x480 and sometimes I can get 800x480.

The projector will downscale the input if required - I've managed to get it to do this under Windows XP (once!). I've never managed on Linux (Fedora 7/8 + Ubuntu 7.04, 7.10).

I'm using nvidia-glx-new driver and my xorg.conf is posted below (along with what I think is relvant bits from my /Xorg.0.log) - I'm trying to specify a resolution + refresh rate manually but its not happening.

Help!

> 
Section "ServerLayout"

        # Uncomment if you have a wacom tablet
        #       InputDevice     "stylus"        "SendCoreEvents"
        #       InputDevice     "cursor"        "SendCoreEvents"
        #       InputDevice     "eraser"        "SendCoreEvents"
    Identifier     "Default Layout"
    Screen      0  "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection


Section "Module"
    Load           "v4l"
    Load           "glx"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "gb"
    Option         "XkbOptions" "lv3:ralt_switch"
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    VendorName     "Generic LCD Display"
    ModelName      "LCD Panel 1440x900"
#    Gamma           1
    Option          "DPMS"
    Option          "UseEdid"   "False"
    # 1440x900 @ 60.00 Hz (GTF) hsync: 55.92 kHz; pclk: 106.47 MHz
    Modeline "1440x900_60.00"  106.47  1440 1520 1672 1904  900 901 904 932  -H$
    DisplaySize     1440 900
EndSection

Section "Device"
    Identifier     "nVidia Corporation C51PV [GeForce 6150]"
    Driver         "nvidia"
    BoardName      "nv"
    Screen          0
    Option         "UseEDID" "False"
    Option         "NoLogo"             "True"
    Option         "AddARGBVisuals"     "True"
    Option         "AddARGBGLXVisuals"  "True"
    Option         "UseEdidFreqs"       "False"
    Option         "ModeValidation" "NoEdidDFPMaxSizeCheck"
    Option         "UseEdidDpi"   "FALSE"
    Option         "DPI"   "96 x 96"

EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation C51PV [GeForce 6150]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1440x900"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1440x900"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1440x900"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1440x900"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1440x900"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1440x900"
    EndSubSection
EndSection


> 
II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Option "UseEDID" "False"
(**) NVIDIA(0): Option "UseEdidFreqs" "False"
(**) NVIDIA(0): Option "UseEdidDpi" "FALSE"
(**) NVIDIA(0): Option "DPI" "96 x 96"
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Option "ModeValidation" "NoEdidDFPMaxSizeCheck"
(**) NVIDIA(0): Enabling RENDER acceleration
(**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID has been
(**) NVIDIA(0):     disabled on all display devices.
(WW) NVIDIA(0): Unrecognized ModeValidation token "NoEdidDFPMaxSizeCheck";
(WW) NVIDIA(0):     ignoring.
(**) NVIDIA(0): Ignoring EDIDs
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(GPU-0): Not probing EDID on DFP-0.
(II) NVIDIA(0): NVIDIA GPU GeForce 6150 (C51) at PCI:0:5:0 (GPU-0)
(--) NVIDIA(0): Memory: 131072 kBytes
(--) NVIDIA(0): VideoBIOS: 05.51.22.26.07
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 6150 at PCI:0:5:0:
(--) NVIDIA(0):     NVIDIA TV Encoder (TV-0)
(--) NVIDIA(0):     DFP-0
(--) NVIDIA(0): NVIDIA TV Encoder (TV-0): 400.0 MHz maximum pixel clock
(--) NVIDIA(0): TV encoder: NVIDIA
(II) NVIDIA(0): Assigned Display Device: DFP-0
(WW) NVIDIA(0): No valid modes for "1440x900"; removing.
(WW) NVIDIA(0):
(WW) NVIDIA(0): Unable to validate any modes; falling back to the default mode
(WW) NVIDIA(0):     "nvidia-auto-select".
(WW) NVIDIA(0):
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 640 x 480
(**) NVIDIA(0): DPI set to (96, 96); computed from "DPI" X config option
(**) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.


---

### Post by pytheas22 on 2008-03-21
Did you try using nvidia's convenient X-configuration GUI?  I think that you can call it with "nvidia-settings"  I haven't had an nvidia card in a while, but I recall this utility being very useful (much more than Fedora or Ubuntu's monitor-configuration GUIs) and requiring little thinking; it's worth a shot if you haven't tried it yet.

---

### Post by richw on 2008-04-27
Just an update incase anyone comes across my thread if they are searching.

It appears there is issues with the Nvidia drivers and EDID. An ATI graphics card's helped me out a lot. Now using Ubuntu 8.04 + ATI offical drivers and now my projector defaults to 1080i...now I need to get it down to 720p :lolflag:

---

