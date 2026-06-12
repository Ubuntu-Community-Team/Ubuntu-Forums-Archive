---
title: "HP zt3000 and fglrx..."
date: 2006-06-11
forum: Hardware &amp; Laptops
---

### Post by D_Angle on 2006-06-11
been looking for a fix for getting the ATI Mobility 9200 (also known as 9000 , m9 or R250) to run to it's full potential.

I have tryed installing ati's drivers and fglrx drivers, even tryed the modeline hack and all i get is a garbled screen which is not readable.

I have the same problem with drivers newer then 5.6 from ati in windows ](*,) any driver older then that work fine.

Any help?

---

### Post by D_Angle on 2006-06-13
bump :sad:

---

### Post by pincushionman on 2006-06-14
I have a Presario X1000 (similar to your ZT3000), with the same "9200" M9 chip inside.  I had a heck of a time setting up Direct Rendering.  I actually use x11-drm now, instead of the ATi driver.  I am running Xorg 7.1, and the ATi driver doesn't support that yet (as of 8.26 drivers).

I have some things to try for you.  First of all, get the x11-drm driver (I think the name is radeon).  Make sure that you remove the ATi binary driver - the two usually don't coexist happily.  Next, I had to put some odd things in my xorg.conf (it lives at /etc/X11/xorg.conf).  Here's a bit of what I had to do:

Section "ServerLayout"
  InputDevice        "Mouse0" "CorePointer"
  InputDevice        "TouchPad" "AlwaysCore"
  ...
EndSection

Section "Module"
  Load "dbe"
  SubSection "extmod"
    Option "omit xfree86-dga"
  Load "type1"
  Load "freetype"
  Load "dri"
  Load "glx"
  Load "ddc"
EndSection

Section "InputDevice"
  Identifier "Mouse0"
  Driver "mouse"
  Option "Protocol" "ImPS/2"
  Option "Device" "/dev/input/mice"  #Makes mouse hot-pluggable
  Option "ZAxisMapping" "4 5"
  Option "Emulate3Buttons"
EndSection

Section "InputDevice"
  Identifier "TouchPad"
  Driver "synaptics"
  Option "Device" "/dev/input/mouse0"
  Option "Protocol" "auto-dev"
  ...
  Option "SHMConfig" "on"
  Option "UseShm" "true"
EndSection

Section "Monitor"  #Don't use this part if you don't have a 1680x1050 screen
  Identifier "SEC:0000"
  VendorName "SEC"
  ModelName "SEC:0000"
  Mode   "1680x1050"   # vfreq 60.562Hz, hfreq 64.499kHz
            DotClock        121.000000
            HTimings        1680 1704 1792 1876
            VTimings        1050 1051 1054 1065
            Flags             "-HSync" "-VSync"
  EndMode
EndSection

Section "Device"
  ...
  Driver "radeon"
  Option "NoDDC" "false"
  Option "ReverseDDC" "true"
  Option "AGPMode" "true"
  Option "DMAforXv" "true"
  Option "MonitorLayout" "LVDS,NONE"
  VideoRam 65536 # you may want 32768 if you have 32MB
  Option "RenderAccel" "true"
  # Option "AGPFastWrites" "true"    # <= Enable this at your own peril!
EndSection

Section "Screen"
  ...
  DefaultDepth 24    # Performance hit, but required for Xgl
  SubSection "Display"
    Viewport                0   0
    Depth                  24
  EndSubSection
Section "DRI"
  Mode "0666"
EndSection


  


Also, from what I have read, there is no way to make lm-sensors work in this laptop.

---

### Post by D_Angle on 2006-06-14
will give it a try and cget back to ya:D

---

