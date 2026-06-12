---
title: "Laptop LCD Contrast Control, Please help !"
date: 2009-05-03
forum: Hardware
---

### Post by randadinata on 2009-05-03
Hi,

Is there anyway in Ubuntu i can control my laptop (ACER 2480) lcd contrast ? 
By default my laptop looks too bright and rather yellow-ish. It's the same on windows XP, but, intel driver package on windows has this display control panel with color correction on it. 

[IMG]http://i39.tinypic.com/5ex40l.png[/IMG]


I'm not talking about the backlight, it's already working correctly on Ubuntu, i can control them using the keyboard hotkeys. So far, i have already tried :

1. xgamma didnt have the effect i wanted.

2. initially, ddccontrol doesnt support my graphic (Intel 950GM). so i insert the PCI DEVICE ID to its source code. Then ddccontrol can recognize my VGA but sill not working, even tho the EDID was read correctly.

3. i also tried various stuff in /*proc*/acpi/video/***

Please help, this is the only stopper for me from using ubuntu. I want to solve this. I'm not a kernel guru, but i can do basic compiling.

Technical Details :
---------------------------------------------------------------------------------------
Ubuntu Hardy

Monitor Name                                      : Toppoly TD141TGCK1 
      Monitor ID                                        : TNJ0160
Manufacturer                                      : TD141TGCK1 
      Monitor Type                                      : 14.1" LCD (WXGA)       
Manufacture Date                                  Week 39 / 2006       

[ Intel 82940GML/943GML Graphics Controller 0 [A-3] ]

    Device Properties:
      Device Description                                Intel 82940GML/943GML Graphics Controller 0 [A-3]
      Bus Type                                          PCI
      Bus / Device / Function                           0 / 2 / 0
      Device ID                                         8086-27A2
      Subsystem ID                                      1025-0110
      Device Class                                      0300 (VGA Display Controller)
      Revision                                          03
      Fast Back-to-Back Transactions                    Supported, Disabled

    Device Features:
      66 MHz Operation                                  Not Supported
      Bus Mastering                                     Enabled

  [ Intel 82940GML/943GML Graphics Controller 1 [A-3] ]

    Device Properties:
      Device Description                                Intel 82940GML/943GML Graphics Controller 1 [A-3]
      Bus Type                                          PCI
      Bus / Device / Function                           0 / 2 / 1
      Device ID                                         8086-27A6
      Subsystem ID                                      1025-0110
      Device Class                                      0380 (Display Controller)
      Revision                                          03
      Fast Back-to-Back Transactions                    Supported, Disabled

    Device Features:
      66 MHz Operation                                  Not Supported
      Bus Mastering                                     Enabled

---

