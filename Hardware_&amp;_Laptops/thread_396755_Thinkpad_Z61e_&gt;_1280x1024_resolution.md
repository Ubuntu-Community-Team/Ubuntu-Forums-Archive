---
title: "Thinkpad Z61e &gt; 1280x1024 resolution?"
date: 2007-03-29
forum: Hardware &amp; Laptops
---

### Post by balu123 on 2007-03-29
Hey,

I've just bought a Lenovo Z61e widescreen and almost everything worked out of the box. 
There is only one thing which annoys me for a while yet:

I want to use my notebook also with my external lcd monitor with a 1280x1024 screen resolution, but I don't find a way. (switch from notebook to external lcd is working)

I'm using the i810 driver and my xorg.conf is the following:

    Section "Device"
    Identifier "Generic Video Card"
    Driver "i810"
    BusID "PCI:0:2:0"
    EndSection

    Section "Monitor"
    Identifier "Generic Monitor"
    Option "DPMS"
    HorizSync 31.5-64.3
    VertRefresh 43-60
    EndSection

    Section "Screen"
    Identifier "Default Screen"
    Device "Generic Video Card"
    Monitor "Generic Monitor"
    DefaultDepth 24
    SubSection "Display"
    Depth 1
    Modes "1280x1024" "1280x800" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
    Depth 4
    Modes "1280x1024" "1280x800" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
    Depth 8
    Modes "1280x1024" "1280x800" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
    Depth 15
    Modes "1280x1024" "1280x800" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
    Depth 16
    Modes "1280x1024" "1280x800" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
    Depth 24
    Modes "1280x1024" "1280x800" "1024x768" "800x600" "640x480"
    EndSubSection
    EndSection

So, 1280x1024 is there, but there is no way for me to choose 1280x1024 as screen resolution (there is only 1280x800, 1024x768, 800x600 and 640x480). It seems like that the xserver doesn't care about my settings. I've already tried it with modelines without success. And 950resolution is also not working. 

But I wonder when I run it, it throws out the following:

    felix@felix-laptop:~$ sudo 915resolution -l
    Password:
    Intel 800/900 Series VBIOS Hack : version 0.5.2

    Chipset: 945GM
    BIOS: TYPE 1
    Mode Table Offset: $C0000 + $269
    Mode Table Entries: 36

    Mode 30 : 640x480, 8 bits/pixel
    Mode 32 : 800x600, 8 bits/pixel
    Mode 34 : 1024x768, 8 bits/pixel
    Mode 38 : 1280x1024, 8 bits/pixel
    Mode 3a : 1600x1200, 8 bits/pixel
    Mode 3c : 1920x1440, 8 bits/pixel
    Mode 41 : 640x480, 16 bits/pixel
    Mode 43 : 800x600, 16 bits/pixel
    Mode 45 : 1024x768, 16 bits/pixel
    Mode 49 : 1280x1024, 16 bits/pixel
    Mode 4b : 1600x1200, 16 bits/pixel
    Mode 4d : 1920x1440, 16 bits/pixel
    Mode 50 : 640x480, 32 bits/pixel
    Mode 52 : 800x600, 32 bits/pixel
    Mode 54 : 1024x768, 32 bits/pixel
    Mode 58 : 1280x1024, 32 bits/pixel
    Mode 5a : 1600x1200, 32 bits/pixel
    Mode 5c : 1920x1440, 32 bits/pixel
    Mode 60 : 3584x769, 8 bits/pixel
    Mode 61 : 3584x769, 16 bits/pixel
    Mode 62 : 3584x769, 32 bits/pixel
    Mode 63 : 1472x770, 8 bits/pixel
    Mode 64 : 1472x770, 16 bits/pixel
    Mode 65 : 1472x770, 32 bits/pixel
    Mode 66 : 512x771, 8 bits/pixel
    Mode 67 : 512x771, 16 bits/pixel
    Mode 68 : 512x771, 32 bits/pixel
    Mode 69 : 2208x771, 8 bits/pixel
    Mode 6a : 2208x771, 16 bits/pixel
    Mode 6b : 2208x771, 32 bits/pixel
    Mode 6c : 1280x800, 8 bits/pixel
    Mode 6d : 1280x800, 16 bits/pixel
    Mode 6e : 1280x800, 32 bits/pixel

So, there ARE the resolutions I need, but I cannot select it. 

Why? Any Ideas? I'm trying for hours now.

Balu

---

### Post by balu123 on 2007-03-30
I got it.
I had to select ALL available resolutions in xorg.conf

---

