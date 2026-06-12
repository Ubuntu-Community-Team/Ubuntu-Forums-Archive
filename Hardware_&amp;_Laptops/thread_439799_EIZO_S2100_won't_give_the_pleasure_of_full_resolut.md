---
title: "EIZO S2100 won't give the pleasure of full resolution"
date: 2007-05-11
forum: Hardware &amp; Laptops
---

### Post by Saubazi on 2007-05-11
Bits from Xorg.0.log:

(--) NVIDIA(0): Connected display device(s) on Quadro4 980 XGL at PCI:1:0:0:
(--) NVIDIA(0):     EIZO S2100 (DFP-1)
(--) NVIDIA(0): EIZO S2100 (DFP-1): 165.0 MHz maximum pixel clock
(--) NVIDIA(0): EIZO S2100 (DFP-1): External Single Link TMDS
(II) NVIDIA(0): Assigned Display Device: DFP-1
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 1024 x 768
(--) NVIDIA(0): DPI set to (92, 92); computed from "UseEdidDpi" X config option
(WW) NVIDIA(0): UBB is incompatible with the Composite extension.  Disabling
(WW) NVIDIA(0):     UBB.

I get only 1024x768 out of the screen although it should provide 1600x1200 as native!
What can I do?

---

### Post by Saubazi on 2007-05-11
I tried defining my own modelines but the system seems to be ignoring them.
I tried putting ignoreEDID option to device section. It indeed ignores EDID but gives only 1600x1200 resolution and I get terrible corruption if I run glxgears. It throws pixels all over
the screen and the whole machine may hang up.

I don't know what the problem with my own modelines is so that the machine ignores it and goes to nvidia-autodetect...

Here are bits from xorg.conf

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 63.0
#    Modeline "1600x1200"   162   1600 1664 1856 2160   1200 1201 1204 1250  +hsync +vsync
    Modeline "1280x1024-75"   135   1280 1296 1440 1688   1024 1025 1028 1066  +hsync +vsync
    Modeline "1280x1024-60"   108   1280 1328 1440 1688   1024 1025 1028 1066  +hsync +vsync
    Modeline "1024x768-85"   94.5   1024 1072 1168 1376   768 769 772 808  +hsync +vsync
#    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV28GL [Quadro4 980 XGL]"
    Driver         "nvidia"
    Option         "UseEDIDDpi" "FALSE"
    Option       "DFP" "1"
    Option      "RenderAccel" "1"
    Option      "NvAGP" "1"
#    Option      "NoDDC" "1"
    Option      "NoLogo" "1"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV28GL [Quadro4 980 XGL]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1024x768-85"
    EndSubSection
EndSection

Section "Extensions"
    Option "Composite" "Enable"
EndSection

---

### Post by Saubazi on 2007-05-11
This is the comment about dissing my modelines from Xorg.0.log

(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on Quadro4 980 XGL at PCI:1:0:0:
(--) NVIDIA(0):     EIZO S2100 (DFP-1)
(--) NVIDIA(0): EIZO S2100 (DFP-1): 165.0 MHz maximum pixel clock
(--) NVIDIA(0): EIZO S2100 (DFP-1): External Single Link TMDS
(II) NVIDIA(0): Assigned Display Device: DFP-1
(WW) NVIDIA(0): No valid modes for "1024x768-85"; removing.
(WW) NVIDIA(0): 
(WW) NVIDIA(0): Unable to validate any modes; falling back to the default mode
(WW) NVIDIA(0):     "nvidia-auto-select".
(WW) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 1600 x 1200
(==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
(WW) NVIDIA(0): UBB is incompatible with the Composite extension.  Disabling
(WW) NVIDIA(0):     UBB.
(--) Depth 24 pixmap format is 32 bpp

---

### Post by Saubazi on 2007-05-11
IgnoreEDID seems to be deprecated - there are now three options - ignore valid modes and frequency and stuff like that. Ignoring everything got the custon modelines read.

Only nvidia driver that seems to work is 8776 running on edgy - 9629 gives core dump when asking extensions 9631 throws crappy pixels all over the screen and crashes the machine. Anything older than 8776 won't compile. What a mess.

It's sad that the support on a high end graphics card sucks this bad...I wonder whether I would be better of with SuSe or RH after all when using this one as a CAD workstation...

---

