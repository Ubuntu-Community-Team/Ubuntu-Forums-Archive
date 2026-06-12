---
title: "nvidia driver started using an imaginary display"
date: 2009-03-04
forum: Hardware
---

### Post by LarsHaugseth on 2009-03-04
I have a PC running Ubuntu 8.04.1 with all the latest updates installed.
It contains an nVidia GeForce 7600 GS graphics card connected to a LCD
(HP 2025 1600x1200) through DVI. The card has two DVI connectors, but
only one is in use.

A couple of weeks ago, some update seem to have broken the nvidia setup
on this PC, so that it thinks there are two displays connected. Sadly
the imaginary one is picked by default and as soon as gdm starts, my
display is entering sleep mode and I can't see a thing.

Here's the relevant part of my /var/log/Xorg.0.log:

 (II) Setting vga for screen 0.
 (II) NVIDIA(0): Creating default Display subsection in Screen section
         "Default Screen" for depth/fbbpp 24/32
 (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
 (==) NVIDIA(0): RGB weight 888
 (==) NVIDIA(0): Default visual is TrueColor
 (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
 (**) NVIDIA(0): Option "NoLogo" "True"
 (**) NVIDIA(0): Enabling RENDER acceleration
 (II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
 (II) NVIDIA(0):     enabled.
 (WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
 (II) NVIDIA(0): NVIDIA GPU GeForce 7600 GS (G73) at PCI:1:0:0 (GPU-0)
 (--) NVIDIA(0): Memory: 262144 kBytes
 (--) NVIDIA(0): VideoBIOS: 05.73.22.25.90
 (II) NVIDIA(0): Detected PCI Express Link width: 8X
 (--) NVIDIA(0): Interlaced video modes are supported on this GPU
 (--) NVIDIA(0): Connected display device(s) on GeForce 7600 GS at PCI:1:0:0:
 (--) NVIDIA(0):     CRT-0
 (--) NVIDIA(0):     HP 2025 (DFP-1)
 (--) NVIDIA(0): CRT-0: 400.0 MHz maximum pixel clock
 (--) NVIDIA(0): HP 2025 (DFP-1): 330.0 MHz maximum pixel clock
 (--) NVIDIA(0): HP 2025 (DFP-1): Internal Dual Link TMDS
 (II) NVIDIA(0): Assigned Display Device: CRT-0
 (==) NVIDIA(0): 
 (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
 (==) NVIDIA(0):     will be used as the requested mode.
 (==) NVIDIA(0): 
 (II) NVIDIA(0): Validated modes:
 (II) NVIDIA(0):     "nvidia-auto-select"
 (II) NVIDIA(0): Virtual screen size determined to be 640 x 480
 (WW) NVIDIA(0): Unable to get display device CRT-0's EDID; cannot compute DPI
 (WW) NVIDIA(0):     from CRT-0's EDID.
 (==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
 (==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.

I have no idea where the CRT-0 comes from. The PC has been hooked up to
the HP 2025 (and only that) for years. I suspect something must have
happened during an update of the nvidia drivers.

I've tried running "nvidia-xconfig" but that didn't help.

Here are links to copies of relevant files:

 /etc/X11/xorg.conf
    [http://www.larshaugseth.com/durin-xorg.conf](http://www.larshaugseth.com/durin-xorg.conf)
 /var/log/Xorg.0.log
    [http://www.larshaugseth.com/durin-xorg.log](http://www.larshaugseth.com/durin-xorg.log)
 /var/log/gdm/:0.log
    [http://www.larshaugseth.com/durin-gdm.log](http://www.larshaugseth.com/durin-gdm.log)

Any ideas on how I can get rid of this problem would be greatly
appreciated.

---

