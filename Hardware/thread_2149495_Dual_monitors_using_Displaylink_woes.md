---
title: "Dual monitors using Displaylink woes"
date: 2013-05-29
forum: Hardware
---

### Post by dolson60174 on 2013-05-29
ok I have read through several posts and tried many different changes to my config file with no luck.  I am posting my info below to see if a second set of eyes sees something I am missing.  My Displaylink monitor is green, so i know its recognized. thanks in advance!

First is my cat /proc/fb info:
[B]0 udlfb
1 inteldrmfb[/B]

Second is my grep -i drivers /var/log/Xorg.0.log:
[B][    19.587] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    19.588] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    19.588] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    19.589] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so[/B]

Last is my config file:

[B]Section "ServerLayout"
        Identifier      "Server Layout"
        Screen  0       "DisplayLinkScreen" 0 0
        Screen  1       "DefaultScreen" RightOf "DisplayLinkScreen"
        Option          "Xinerama" "On"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "intel"
    BusID          "PCI:0:2:0"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "DefaultScreen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        DefaultDepth    16
        SubSection "Display"
                Depth   16
                Modes   "1366x768"
        EndSubSection
EndSection

Section "Device"
        Identifier      "DisplayLinkDevice"
        driver          "fbdev"
        BusID   "USB"
        Option  "fbdev" "/dev/fb0"
EndSection

Section "Monitor"
        Identifier      "DisplayLinkMonitor"
        DisplaySize 152 80    # In millimeters
EndSection

Section "Screen"
        Identifier      "DisplayLinkScreen"
        Device          "DisplayLinkDevice"
        Monitor         "DisplayLinkMonitor"
        DefaultDepth    16
        SubSection "Display"
                Depth   16
                Modes   "800x480"
        EndSubSection
EndSection[/B]

---

### Post by dolson60174 on 2013-05-29
updated info..

i forgot to add myy results of lspci | grep VGA:
[B]
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)[/B]

---

### Post by andrewhiggs on 2013-05-29
I have a similar problem on my laptop, although I am running Slackware 64. This is what I see in dmesg after loads of lines similar to 'udlfb: 1280x1024 valid mode':

[    8.998866] udlfb: DisplayLink USB device /dev/fb0 attached. 1024x768 resolution. Using 3072K framebuffer memory
[    8.999147] usbcore: registered new interface driver udlfb
[    9.039827] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input7
[    9.055443] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    9.055577] i915 0000:00:02.0: setting latency timer to 64
[    9.152290] i915 0000:00:02.0: irq 43 for MSI/MSI-X
[    9.152295] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    9.152362] [drm] Driver supports precise vblank timestamp query.
[    9.152703] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    9.390173] fbcon: inteldrmfb (fb1) is primary device
[    9.390176] fbcon: Remapping primary device, fb1, to tty 1-63
[    9.390372] [drm] Changing LVDS panel from (+hsync, +vsync) to (-hsync, -vsync)
[    9.562826] cfg80211: World regulatory domain updated:
[    9.562831] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    9.562837] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    9.562842] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    9.562846] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    9.562849] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    9.562853] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    9.581030] brcmsmac 0000:06:00.0: bus 6 slot 0 func 0 irq 11
[    9.581077] brcmsmac 0000:06:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    9.581084] brcmsmac 0000:06:00.0: setting latency timer to 64
[    9.897461] udlfb: released /dev/fb0 user=0 count=0
[    9.901282] fb1: inteldrmfb frame buffer device
[    9.902238] drm: registered panic notifier

So as you can see my problem is that during initial boot the device is recognised and registered, but later onn something presumably steps on its toes because '[    9.897461] udlfb: released /dev/fb0 user=0 count=0'. At least that is how I read it.

I know this does not really help you but if your dmesg is the same perhaps it might point you in the right direction.

HTH.

Regards

---

### Post by dolson60174 on 2013-05-29
here are some items related that I found in mine:
[B][   22.210214] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   22.210228] udlfb: DisplayLink USB device /dev/fb1 attached. 1680x1050 resolu
tion. Using 6896K framebuffer memory
[   22.210249] usbcore: registered new interface driver udlfb
[/B]

---

