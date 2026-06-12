---
title: "nvidia stereo for vuzix vr920 glasses: inconsistent EDID"
date: 2010-10-07
forum: Hardware
---

### Post by jonim8or on 2010-10-07
I am trying to connect my vuzix vr920 glasses as second monitor for lucid.
[IMG]http://dvice.com/pics/vuzix_VR920.jpg[/IMG]
These glasses contain two small LCD's which are controlled using a VGA and an USB connector. Under MS Windows this gives nice 3D results.

I am trying to connect these in linux. I've configured the glasses as my second monitor (separate X screen, no Xinerama). It works fine in 2D. When I put on the glasses I see a nice small Lucid desktop in front of me. But running glxgears in stereo mode does not work.
 In [this post](http://www.mygnu.de/index.php/2009/02/vuzix-vr920-with-linux-and-active-3d-stereo/) somebody manages to get it to work using
```
Option "Stereo" "1"
```
However this option is not supported on my **nVidia Quadro FX 1600m**. Now I am trying stereo option "10", which is nvidia's own stereo mode. I've disabled Composite, because that is not compatible with stereo.
However, still it won't use 3D because of "inconsistent EDID data". 

```

(**) NVIDIA(1): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(1): RGB weight 888
(==) NVIDIA(1): Default visual is TrueColor
(==) NVIDIA(1): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(1): Option "Stereo" "10"
(**) NVIDIA(1): Option "TwinView" "0"
(**) NVIDIA(1): Option "MetaModes" "DFP: 800x600 +0+0"
(**) Oct 07 11:24:34 NVIDIA(1): USB IR emitter stereo requested
(**) Oct 07 11:24:34 NVIDIA(1): Enabling RENDER acceleration
(II) Oct 07 11:24:34 NVIDIA(1): NVIDIA GPU Quadro FX 1600M (G84GL) at PCI:1:0:0 (GPU-0)
(--) Oct 07 11:24:34 NVIDIA(1): Memory: 524288 kBytes
(--) Oct 07 11:24:34 NVIDIA(1): VideoBIOS: 60.84.6a.00.05
(II) Oct 07 11:24:34 NVIDIA(1): Detected PCI Express Link width: 16X
(--) Oct 07 11:24:34 NVIDIA(1): Interlaced video modes are supported on this GPU
(--) Oct 07 11:24:34 NVIDIA(1): Connected display device(s) on Quadro FX 1600M at PCI:1:0:0:
(--) Oct 07 11:24:34 NVIDIA(1):     IWR iWear VR920 (CRT-0)
(--) Oct 07 11:24:34 NVIDIA(1):     Seiko (DFP-0)
(--) Oct 07 11:24:34 NVIDIA(1): IWR iWear VR920 (CRT-0): 400.0 MHz maximum pixel clock
(--) Oct 07 11:24:34 NVIDIA(1): Seiko (DFP-0): 330.0 MHz maximum pixel clock
(--) Oct 07 11:24:34 NVIDIA(1): Seiko (DFP-0): Internal Dual Link LVDS
(WW) Oct 07 11:24:34 NVIDIA(1): Unable to find any NVIDIA 3D Vision Stereo mode timings for
(WW) Oct 07 11:24:34 NVIDIA(1):     use with the EDID of IWR iWear VR920 (CRT-0); NVIDIA 3D
(WW) Oct 07 11:24:34 NVIDIA(1):     Vision Stereo may not function properly. This might happen
(WW) Oct 07 11:24:34 NVIDIA(1):     if no EDID is available for IWR iWear VR920 (CRT-0), or if
(WW) Oct 07 11:24:34 NVIDIA(1):     the NVIDIA 3D Vision Stereo mode timings were invalidated,
(WW) Oct 07 11:24:34 NVIDIA(1):     e.g., if a display port connection lacks adequate
(WW) Oct 07 11:24:34 NVIDIA(1):     bandwidth.
(WW) Oct 07 11:24:34 NVIDIA(1): The EDID for IWR iWear VR920 (CRT-0) contradicts itself: mode
(WW) Oct 07 11:24:34 NVIDIA(1):     "640x480" is specified in the EDID; however, the EDID's
(WW) Oct 07 11:24:34 NVIDIA(1):     valid VertRefresh range (60.000 Hz) would exclude this
(WW) Oct 07 11:24:34 NVIDIA(1):     mode's VertRefresh (63.2 Hz); ignoring VertRefresh check
(WW) Oct 07 11:24:34 NVIDIA(1):     for mode "640x480".
(II) Oct 07 11:24:34 NVIDIA(1): Assigned Display Device: CRT-0
(II) Oct 07 11:24:34 NVIDIA(1): Validated modes:
(II) Oct 07 11:24:34 NVIDIA(1):     "DFP:800x600+0+0"
(II) Oct 07 11:24:34 NVIDIA(1): Virtual screen size determined to be 800 x 600
(--) Oct 07 11:24:34 NVIDIA(1): DPI set to (16, 16); computed from "UseEdidDpi" X config
(--) Oct 07 11:24:34 NVIDIA(1):     option
(==) Oct 07 11:24:34 NVIDIA(1): Disabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) Oct 07 11:24:34 NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
(II) Oct 07 11:24:34 NVIDIA(0): Initialized GPU GART.
(II) Oct 07 11:24:34 NVIDIA(0): Setting mode "DFP:1680x1050_60_0+0+0"
(II) Loading extension NV-GLX


```

Here is my xorg.conf:
```

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
EndSection

Section "Extensions"
    Option "Composite" "Disable"
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
    ModelName      "Seiko"
    HorizSync       30.0 - 75.0
    VertRefresh     60.0
    Option         "DPMS"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "IWR iWear VR920"
    HorizSync       31.0 - 64.0
    VertRefresh     59.0 - 65.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro FX 1600M"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro FX 1600M"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP: 1680x1050_60_0 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP: 800x600 +0+0"
    Option         "Stereo" "10"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

