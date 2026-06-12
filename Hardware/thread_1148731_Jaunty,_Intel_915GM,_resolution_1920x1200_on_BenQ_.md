---
title: "Jaunty, Intel 915GM, resolution 1920x1200 on BenQ 24&quot;"
date: 2009-05-04
forum: Hardware
---

### Post by esutter on 2009-05-04
I have this ASUS Nova Lite low-budget PC, which works great apart from the following problem. When I install Jaunty from CD, Gnome starts with a resolution of 1600x1200, which is the maximum I can choose in the display preferences. The 24" BenQ monitor via DVI has a native resolution of 1920x1200. 
The default driver in /etc/X11/xorg.conf is "vesa". When I manually change the driver from "vesa" to "intel", the system boots, but the monitor remains blank (no signal detected). I wonder if anyone has similar issues. 

Monitor:
```
id: BenQ G2400W
res: 1920x1920 1920x1200 1680x1680 1600x1200 1440x1440 1280x1280 1280x1024 1152x1152 1024x768 800x600 720x400 640x480
freq: 31-94 50-85
```Graphics Controller:
```
description: VGA compatible controller
product: Mobile 915GM/GMS/910GML Express Graphics Controller
vendor: Intel Corporation
```xorg.conf after installation:
```
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "vesa"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection
```Xorg.0.log with vesa/intel drivers are attached. The most annoying thing however is, that with the redmond type OS, it just works :sad:. I have also tried various settings such as Modeline and DisplaySize in xorg.conf.

Thanks for your help!

---

### Post by arito on 2009-05-04
I have the same problem with someone elses PC, except that the monitor is an LG and the graphics card is an older Nvidia. I'm going to report this to Launchpad when I can access the machine in question again.

I had another kind of problem with resolution on my own PC. When I changed the resolution to 1600x1200, which is best for my 21" CRT, it was always changed to 2048x1536 when I restarted the machine. After a lot of searching, I found a working solution. I added this text to my xorg.conf file, section "Screen":

SubSection "Display"
Depth 24
Modes "1600x1200"
EndSubSection

Perhaps I should add a few more resolutions to "Modes". On the other hand "NVIDIA X Server Settings" seems to have plenty of them available. Anyway, I'm going to try if this solution works with the first machine too.

---

