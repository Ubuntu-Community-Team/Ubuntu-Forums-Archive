---
title: "Samsung Q1 Touchscreen Calibration"
date: 2008-10-19
forum: Hardware
---

### Post by c-2501 on 2008-10-19
I have recently installed ubuntu (8.04) (through wubi) on my Samsung Q1 unit (not the ultra model), everything seems to be running fine wireless network, bluetooth, CF card reader and even the touchscreen... to a point.

The problem is that the touchscreen calibration seems to be off dramatically, where the pointer is placed/moves on the screen is no where near the place the screen is touched.  I'm guessing this is simply a matter of calibrating the touchscreen correctly.  The problem is I cant seem to find any built in tools that will allow me to do this.

I have noticed similar threads on the forum but these don't seem to apply to my situation since they all appear to be setting up the touchscreen from scratch on an older version of ubuntu.

Any help you could give me in this is much appreciated.

P.S. I have tried running the TouchKit calibration tool I downloaded on the advice of another forum thread, however this seems to have no effect on the position problems.

---

### Post by bmj0nes on 2008-10-19
sorry i'm no help. I'm just posting to watch this thread. I have a Q1Ultra i've been trying to get everything working in ubuntu. I've gotten everything but the touch screen working. I tried to compile a build of the embedded os but I've been having trouble with that as well.

---

### Post by c-2501 on 2008-10-21
Quick update: last night I tried the beta version of Intrepid on the machine (again through wubi) and this time the touchscreen calibration seems a lot better, not perfect but adequate.

I am however having a problem with completing the wubi install (errors about 'no root file system detected') Im wondering if this was caused by the way I installed wubi, because I dont have an external CD drive i dumped the contents of the live cd to a usb pen drive and ran wubi from there. 

I'll have a look through these forums and also the wubi ones for a solution.

---

### Post by c-2501 on 2008-11-07
Ok I have to say I'm completely stumped now, I've the calibration setup by default just isnt good enough (it seems perfect screen centre but gets more inaccurate towards the edges).  I have tried the other posts about this device but the problem seems to be i cant blacklist the usbtouchscreen module properly.

Is there a way to calibrate the settings this module uses?

---

### Post by maveloth on 2008-12-04
i had a good calibration with the package xserver-xorg-input-evtouch installed.

```
Section "InputDevice"
        Identifier "touchscreen"
        Driver "evtouch"
        Option "Device" "/dev/input/touchscreen"
        Option "DeviceName" "touchscreen"
        Option "MinX" "82"
        Option "MinY" "3900"
        Option "MaxX" "3960"
        Option "MaxY" "195"
        Option "SwapY" "1"
        #Option "SwapXY" "1"
        Option "ReportingMode" "Raw"
        Option "Emulate3Buttons"
        Option "Emulate3Timeout" "50"
        Option "SendCoreEvents"
        Option "MoveLimit"  "2"
EndSection
Section "ServerLayout"
     .
     .
     .
     InputDevice        "touchscreen" "SendCoreEvents"  #NOTA: non modificare o rimuovere altre voci
EndSection

```

this how i configured my xorg.conf for the touchscreen, and i had no problem!

Maveloth

P.S.sorry for my bad english but I'm italian..

---

### Post by bobneub on 2009-05-13
I have a Q1 Ultra and have to confess i'm a complete beginner at this, is there anyone that can help me get my touchscreen working on my Samsung Q1 Ultra?  I installed WUBI and i dont get any activity from my screen.

---

