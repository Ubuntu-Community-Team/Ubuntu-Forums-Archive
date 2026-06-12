---
title: "dual screen on toshiba a100 (1650x1080)"
date: 2008-07-19
forum: Hardware
---

### Post by max7 on 2008-07-19
I have toshiba a100-002.

I used it with 17 inch (1280x1024) LCD.
I have constructed manually xorg.conf that makes both screen work with proprietary driver. (Compiz was working fine)

X and nvidia auto tools were failing to create a working copy of xorg.conf

And now I got a new Acer p223w (1650x1050) to replace old 1280x1024.

I can not make it work.

I was replacing HorizSync, VertRefresh and ModeLine

    HorizSync       31.5 - 107.5
    VertRefresh     50.0 - 85.0
    ModeLine       "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
    

-----

I tried following values:-

ModeLine "1680x1050@60"  147.14  1680 1784 1968 2256  1050 1051 1054 1087  -HSync +Vsync

modeline "1680x1050@60" 146.25 1680 1784 1960 2240 1050 1053 1059 1089 +hsync -vsync

Option "DPMS"
HorizSync 30-70
VertRefresh 50-160

  Modeline      "1680x1050"x60.0 146 1680 1784 1960 2240 1050 1053 1059 1089 -hsync +vsync 
  Option       "DPMS"
  DisplaySize  474 296
  HorizSync    31-83
  VertRefresh  56-75


---------------

I was trying to use:-

cd /etc/X11
sudo X -configure
sudo X -config xorg.conf.new

It produce following Monitor tag:-

Section "Monitor"
        #DisplaySize      470   300     # mm
        Identifier   "Monitor0"
        VendorName   "ACR"
        ModelName    "Acer P223W"
 ### Comment all HorizSync and VertRefresh values to use DDC:
        HorizSync    31.0 - 83.0
        VertRefresh  56.0 - 75.0
        Option      "DPMS"
EndSection

Please, help.

Does anyone has a working xorg.conf for similar configuration?

Thank You,
Max

---

