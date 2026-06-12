---
title: "Touchpad and keyboard problems on Xubuntu 9.04"
date: 2009-06-03
forum: Hardware
---

### Post by zowki on 2009-06-03
I've been using Xubuntu 8.10 for a long time without a single problem but then I decided to do a fresh install of Xubuntu 9.04. It apparently screws up my touchpad and keyboard. My touchpad doesnt work but the left and right click buttons work. The keyboard after some time does not function at all. I can still log in to the terminal using safe mode and fix problems. I am using an Acer 5500z laptop. I have googled this issue and found many others with my problem but no solutions. Help please?

Edit: Forgot to mention, USB mouse still works

Edit 2: I found a temporary solution. If I disabled my touch pad my keyboard works perfectly. But then I need to haul a USB mouse wherever I bring my laptop.

---

### Post by zowki on 2009-06-06
Bump

---

### Post by utnubuuser on 2009-06-06
tried gsynaptics?

---

### Post by zowki on 2009-06-06
Gsynaptics did not seem to help. When I tried running it at first, it complained SHMConfig needed to be true in xorg.conf. After doing a bit of googling I added this to my xorg.conf:
```
Section "InputDevice"
        Identifier      "SynPS/2 Synaptics TouchPad"
        Driver          "synaptics"
        Option          "CorePointer"
        Option          "Device"              "/dev/psaux"
        Option          "Protocol"            "auto-dev" 
        Option          "SHMConfig"           "true" 
EndSection
```
I could run gsynaptics now but after fiddling with a few settings my touchpad still did not seem to work.

---

### Post by zowki on 2009-06-08
bump

---

### Post by utnubuuser on 2009-06-09
it might be an "Alps" touchpad.  When I tried to get gsynaptics working on an older hp, I had to google around till I found someone elses xorg.conf file and copy their settings.  One of the key bits of information I found was that the section "InputDevice" had to be "Mouse" in order for it to work.

I'd suggest using the settings and options you've got, and get a look at a xorg.conf file for a system configured for a mouse, then add your driver and options details.

> Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5 6 7"
        Option          "Buttons"               "9"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "SHMConfig"             "on"
        Option          "HorizScrollDelta"      "0"
EndSection[http://ubuntuforums.org/showthread.php?p=975421]("http://ubuntuforums.org/showthread.php?p=975421")
and sometimes, xorg recongnizes "true" instead of "on" or maybe "1".
Try this:> Section "InputDevice"
Identifier "Configured Mouse"
Driver "synaptics"
Option "SendCoreEvents" "true"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
Option "SHMConfig" "true" "on" "1"
Option "HorizontalScrollDelta" "0"
EndSection

if you google around, you'll find lots under: SHMConfig

here's another thread:[http://forums.fedoraforum.org/showthread.php?t=184938]("http://forums.fedoraforum.org/showthread.php?t=184938")

---

### Post by yotam on 2009-10-17
You may consider trying my Alps driver in
   [http://www.medini.org/software/alps/alps.html]("www.medini.org/software/alps/alps.html")
-- yotam

---

