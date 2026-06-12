---
title: "Slow tap response on ALPS touchpad"
date: 2006-09-15
forum: Hardware &amp; Laptops
---

### Post by havenoclu on 2006-09-15
Hey there. I haven't been able to find anyone with this particular problem, so here it is:

I've gotten my alps touchpad (dell 600m) working almost perfect. It has all the great functionality, but one gripe remains. When I tap to click (which I prefer using) it seems to be somewhat laggy. I'll click..and then there is a noticable lag time until the click actually occurs. I feel like there has to be a way to fix this...as the touchpad clicks are instantaneous in windows (hate to compare :). Below is part of my xorg.conf. Is there anything I should add/remove/change? Thanks!

```
Section "InputDevice"
        Identifier  "Touchpad"
        Driver      "synaptics"
        Option      "SendCoreEvents" "true"
        Option      "Device" "/dev/input/event2"
        Option      "Protocol" "event"
        Option      "LeftEdge" "130"
        Option      "RightEdge" "840"
        Option      "TopEdge" "130"
        Option      "BottomEdge" "640"
        Option      "FingerLow" "7"
        Option      "FingerHigh" "8"
        Option      "MaxTapTime" "270"
        Option      "MaxTapMove" "110"
        Option      "EmulateMidButtonTime" "75"
        Option      "VertScrollDelta" "20"
        Option      "HorizScrollDelta" "20"
        Option      "MinSpeed" "0.60"
        Option      "MaxSpeed" "1.10"
        Option      "AccelFactor" "0.030"
        Option      "EdgeMotionMinSpeed" "200"
        Option      "EdgeMotionMaxSpeed" "200"
        Option      "UpDownScrolling" "1"
        Option      "CircularScrolling" "1"
        Option      "CircScrollDelta" "0.1"
        Option      "CircScrollTrigger" "2"
        Option      "SHMConfig" "on"
        Option      "Emulate3Buttons" "on"
        Option      "GuestMouseOff" "0"
        Option      "ClickTime" "0"
EndSection
```

---

### Post by havenoclu on 2006-09-16
Anyone?

---

### Post by havenoclu on 2006-09-19
Could someone with a proper working/responsive alps touchpad paste there xorg.conf?? Im finding it hard to believe that I'm the only one with this problem. Thanks in advance!

---

### Post by sandeep.rajarao on 2006-09-19
Dell 640m - tapping on the pad instantly recognized as click.

Section "InputDevice"
  Identifier  "Synaptics Touchpad"
  Driver    "synaptics"
  Option    "SendCoreEvents"  "true"
  Option    "Device"    "/dev/psaux"
  Option    "Protocol"    "auto-dev"
  Option    "HorizScrollDelta"  "0"
EndSection

Sandeep

---

### Post by havenoclu on 2006-09-19
> **sandeep.rajarao said:**
> Dell 640m - tapping on the pad instantly recognized as click.

Section "InputDevice"
  Identifier  "Synaptics Touchpad"
  Driver    "synaptics"
  Option    "SendCoreEvents"  "true"
  Option    "Device"    "/dev/psaux"
  Option    "Protocol"    "auto-dev"
  Option    "HorizScrollDelta"  "0"
EndSection

Sandeep

Thanks. I'll give it a shot after work and reply with the outcome.

---

### Post by bthoward on 2008-04-21
I have something very similar:

```

Section "InputDevice"
        Identifier  "Synaptics Touchpad"
        Driver      "synaptics"
        Option      "SendCoreEvents" "true"
        Option      "Device" "/dev/psaux"
        Option      "Protocol" "auto-dev"
        Option      "HorizEdgeScroll" "0"
EndSection

``` 

yet I still have the laggy taps...  This is on a Dell D610 running Ubuntu 8.04.

---

