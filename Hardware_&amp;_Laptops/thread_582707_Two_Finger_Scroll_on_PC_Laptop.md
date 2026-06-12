---
title: "Two Finger Scroll on PC Laptop"
date: 2007-10-20
forum: Hardware &amp; Laptops
---

### Post by Mint137 on 2007-10-20
Hello  I'm a new Linux/Ubuntu user and I'm wondering if I can get Two Finger Scrolling and other actions on my PC Laptop. I'm relatively new at Linux so I'm still trying to get used to configuring everything manually.

I've searched the forums and have found similar topics, but they seem out of date or the answers work for some and not for others.

I can currently use the edge scrolling....but really it sucks...

For reference:

Ubuntu 7.10.
ASUS F3T
ALPs Trackpad [apparently]

If you need any more info about my hardware tell me and pardon me if I don't understand some Linux talk [still learning].

---

### Post by raul_ on 2007-10-22
Just use the synaptics driver and change your xorg.conf file. Here's mine:
```


(...)
Section "InputDevice"
Driver          "synaptics"
Identifier      "Mouse0"
Option  "Device"        "/dev/psaux"
Option  "Protocol"      "auto-dev"
Option  "LeftEdge"      "1700"
Option  "RightEdge"     "5300"
Option  "TopEdge"       "1700"
Option  "BottomEdge"    "4200"
Option  "FingerLow"     "25"
Option  "FingerHigh"    "30"
Option  "FingerPress" "250"
Option  "MaxTapTime"    "130"
Option  "MaxTapMove"    "150"
Option  "VertScrollDelta" "300"[B]
Option  "VertEdgeScroll"        "false"
Option  "VertTwoFingerScroll"   "true"[/B]
Option  "MinSpeed"      "0.06"
Option  "MaxSpeed"      "0.12"
Option  "AccelFactor" "0.0010"
Option  "SHMConfig"     "on"
Option  "EdgeMotionUseAlways" "false"
EndSection

(...)

```

if you have any doubts just post ;)

---

### Post by Mazen on 2007-10-23
Do i need to copy all the section, because i only copied ```
[B][B]Option  "VertEdgeScroll"        "false"
Option  "VertTwoFingerScroll"   "true"[/B][/B]
```but it did not work!

---

### Post by raul_ on 2007-10-25
Sorry for not replying earilier. I really don't know. 

Did the mouse work at all?

---

### Post by Mazen on 2007-10-25
yes that did not change a thing, bt when i changed the whole section it did not boot at all!!lol

---

### Post by raul_ on 2007-10-26
keep in mind that the (...) are not included ;)

Do you have the synaptics driver installed?

---

### Post by Mazen on 2007-10-26
of course the (...) aren't included!!
i didn't install any drivers myself, but it already says Synaptics touchpad in the name, is there anything i should install on my own?

---

### Post by raul_ on 2007-10-27
What about the "driver" field? what does it say? synaptics or mouse?

---

### Post by Mazen on 2007-10-27
synaptics
this is the Setcion from my xorg```
Section "InputDevice"
    Identifier    "Synaptics Touchpad"
    Driver        "synaptics"
    Option        "SendCoreEvents"    "true"
    Option        "Device"        "/dev/psaux"
    Option        "Protocol"        "auto-dev"
    Option        "HorizScrollDelta"    "0"
EndSection
```

---

### Post by raul_ on 2007-10-27
Try adding the delta field as well:

```
Option  "VertScrollDelta" "300"
Option  "VertEdgeScroll"        "false"
Option  "VertTwoFingerScroll"   "true"
```

---

### Post by Mazen on 2007-10-27
the side scroll is barely working! but no two finger scroll!

---

### Post by Mint137 on 2007-11-01
Doesn't seem to work for me. I even tried just copying everything -_-.

---

### Post by raul_ on 2007-11-01
That's odd...What can I say? It works for me, so I guess I can't help you guys :(

---

