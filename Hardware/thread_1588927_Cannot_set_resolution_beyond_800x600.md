---
title: "Cannot set resolution beyond 800x600"
date: 2010-10-05
forum: Hardware
---

### Post by Thizzle on 2010-10-05
On a fresh install of Ubuntu 10.04, I've been trying to set my screen resolution to my monitor's native resolution (1920x1200). I've connected my Dell 2405FPW to the VGA port of my Matrox G550. So far, the only options Ubuntu gives me are 800x600 and lower.

Here's what my xorg.conf currently looks like:

```

Section "Device"
Identifier "Device0"
Driver "mga"
BusID "PCI:1:0:0"
Option "OldDmaInit" "True" "ModeValidation" "NoMaxPClkCheck"
EndSection

Section "Monitor"
Identifier "Monitor0"
VendorName "Unknown"
ModelName "Unknown"
HorizSync 30.0 - 110.0
VertRefresh 50.0 - 150.0
Option "DPMS"
Modeline "1920x1200_60.00" 154.0  1920 1968 2000 2080  1200 1203 1209 1235 +Hsync -Vsync
EndSection

Section "Screen"
Identifier "Screen0"
Device "Device0"
Monitor "Monitor0"
DefaultDepth 24
SubSection "Display"
Depth 24
Modes "1920x1200_60.00" "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
EndSection

```

When I use these settings, Ubuntu hangs at the loading/logo screen. When I remove the xorg.conf, Ubuntu boots up fine, but I'm stuck with 800x600.

I can't figure out what I'm doing wrong. Any help would be appreciated!

---

### Post by S.R on 2010-10-05
Sounds like a driver issue. What kind of graphics card do you have? Are you running the generic or the drivers specifically for that card?

---

### Post by Thizzle on 2010-10-06
I have a Matrox G550 card and I'm using the mga drivers that were included in the Ubunutu 10.04 installation.
 
For now I have removed the xorg.conf file, so that it will at least boot up properly in 800x600.
 
Any help would be much appreciated.

---

