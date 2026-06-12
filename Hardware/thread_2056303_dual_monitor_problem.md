---
title: "dual monitor problem"
date: 2012-09-11
forum: Hardware
---

### Post by oceanid on 2012-09-11
Dear All;
how can I save the dual monitor configuration to load after restarting?

the problem is:
I have 3 computers with "ATI 5400" in my office.
all monitors are samsung syncmaster s22a360h plus.
I use a DTV and a Projector connected to my PCs too.
I have connected them as follow:
   -each monitors to the graphic card vga port,
   -all HDMI output to a switcher and use this switcher to get the monitors on DTV 
   -all DVA ports to a switcher and use this switcher to get the monitors on projector.

in this way I am going to switch between monitors on the DTV or Projector.
but each time that I do a restart or switch some times on computers, the configuration such as screen resolution and refresh rate reset and cause to some problems such as changing desktop Icons on monitor or black screen on DTV or Monitor or even DTV not appears in display manager until restart.

how can I solve this problem?

here is my xorg.conf:


Section "ServerLayout"
    Identifier     "amdcccle Layout"
    Screen      0  "amdcccle-Screen[1]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
    Load  "glx"
EndSection

Section "ServerFlags"
    Option        "Xinerama" "off"
EndSection

Section "Monitor"
    Identifier   "0-CRT2"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "Disable" "true"
EndSection

Section "Monitor"
    Identifier   "0-DFP1"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "TargetRefresh" "60"
    Option        "Position" "1600 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
    Option        "PreferredMode" "1024x768"
EndSection

Section "Monitor"
    Identifier   "0-CRT1"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1600x1200"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Device"
    Identifier  "Default Device"
    Driver      "fglrx"
EndSection

Section "Device"
    Identifier  "amdcccle-Device[1]-0"
    Driver      "fglrx"
    Option        "Monitor-CRT1" "0-CRT1"
    Option        "Monitor-DFP1" "0-DFP1"
    BusID       "PCI:1:0:0"
EndSection

Section "Device"
    Identifier  "amdcccle-Device[1]-1"
    Driver      "fglrx"
    Option        "Monitor-CRT2" "0-CRT2"
    Option        "Monitor-DFP1" "0-DFP1"
    BusID       "PCI:1:0:0"
    Screen      1
EndSection

Section "Screen"
    Identifier "Default Screen"
    DefaultDepth     24
EndSection

Section "Screen"
    Identifier "amdcccle-Screen[1]-0"
    Device     "amdcccle-Device[1]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Virtual   3520 3520
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "amdcccle-Screen[1]-1"
    Device     "amdcccle-Device[1]-1"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

---

### Post by darth62969 on 2012-09-11
first of all you need an eyefinity 4 ready card or 2 cards in each system. this is because of hardware limitations. there are also driver limitations too you can't run 2 screen as a mirror and another 2 as an extension. i would recommend upgrading the graphics card to a few 7870's or 6870's. both of these cards have eyefinity 4 support. you need this even if you are not running a game. but just for the shear card graphics draw. 

[7870]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814103208") 
[6870]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814161389")
the professional option... firepro and quadro cards are expensive and i can't find one that suites your needs within a reasonable price range

---

### Post by oceanid on 2012-09-16
ok thank you,
if I want to have 2 display such as vga monitor+ HD TV(HDMI) or vga monitor + Projector(DVI), while all of 3 cables (VGA+HDMI+DVI) connected to graphic card, do you have any suggestion to setting up?

---

