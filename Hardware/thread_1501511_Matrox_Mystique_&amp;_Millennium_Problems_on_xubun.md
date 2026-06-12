---
title: "Matrox Mystique &amp; Millennium Problems on xubuntu 10.04 LTS"
date: 2010-06-04
forum: Hardware
---

### Post by Badkub on 2010-06-04
Hi, 

Having major problems with my xserver not using mga drivers the computer see's the card but just doesnt use them . it also doesnt give me the option to select a priority driver. pasted below is the content of my xorg.conf file:

Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/cyrillic"
    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/100dpi"
    FontPath     "/usr/share/fonts/X11/75dpi"
    FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath     "built-ins"
EndSection

Section "Module"
    Load  "glx"
    Load  "dri"
    Load  "dri2"
    Load  "record"
    Load  "extmod"
    Load  "dbe"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
    #DisplaySize      380   300    # mm
    Identifier   "Monitor0"
    VendorName   "VSC"
    ModelName    "VX900"
    HorizSync    30.0 - 82.0
    VertRefresh  50.0 - 75.0
    Option        "DPMS"
EndSection

Section "Monitor"
    Identifier   "Monitor1"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "SWcursor"               # [<bool>]
        #Option     "HWcursor"               # [<bool>]
        #Option     "PciRetry"               # [<bool>]
        #Option     "SyncOnGreen"            # [<bool>]
        #Option     "NoAccel"                # [<bool>]
        #Option     "ShowCache"              # [<bool>]
        #Option     "MGASDRAM"               # [<bool>]
        #Option     "ShadowFB"               # [<bool>]
        #Option     "UseFBDev"               # [<bool>]
        #Option     "ColorKey"               # <i>
        #Option     "SetMclk"                # <freq>
        #Option     "OverclockMem"           # [<bool>]
        #Option     "VideoKey"               # <i>
        #Option     "Rotate"                 # [<str>]
        #Option     "TexturedVideo"          # [<bool>]
        #Option     "Crtc2Half"              # [<bool>]
        #Option     "Crtc2Ram"               # <i>
        #Option     "Int10"                  # [<bool>]
        #Option     "AGPMode"                # <i>
        #Option     "AGPSize"                # <i>
        #Option     "DigitalScreen1"         # [<bool>]
        #Option     "DigitalScreen2"         # [<bool>]
        #Option     "TV"                     # [<bool>]
        #Option     "TVStandard"             # [<str>]
        #Option     "CableType"              # [<str>]
        #Option     "NoHal"                  # [<bool>]
        #Option     "SwappedHead"            # [<bool>]
        #Option     "DRI"                    # [<bool>]
        #Option     "MergedFB"               # [<bool>]
        #Option     "Monitor2HSync"          # [<str>]
        #Option     "Monitor2VRefresh"       # [<str>]
        #Option     "Monitor2Position"       # [<str>]
        #Option     "MetaModes"              # [<str>]
        #Option     "OldDmaInit"             # [<bool>]
        #Option     "ForcePciDma"            # [<bool>]
        #Option     "AccelMethod"            # [<str>]
        #Option     "KVM"                    # [<bool>]
    Identifier  "Card0"
    Driver      "mga"
    VendorName  "Matrox Graphics, Inc."
    BoardName   "MGA 1064SG [Mystique]"
    BusID       "PCI:0:8:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "SWcursor"               # [<bool>]
        #Option     "HWcursor"               # [<bool>]
        #Option     "PciRetry"               # [<bool>]
        #Option     "SyncOnGreen"            # [<bool>]
        #Option     "NoAccel"                # [<bool>]
        #Option     "ShowCache"              # [<bool>]
        #Option     "MGASDRAM"               # [<bool>]
        #Option     "ShadowFB"               # [<bool>]
        #Option     "UseFBDev"               # [<bool>]
        #Option     "ColorKey"               # <i>
        #Option     "SetMclk"                # <freq>
        #Option     "OverclockMem"           # [<bool>]
        #Option     "VideoKey"               # <i>
        #Option     "Rotate"                 # [<str>]
        #Option     "TexturedVideo"          # [<bool>]
        #Option     "Crtc2Half"              # [<bool>]
        #Option     "Crtc2Ram"               # <i>
        #Option     "Int10"                  # [<bool>]
        #Option     "AGPMode"                # <i>
        #Option     "AGPSize"                # <i>
        #Option     "DigitalScreen1"         # [<bool>]
        #Option     "DigitalScreen2"         # [<bool>]
        #Option     "TV"                     # [<bool>]
        #Option     "TVStandard"             # [<str>]
        #Option     "CableType"              # [<str>]
        #Option     "NoHal"                  # [<bool>]
        #Option     "SwappedHead"            # [<bool>]
        #Option     "DRI"                    # [<bool>]
        #Option     "MergedFB"               # [<bool>]
        #Option     "Monitor2HSync"          # [<str>]
        #Option     "Monitor2VRefresh"       # [<str>]
        #Option     "Monitor2Position"       # [<str>]
        #Option     "MetaModes"              # [<str>]
        #Option     "OldDmaInit"             # [<bool>]
        #Option     "ForcePciDma"            # [<bool>]
        #Option     "AccelMethod"            # [<str>]
        #Option     "KVM"                    # [<bool>]
    Identifier  "Card1"
    Driver      "mga"
    VendorName  "Matrox Graphics, Inc."
    BoardName   "MGA 2064W [Millennium]"
    BusID       "PCI:0:13:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "Screen1"
    Device     "Card1"
    Monitor    "Monitor1"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Any help would be awesome.

Joey

---

### Post by dino99 on 2010-06-04
the recent kernels deals with X now and most of the old xorg.conf conflict (watch logs for errors, that can help)

maybe you can try renaming xorg.conf for testing without it and rebuilt one with X -configure, or try Nouveau

you can test with the latest packages from this ppa:

[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

[http://www.google.com/search?as_q=matrox%2Blucid&hl=fr&num=10&btnG=Recherche+Google&as_epq=&as_oq=&as_eq=&lr=&cr=&as_ft=i&as_filetype=&as_qdr=m&as_occt=any&as_dt=i&as_sitesearch=&as_rights=&safe=images](http://www.google.com/search?as_q=matrox%2Blucid&hl=fr&num=10&btnG=Recherche+Google&as_epq=&as_oq=&as_eq=&lr=&cr=&as_ft=i&as_filetype=&as_qdr=m&as_occt=any&as_dt=i&as_sitesearch=&as_rights=&safe=images)

---

### Post by Badkub on 2010-06-04
Thanks but I saw that nouveau does not support Matrox cards so still at the orginal issue

---

