---
title: "Using different resolutions for laptop and external screens"
date: 2006-10-12
forum: Hardware &amp; Laptops
---

### Post by xmas_beetle on 2006-10-12
Hey guys,

I'm struggling a bit with getting my external monitor working on mt HP nx7010. The laptop screen is a wide screen running on 1280x800 but my external screen is a normal 17".

I want to run both screens at the same time but and different resolutions. Keep 1280x800 on the builtin screen and have 1024x768 on the external screen. First of all is this possible? Secondly, hopefully you guys can point me in the right direction.

Here is what I've got so far:

 
```
Section "Device"
  identifier "ATI Technologies, Inc. Radeon R250 Lf [Radeon Mobility 9000 M9]"
  boardname "fglrx"
  busid "PCI:1:0:0"
  driver "ati"
  screen 0
  option "OverlayOnCRTC2"
  option "MergedFB" "off"
EndSection


Section "Monitor"
  identifier "Generic Monitor"
  modelname "Custom 1"
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  modeline  "1280x800@75" 107.21 1280 1360 1496 1712 800 801 804 835 -hsync +vsync
  modeline  "1280x768@75" 102.98 1280 1360 1496 1712 768 769 772 802 -hsync +vsync
  modeline  "1280x720@50" 60.47 1280 1328 1456 1632 720 721 724 741 -hsync +vsync
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
  modeline  "1440x900@60" 106.47 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
  modeline  "1600x1024@60" 136.36 1600 1704 1872 2144 1024 1025 1028 1060 -hsync +vsync
EndSection

Section "Screen"
  Identifier "Default Screen"
  Device "ATI Technologies, Inc. Radeon R250 Lf [Radeon Mobility 9000 M9]"
  Monitor "Generic Monitor"
  DefaultDepth 24
  SubSection "Display"
    depth 24
    virtual 1600 1024
    modes "1280x768@60" "1280x720@60" "800x600@60" "1280x800@75" "800x600@75" "1
280x768@75" "800x600@72" "1280x720@50" "800x600@56" "1280x800@60" "1440x900@60"
"1600x1024@60"
  EndSubSection
EndSection

Section "Monitor"
  Identifier "External Monitor"
  modelname "Custom 2"
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsyn
c
EndSection

Section "Screen"
  Identifier "External Screen"
  Device "ATI Technologies, Inc. Radeon R250 Lf [Radeon Mobility 9000 M9]"
  Monitor "External Monitor"
  DefaultDepth 24
  SubSection "Display"
  virtual 1024 768
  modes "1280x768@60" "1280x720@60" "800x600@60" "1280x800@75" "800x600@75" "128
0x768@75" "800x600@72" "1280x720@50" "800x600@56" "1280x800@60" "1440x900@60" "1
600x1024@60"
  EndSubSection
EndSection

Section "ServerLayout"
#  Identifier "Default Layout"
  Identifier "dual"
  screen 0 "Default Screen" 0 0
  screen 1 "External Screen" 1 1
  InputDevice "Generic Keyboard"
  InputDevice "Configured Mouse"
  InputDevice "stylus" "SendCoreEvents"
  InputDevice "cursor" "SendCoreEvents"
  InputDevice "eraser" "SendCoreEvents"
  InputDevice "Synaptics Touchpad"
EndSection
```

Do I need to put another device section in for the external screen?

Any input would be greatly appreciated.

Thanks
Jared

---

### Post by xmas_beetle on 2006-10-12
I managed to get it working. I'm not quite sure how I did it though. lol

---

### Post by insub2 on 2006-11-12
> **xmas_beetle said:**
> I managed to get it working. I'm not quite sure how I did it though. lol
 could you post your xorg.conf....maybe?

---

### Post by xmas_beetle on 2006-11-28
> **insub2 said:**
> could you post your xorg.conf....maybe?

Sorry for the late reply but since getting it working I have reinstalled with Gentoo. Sorry

---

### Post by jazzgossen on 2006-11-28
For what it's worth: the new nVidia driver (from their website) comes with a graphical utility that lets you set mutiple dislpays easily, if you have an nVidia card and dare to install an non-repository driver.

---

### Post by marcantonio on 2006-11-28
> **xmas_beetle said:**
> Sorry for the late reply but since getting it working I have reinstalled with Gentoo. Sorry

I've had this problem since dapper, in breezy it worked fine.

xmas_beetle:  Is your xorg.conf the same as the one you posted above?

Marc

---

