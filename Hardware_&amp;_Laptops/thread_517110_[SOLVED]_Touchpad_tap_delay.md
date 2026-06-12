---
title: "[SOLVED] Touchpad tap delay"
date: 2007-08-04
forum: Hardware &amp; Laptops
---

### Post by isaacj87 on 2007-08-04
Hello all,

I got my synaptic touchpad working! But I was noticing that there's a delay between the actual tap of my fingers to the button on the screen itself. To clarify, when I tap it takes about a second before the button is  pressed...here's the section of my xorg.conf file related to my synaptic touchpad...can someone tell me how to fix this? 

> Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents" "true"
        Option          "Device" "/dev/psaux"
        Option          "Protocol" "auto-dev"
        Option          "SHMConfig" "on"
# Touchpad Configuration
        Option          "LeftEdge" "1900"
        Option          "RightEdge" "5300"
        Option          "TopEdge" "1400"
        Option          "BottomEdge" "4500"
        Option          "FingerLow" "25"
        Option          "FingerHigh" "30"
        Option          "MaxTapTime" "140"
        Option          "MaxTapMove" "220"
        Option          "MaxDoubleTapTime" "180"   
        Option          "VertScrollDelta" "100"
        Option          "HorizScrollDelta" "0"  
        Option          "MinSpeed" "0.10"
        Option          "MaxSpeed" "0.25"
        Option          "AccelFactor" "0.0011"
        Option          "TapButton1" "0"
        Option          "TapButton2" "1"
        Option          "TapButton3" "3"
EndSection


PS. I tried shorting the "TapMaxTime" to 140 but it doesn't do anything.

---

### Post by ugm6hr on 2007-08-04
For complete information:
```
man synaptics
```

Things worth trying (in order, or possibly in combination):
> Option "FastTaps" "1"
> Option "SingleTapTimeout" "180"

---

### Post by isaacj87 on 2007-08-04
Success!

It was definitely the FastTaps option..thanks you're a life saver :)

---

### Post by isaacj87 on 2007-08-04
Sorry to double post, I'm going to share my xorg.conf synaptic settings if anyone needs them...

> Section "InputDevice"
Identifier "Synaptics Touchpad"
Driver "synaptics"
Option "SendCoreEvents" "true"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
Option "SHMConfig" "on"
# Touchpad Configuration
Option "LeftEdge" "1900"
Option "RightEdge" "5300"
Option "TopEdge" "1400"
Option "BottomEdge" "4500"
Option "FingerLow" "25"
Option "FingerHigh" "30"
Option "MaxTapTime" "180"
Option "MaxTapMove" "220"
Option "MaxDoubleTapTime" "180"
Option "VertScrollDelta" "100"
Option "HorizScrollDelta" "0"
Option "MinSpeed" "0.10"
Option "MaxSpeed" "0.25"
Option "AccelFactor" "0.0011"
Option "TapButton1" "0"
Option "TapButton2" "1"
Option "TapButton3" "3"
Option "FastTaps" "1"
EndSection

---

### Post by ugm6hr on 2007-08-04
Perhaps you might like to share your entire xorg.conf for the laptop? - see the link on my signature.

---

### Post by isaacj87 on 2007-08-04
Haha...I will..I've got an Acer Aspire 1642WLMi

I'll post it later on today. :)

---

