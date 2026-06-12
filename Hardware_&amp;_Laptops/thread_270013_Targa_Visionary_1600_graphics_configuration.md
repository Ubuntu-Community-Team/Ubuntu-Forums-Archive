---
title: "Targa Visionary 1600 graphics configuration"
date: 2006-10-02
forum: Hardware &amp; Laptops
---

### Post by Immortalis on 2006-10-02
I'm having trouble with the graphics in Ubuntu. Ubuntu works but it doesn't seem like the graphics i configured the way it should be. It runs more badly then Windows XP, when I move windows they make a tail on the screen and I get around 73.139 FPS using glxgears -printfps.

The following is taken from the manual,

LCD
• Display Panel: 14.1-inch XGA / SXGA+ active-matrix TFT display with up to 16M colors.

Graphics
• Graphic Controller: VIA Twister K with S3 Savage4 (VT8362) integrated 2D / 3D graphics accelerator.

The following is from the /etc/X11/xorg.conf,

Section "Device"
    Identifier    "S3 Inc. VT8636A [ProSavage KN133] APG4X VGA Controller (TwisterK)"
    Driver        "vesa"
    BusID         "PCI:1:0:0"
EndSection

I've tried changing the "vesa" -> "savage" which resulted in my graphics running better. I was however only able to run in 640x480.

Any help is welcome :) but do try and explain it in steps, as I'm new to linux/Ubuntu.

---

