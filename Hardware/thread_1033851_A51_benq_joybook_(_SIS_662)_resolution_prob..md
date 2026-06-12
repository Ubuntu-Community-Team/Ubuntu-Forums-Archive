---
title: "A51 benq joybook ( SIS 662) resolution prob."
date: 2009-01-07
forum: Hardware
---

### Post by ardav on 2009-01-07
i am pretty bored with this. i will summarize everything.
i have ubuntu 8.10 (intrepid...)
Benq Joybook A51  sis mirage 662 graphic card.
sis driver is useless. (flickering blank screen etc.) both in 7.10 and 8.10. 
i did A LOT of research. tried different drivers. edited xorg.conf manually. i was able to get 1280x768 with vesa at most. i believe i tried everything that can be done in xorg.conf . (i managed to get 1280x768 from 640x480 with those advices). but i COULD NOT get 1280x800 which is the best for my screen. i am asking especially for people who has this notebook( benq a51) or sis 661/741/760 PCI/AGP or 662/761Gx. 
i need a working sis driver with 1280x800 and config or
       a config for vesa driver with 1280x800.

---

### Post by ardav on 2009-01-08
Section "Device"
  identifier "Carte testcdq"
  boardname "vesa"
  busid "PCI:1:0:0"
  driver "vesa"
  screen 0
EndSection

Section "Monitor"
  identifier "ecran CFT"
  vendorname "Generic"
  modelname "Flat Panel 1280x800"
  HorizSync 31.5-90
  VertRefresh 60
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
  modeline  "1440x900@60" 106.47 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
  modeline  "1600x1024@60" 136.36 1600 1704 1872 2144 1024 1025 1028 1060 -hsync +vsync
  modeline  "1680x1050@60" 147.14 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
  modeline  "1920x1200@60" 193.16 1920 2048 2256 2592 1200 1201 1204 1242 -hsync +vsync
  gamma 1.0
EndSection

Section "Screen"
  Identifier "Default Screen"
  Device "Carte testcdq"
  Monitor "ecran CFT"
  DefaultDepth 24
  SubSection "Display"
    depth 24
    virtual 1280 800
    modes "800x600@60" "1280x768@60" "1280x720@60" "1280x800@60" "1440x900@60" "1600x1024@60" "1680x1050@60" "1920x1200@60"
  EndSubSection
EndSection


with this i get 1280x768 res. and i get an 1280x800 option. but it is weird .(screen moves up when i move mouse up, and down when move down)
i understood that vesa does not allow 1280 800 but i can only use "vesa" driver. with sis i get blank screen,fuzz,snow call whatever you want.i ONLY want 1280x800 res. so
if you use sis driver properly please help me.

---

### Post by ardav on 2009-01-08
Section "Device"
  identifier "Carte testcdq"
  boardname "vesa"
  busid "PCI:1:0:0"
  driver "vesa"
  screen 0
EndSection

Section "Monitor"
  identifier "ecran CFT"
  vendorname "Generic"
  modelname "Flat Panel 1280x800"
  HorizSync 31.5-90
  VertRefresh 60
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
  modeline  "1440x900@60" 106.47 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
  modeline  "1600x1024@60" 136.36 1600 1704 1872 2144 1024 1025 1028 1060 -hsync +vsync
  modeline  "1680x1050@60" 147.14 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
  modeline  "1920x1200@60" 193.16 1920 2048 2256 2592 1200 1201 1204 1242 -hsync +vsync
  gamma 1.0
EndSection

Section "Screen"
  Identifier "Default Screen"
  Device "Carte testcdq"
  Monitor "ecran CFT"
  DefaultDepth 24
  SubSection "Display"
    depth 24
    virtual 1280 800
    modes "800x600@60" "1280x768@60" "1280x720@60" "1280x800@60" "1440x900@60" "1600x1024@60" "1680x1050@60" "1920x1200@60"
  EndSubSection
EndSection


with this i get 1280x768 res. and i get an 1280x800 option. but it is weird .(screen moves up when i move mouse up, and down when move down)
i understood that vesa does not allow 1280 800 but i can only use "vesa" driver. with sis i get blank screen,fuzz,snow call whatever you want.i ONLY want 1280x800 res. so
if you use sis driver properly please help me.

---

### Post by bsdaemon on 2009-02-07
Hello!
I solved this problem by downloading new sis driver from intel download site. here is the link: [http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&Inst=Yes&ProductID=2773&DwnldID=15443&strOSs=All&OSFullName=All%20Operating%20Systems&lang=eng](http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&Inst=Yes&ProductID=2773&DwnldID=15443&strOSs=All&OSFullName=All%20Operating%20Systems&lang=eng) . Then unpack it and overwrite /usr/lib/xorg/modules/drivers/sis_drv.so by downloaded file from archive. Then put into your /etc/X11/xorg.conf your 1280x800 resolution. This is the part of my file for example:

Section "Device"
        Identifier  "Videocard0"
        Driver      "sis"
EndSection

Section "Screen"
        Identifier "Screen0"
        Device     "Videocard0"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
                Modes "800x600" "1280x800"
        EndSubSection
EndSection


Then restart your Xorg and enjoy.
I have CentOS  5.2, but i think this will be useful for your Ubuntu.

---

