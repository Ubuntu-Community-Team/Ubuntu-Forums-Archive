---
title: "Dell 9400 dual head"
date: 2006-07-17
forum: Hardware &amp; Laptops
---

### Post by tud on 2006-07-17
Hello,

I have a new Dell 9400 with a Nvidia GeForce Go 7900 GS graphic card.
I would like to use a dual monitor configuration.
1) the lcd laptop monitor (Seiko) 1920x1200
2) an external lcd (Phillips 179S4) monitor connected to vga plug

I tried to configure Twinview but I'm not able to start the external monitor :( ](*,) 

xorg.conf 
```

Section "Device"
    Identifier     "NVIDIA"
    Driver         "nvidia"
    Option         "TwinView" "True"
    Option         "TwinViewOrientation" "RightOf"
    Option         "UseEdidFreqs" "True"
    Option         "ConnectedMonitor" "DFP, CRT"
    Option         "NoLogo" "true"
#    Option         "MetaModes" "1920x1200,1280x1024;1920x1200,NULL"
#    Option         "SecondMonitorHorizSync" "30-82"
#    Option         "SecondMonitorVertRefresh" "36-76"
EndSection

```

```

Xorg.0.log(**) NVIDIA(0): Option "NoLogo" "true"
(**) NVIDIA(0): Option "UseEdidFreqs" "True"
(**) NVIDIA(0): Option "TwinView" "True"
(**) NVIDIA(0): Option "TwinViewOrientation" "RightOf"
(**) NVIDIA(0): Enabling RENDER acceleration
(**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID has been
(**) NVIDIA(0):     enabled on all display devices.
(WW) NVIDIA(0): No TwinView "MetaModes" specified; will fall back to Display
(WW) NVIDIA(0):     SubSection modes.
(**) NVIDIA(0): TwinView enabled
(II) NVIDIA(0): NVIDIA GPU GeForce Go 7900 GS at PCI:1:0:0
(--) NVIDIA(0): VideoRAM: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.71.22.16.13
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce Go 7900 GS at
(--) NVIDIA(0):     PCI:1:0:0:
(--) NVIDIA(0):     Philips 170S4 (CRT-0)
(--) NVIDIA(0):     Seiko (DFP-0)
(--) NVIDIA(0): Philips 170S4 (CRT-0): 400.0 MHz maximum pixel clock
(--) NVIDIA(0): Seiko (DFP-0): 330.0 MHz maximum pixel clock
(--) NVIDIA(0): Seiko (DFP-0): Internal Dual Link LVDS
(II) NVIDIA(0): Assigned Display Devices: CRT-0, DFP-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1920x1200"
(II) NVIDIA(0): Virtual screen size determined to be 1920 x 1200
(--) NVIDIA(0): DPI set to (95, 96); computed from "UseEdidDpi" X config option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.

```

Any hint please?

---

### Post by tud on 2006-07-17
Now with this configuration it's working

xorg.conf
```

Section "Device"
    Identifier     "NVIDIA"
    Driver         "nvidia"
    Option         "TwinView" "1"
    Option         "TwinViewOrientation" "LeftOf"
    Option         "UseEdidFreqs" "True"
    Option         "ConnectedMonitor" "CRT-0, DFP-0"
    Option         "NoLogo" "1"
    Option         "MetaModes" "1280x1024,1920x1200;NULL,1920x1200"
    Option         "NvAGP" "2"
    Option         "RenderAccel" "1"
    Option         "CursorShadow" "1"
    Option         "Coolbits" "1"
    Option         "NoPowerConnectorCheck"
#    Option         "SecondMonitorHorizSync" "30-82"
#    Option         "SecondMonitorVertRefresh" "56-76"
EndSection

```

but I'd like to use the laptop monitor as the "main", I I mean with gnome toolbars which are now on the external monitor.

Any suggestion please?
Thanks

---

