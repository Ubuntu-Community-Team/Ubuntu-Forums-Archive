---
title: "Intel core I5 build in video and HDMI Issue"
date: 2012-12-19
forum: Hardware
---

### Post by zerocooler on 2012-12-19
Hi
Here is my xorg.conf placed in /etc/X11/

```
Section "Device"
    Identifier     "Intel HD Graphics"
    Driver         "intel"
    VendorName     "INTEL Corporation"
    BusID          "PCI:0:2:0"
    Option         "monitor-VGA1" "none"
    Option         "monitor-DP1" "none"
    Option         "monitor-HDMI1" "none"
    Option         "monitor-HDMI2" "none"
    Option         "monitor-HDMI3" "HCG"
    Option         "monitor-DP2" "none"
    Option         "monitor-DP3" "none"
    Option         "ModeDebug" "true"
#    Option        "UseDisplayDevice" "HCG"
#    Option         "ConnectedMonitor" "HCG"
#    Option         "UseEDID" "FALSE"
#    Option          "IgnoreEDID" "true"
#    Option          "DDCMode" "false"
    Option          "noDDC"
EndSection

Section "Monitor"
   Identifier "HCG"
   VendorName "HarmanKardon"
   Option "enable" "true"
#  HorizSync   14.0 - 70.0
#  VertRefresh 24.0 - 62.0
#  Option      "DPMS" "true"
  Modeline    "1920x1080@24p"     74.230 1920 2560 2604 2752 1080 1084 1089 1125 +hsync +vsync
  Modeline    "1920x1080@50p"    148.500 1920 2448 2492 2640 1080 1084 1089 1125 +hsync +vsync
  Modeline    "1920x1080@59.94p" 148.352 1920 1960 2016 2200 1080 1082 1088 1125 +hsync +vsync
  Modeline    "1920x1080@60p"    148.500 1920 2008 2056 2200 1080 1084 1089 1125 +hsync +vsync
EndSection

Section "Monitor"
Identifier "none"
Option "Ignore" "true"
EndSection

Section "Screen"
    Identifier     "TV"
    Device         "Intel HD Graphics"
    Monitor        "HCG"
#    Option         "ColorRange" "Full"
#    Option         "ColorSpace" "RGB"
    Option         "UseDisplayDevice" "HCG"
    Option         "ConnectedMonitor" "HCG"

    DefaultDepth  24
    SubSection     "Display"
    Depth       24
    Modes     "1920x1080@24p" "1920x1080@50p" "1920x1080@59.94p" "1920x1080@60p"

    EndSubSection
EndSection

```

My HDMI cable is connected to amplituner AVR260 (HarmanKardon).
When i start PC when amplituner is turned on all works well.
But when it starts on powered off amplituner i cannot get the screen to work afterwards.
How can i force (fake) detection of connected amplituner to HDMI port?

lubuntu 12.10 - forgot to mention that

---

### Post by zerocooler on 2012-12-19
*BUMP*
no one can point me right direction?

---

### Post by typhoon_tip on 2012-12-19
Have you tried entering "Display" interface from the top bar/right menu when you switch on the amp after the computer ? It should then detect the additional display normally.

---

### Post by zerocooler on 2012-12-20
yes it does detect it.
The problem is i want to launch at start xbmc so my wife can operrate it from remote.
She cant afford to vnc to lxde session.
Thats why i want to fake detection of hdmi cable, force resolution and refreshrate at start

---

### Post by typhoon_tip on 2012-12-20
Got you. I don't think it can be done, I am an A/V fanatic myself, and even on Windows 7 is far more complicated than opening display to make the thing come to life if you don't switch the Amp first.

A friend of mine was in the same situation with his wife. It is much easier to tell her to switch on the Amp before the computer than write complex instruction.

An alternative is running a script that can fix the problem (XBMC can run scripts into Ubuntu and return easily back, I have made one to make PPPoE connection when running full screen at start).

---

