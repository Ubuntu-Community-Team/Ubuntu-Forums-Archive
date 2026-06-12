---
title: "Dell Inspiron 1100: can't get high resolution"
date: 2009-04-26
forum: Hardware
---

### Post by atomic-luncheon on 2009-04-26
I installed Ubuntu 8.1 on a Dell Inspiron 1100 and upgraded it to 9.04.  However, I cannot get any desktop resolutions other than 640x480 and 800x600.

I read several threads with this problem and tried solving it, but now I'm out of ideas.  Here's a summary of what I've done so far:

1.  My BIOS is version A32, and has 8mb set for video memory.

2.  In /boot/grub/menu.1st I changed the default from splash to nosplash.

3.  Various threads said that I should install the 915resolution utility, but this package is obsolete.  [http://packages.ubuntu.com/hardy/x11/915resolution](http://packages.ubuntu.com/hardy/x11/915resolution) says that it is especially obsolete with "xserver-xorg-video-intel", of which I have version 2.2.6.3-0ubuntu9 already installed.

4.  When I reconfigure my xorg.conf file to use driver "i810" the driver seems to load but I get a "(EE) No devices detected.  Fatal Server Error: no screens found" error and X won't start.  Here is the latest xorg.conf file I've tried this with:

```
Section "Device"
    Identifier    "Configured Video Device"
    Driver        "i810"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
    HorizSync 28-80
    VertRefresh 43-60
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth 24    
    SubSection "Display"
        Depth 16
        Modes "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth 24
        Modes "1024x768" "800x600" "640x480"
    EndSubSection
EndSection
```When I reboot into recovery mode and tell the menu to try to repair X, I get this next configuration file.  It works, but I am stuck with either 640x480 or 800x600 resolution.
```
Section "Device"
    Identifier    "Configured Video Device"
    Driver        "vesa"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection
```Um... what should I try now?

---

