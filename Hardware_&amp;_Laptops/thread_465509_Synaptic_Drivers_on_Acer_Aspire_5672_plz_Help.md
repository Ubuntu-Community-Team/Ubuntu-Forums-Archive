---
title: "Synaptic Drivers on Acer Aspire 5672 plz Help"
date: 2007-06-05
forum: Hardware &amp; Laptops
---

### Post by viperdrake on 2007-06-05
hi guys ive been trying to install this driver ... dont know how to 

i have used the synaptic package manager...

and i cannot get it to work...

when i check my Xorg.conf  itsinstact nothing has been added....

i tried adding the info needed.. but still it wouldnt work...

i have installed Qsynaptics and when i load it up ( alt + f2, then type qsynaptics)

everything is grayed out and it says to please install the drivers.

the Synaptic package manager says that i alredy have installed the driver... yet. it wont work

and the program says to install it...


please help... is very anoying and difficult trying to type while randomly clicking the touchpad.




thx in advance 

Viper

---

### Post by DagMan on 2007-06-05
in /etc/X11/xorg.conf I have this near the mouse section.
```
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
        Option          "SHMConfig"             "on"
EndSection
```
and toward the bottom of the file I have this in the part that begins with **Section "ServerLayout"**
```
        InputDevice     "Synaptics Touchpad"
```

---

### Post by viperdrake on 2007-06-05
Dagman ur my hero!!!

ive spent hours trying to get this to work


it was the last line i was missing that was all!!! now it works perfectly!!!


WOOT

thx man ! haha i can finally write normaly!

---

