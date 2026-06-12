---
title: "Hardware/Xorg Help"
date: 2015-10-09
forum: Hardware
---

### Post by tron2 on 2015-10-09
My monitor/TV (Samsung 4K) has a firmware issue such that it reports the incorrect resolution (1920x1080) when queried by the video card (nVidia GTX750).  The system happily starts in 1920x1080 despite my (attempts at) configuration in xorg.conf to the contrary.  I know it supports the mode because as soon as get to the desktop I can open nVidia Settings click the resolution from "Auto" to "3840x2160" and it works flawlessly until I restart.

xorg-server 2:1.15.1-0ubuntu2.6

Successfull mode change:
```
[    51.093] (II) NVIDIA(0): Setting mode "DPY-3:3840x2160+0+0"

```
Relavent section from xorg.conf (the commented lines are random tries):

```
Section "Screen"

    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "Stereo" "0"
    Option         "nvidiaXineramaInfoOrder" "DFP-2"
    Option         "UseDisplayDevice" "DFP-2"
#    Option         "metamodes" "3840x2160_30 +0+0; nvidia-auto-select +0+0"
#    Option         "metamodes" "3840x2160_30 +0+0"
    Option         "metamodes" "DPY-3:3840x2160+0+0"
    Option         "SLI" "Off"
    Option         "MultiGPU" "Off"
    Option         "BaseMosaic" "off"
#    SubSection     "Display"
#        Depth       24
#    EndSubSection
EndSection
```

What the card seems to actually do:
```

[    13.098] (--) NVIDIA(0): Valid display device(s) on GeForce GTX 750 at PCI:1:0:0
[    13.098] (--) NVIDIA(0):     CRT-0
[    13.098] (--) NVIDIA(0):     DFP-0
[    13.098] (--) NVIDIA(0):     DFP-1
[    13.098] (--) NVIDIA(0):     SAMSUNG (DFP-2) (boot, connected)
[    13.098] (--) NVIDIA(0):     DFP-3
[    13.098] (--) NVIDIA(0): Valid display device(s) on GeForce GTX 750 at PCI:1:0:0
[    13.098] (--) NVIDIA(0):     CRT-0
[    13.098] (--) NVIDIA(0):     DFP-0
[    13.098] (--) NVIDIA(0):     DFP-1
[    13.098] (--) NVIDIA(0):     SAMSUNG (DFP-2) (boot, connected)
[    13.098] (--) NVIDIA(0):     DFP-3
[    13.099] (--) NVIDIA(GPU-0): CRT-0: 400.0 MHz maximum pixel clock
[    13.099] (--) NVIDIA(0): DFP-0: Internal TMDS
[    13.099] (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
[    13.099] (--) NVIDIA(0): DFP-1: Internal TMDS
[    13.099] (--) NVIDIA(GPU-0): DFP-1: 165.0 MHz maximum pixel clock
[    13.099] (--) NVIDIA(0): SAMSUNG (DFP-2): Internal TMDS
[    13.099] (--) NVIDIA(GPU-0): SAMSUNG (DFP-2): 340.0 MHz maximum pixel clock
[    13.099] (--) NVIDIA(0): DFP-3: Internal DisplayPort
[    13.099] (--) NVIDIA(GPU-0): DFP-3: 960.0 MHz maximum pixel clock
[    13.099] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    13.099] (**) NVIDIA(0):     device SAMSUNG (DFP-2) (Using EDID frequencies has been
[    13.099] (**) NVIDIA(0):     enabled on all display devices.)
[    13.102] (II) NVIDIA(0): Validated MetaModes:
[    13.102] (II) NVIDIA(0):     "DPY-3:3840x2160+0+0"
[    13.102] (II) NVIDIA(0): Virtual screen size determined to be 3840 x 2160
[    13.128] (++) NVIDIA(0): DPI set to (70, 70); computed from -dpi X commandline option
[    13.128] (--) Depth 24 pixmap format is 32 bpp
[    13.128] (II) NVIDIA: Using 3072.00 MB of virtual memory for indirect memory
[    13.128] (II) NVIDIA:     access.
[    13.141] (II) NVIDIA(0): Setting mode "DPY-3:3840x2160+0+0"

```
The setting mode is a big fat lie in this case because just .6 sec later
```

[    13.786] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    13.786] (**) NVIDIA(0):     device SAMSUNG (DFP-2) (Using EDID frequencies has been
[    13.786] (**) NVIDIA(0):     enabled on all display devices.)
[    13.951] (II) NVIDIA(0): Setting mode "NULL"
[    14.072] (II) NVIDIA(0): Setting mode "HDMI-0: nvidia-auto-select @1920x1080 +0+0 {ViewPortIn=1920x1080, ViewPortOut
=1920x1080+0+0}"

```

I used to think I wasn't dumb, but I've been poking at this problem for 6 months now . . .

---

### Post by tgalati4 on 2015-10-09
Welcome to the forums.

Understand that with a 4K display, not only do you need enough video RAM to paint 4K resolution worth of pixels in 2D mode, but you also need enough video RAM to hold the 3D textures, polygons, etc that are used to support 3D graphical mode.  My guess is that you are running out of video RAM and the card simply goes back to 1920x1080 (standard HD).  Look through /var/log/Xorg.0.log carefully for additional clues.

Does your video card have 3 GB of video RAM?

Try booting with a LiveUSB and use 2D graphics mode only (*metacity* for example) and see if your graphics are stable at 4K resolution in 2D mode only.

Also check the quality of your HDMI cable.  A cheap cable will not pass the high frequencies needed to support 4K.

---

### Post by Yellow Pasque on 2015-10-09
> Using HorizSync/VertRefresh ranges from the EDID for display device SAMSUNG (DFP-2) (Using EDID frequencies has been enabled on all display devices.)

Maybe there is something here you can use, like UseEDID: [http://us.download.nvidia.com/XFree86/Linux-x86_64/346.96/README/xconfigoptions.html](http://us.download.nvidia.com/XFree86/Linux-x86_64/346.96/README/xconfigoptions.html)
```
Option "UseEDID" "boolean"

    By default, the NVIDIA X driver makes use of a display device's EDID, when available, during construction of its mode pool. The EDID is used as a source for possible modes, for valid frequency ranges, and for collecting data on the physical dimensions of the display device for computing the DPI (see Appendix E, Dots Per Inch). However, if you wish to disable the driver's use of the EDID, you can set this option to False:

        Option "UseEDID" "FALSE"

    Note that, rather than globally disable all uses of the EDID, you can individually disable each particular use of the EDID; e.g.,

        Option "UseEDIDFreqs" "FALSE"
        Option "UseEDIDDpi" "FALSE"
        Option "ModeValidation" "NoEdidModes"

    When this option is set for an X screen, it will be applied to all X screens running on the same GPU.

    Default: True (use EDID).
```

---

### Post by tron2 on 2015-10-09
> **tgalati4 said:**
> Welcome to the forums.

Understand that with a 4K display, not only do you need enough video RAM to paint 4K resolution worth of pixels in 2D mode, but you also need enough video RAM to hold the 3D textures, polygons, etc that are used to support 3D graphical mode.  My guess is that you are running out of video RAM and the card simply goes back to 1920x1080 (standard HD).  Look through /var/log/Xorg.0.log carefully for additional clues.

Does your video card have 3 GB of video RAM?

Try booting with a LiveUSB and use 2D graphics mode only (*metacity* for example) and see if your graphics are stable at 4K resolution in 2D mode only.

Also check the quality of your HDMI cable.  A cheap cable will not pass the high frequencies needed to support 4K.

Thanks for the suggestions.

I've got the 1GB card, but once the graphical interface comes up I can successfully run 4K @ 2D (which is exactly what I'm trying to set automatically at boot time).

The cable is a monter black platinum, so I don't see any issues with the bandwidth (and it works flawlessly once I put the card into 4K mode manually).

I'll comb over the Xorg log again.

---

### Post by tron2 on 2015-10-09
Thank you

I've read this appendix a few times.  When I ignore the EDID I get unpredictable results.  I've downloaded the EDID and modified it to attempt to generate my own custom EDID, but it didn't have the expected effects.

---

