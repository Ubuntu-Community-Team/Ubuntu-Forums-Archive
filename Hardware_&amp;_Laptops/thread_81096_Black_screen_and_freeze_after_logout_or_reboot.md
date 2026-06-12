---
title: "Black screen and freeze after logout or reboot"
date: 2005-10-23
forum: Hardware &amp; Laptops
---

### Post by cameleon078 on 2005-10-23
Hello,

I have just installed an ubuntu 5.10 and the nvidia driver.
I had this lines to my /etc/X11/xorg.conf because my screen is not correctly detected :

Section "Monitor"[INDENT]Identifier   "Monitor0"
        VendorName   "Monitor Vendor"
        ModelName    "Flatron995FT"
        DisplaySize  360        270
        HorizSync    30.0 - 96.0
        VertRefresh  50.0 - 160.0
        Option      "dpms"
[/INDENT]
EndSection

Section "Device"[INDENT]Identifier  "Videocard0"
        Driver      "nvidia"
        VendorName  "Videocard vendor"
        BoardName   "NVIDIA GeForce FX (generic)"
        Option      "NoLogo" "on"
[/INDENT]
EndSection

Section "Screen"[INDENT]Identifier "Screen0"
        Device     "Videocard0"
        Monitor    "Monitor0"
        DefaultDepth     24
        SubSection "Display"[INDENT]Viewport   0 0
                Depth     16
                Modes    "800x600" "640x480"
        [/INDENT]
        EndSubSection
        SubSection "Display"[INDENT]Viewport   0 0
                Depth     24
                Modes    "1600x1200" "1400x1050" "1280x960" "1280x800" "1280x1024" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
        [/INDENT]
        EndSubSection
[/INDENT]
EndSection

After that I can put the resolution in 1600x1200.
But when I want to reboot or logout, the screen becomes black and the x server is frozen.

Thank you for your help.

---

### Post by cameleon078 on 2005-10-24
I have the same problem when I want to get a consol with CTRL-ALT-F*.

---

