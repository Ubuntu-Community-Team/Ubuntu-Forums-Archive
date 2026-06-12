---
title: "X doesn't start with Nvidia drivers"
date: 2009-08-31
forum: Hardware
---

### Post by plugAndPlayin on 2009-08-31
I am trying Ubuntu (9.04) for the first time on my aging desktop... 
I tried installing the Nvidia drivers for my old Geforce 2 MX 200 graphics card thru >system>administration>hardware drivers. (I need the hardware acceleration to get flash-video playing in a smooth way)
Driver installed = version 96.43.10


The system tends to hang itself just before it show the logon window. If I startup in recovery mode and autofix the graphics than ubuntu starts up again. (using the generic graphics driver without graphics acceleration) 
Strangely, sometimes the system does boot with the Nvidia drivers installed..(only the first restart after installing the drivers; and it seems as long as you restart it keeps on working, but if you actually shut down and do a cold boot, the system hangs after the first ubuntu screen with the progress bar, when it's at the end the screen turns black)


After a good boot with the proprietary Nvidia drivers, there are no errors in Xorg.0.log
only a warning:
(WW) NVIDIA(0): 
(WW) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
(WW) NVIDIA(0):     will be used as the requested mode.
(WW) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 1024 x 768
(--) NVIDIA(0): DPI set to (81, 81); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(--) Depth 24 pixmap format is 32 bpp

After a failure to boot with the proprietary Nvidia drivers, there is following error in Xorg.0.log:
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)


I noticed: When boot with Nvidia drivers succesfull, then the resolution of the logon window is the same as the desktop/windows when ubuntu is up and running. When the generic drivers are used, the logon window seems to be shown in a higher resolution then ubuntu is when it is up and running. (u can actually see the mouse pointer get bigger)




I checked that nvidia is added to /etc/modules so it loads at reboot. (it contains "lp" and "nvidia")

My Xorg.conf file looks like this:
Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
    Option    "AddARGBGLXVisuals"    "True"
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection


I also tried things explained at following forum:
[http://ubuntuforums.org/showthread.php?t=971103&page=3](http://ubuntuforums.org/showthread.php?t=971103&page=3)
No luck however...

I also tried to install other drivers (version 76) with envy. But this didn't boot either. (the system automatically repaired itself and used the generic drivers again to get started.


Can anyone help me? Or is this a lost cause?

---

### Post by newton21989 on 2009-09-03
I'm no Xorg.conf expert, but it looks like you need to manually specify the video modes your screen can use. Like I said, my knowledge of tweaking Xorg.conf is very limited, but I hope this gives you a good place to start Googling.

---

