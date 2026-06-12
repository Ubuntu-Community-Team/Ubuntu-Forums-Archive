---
title: "How to have both multitouch and edge scrolling enabled?"
date: 2012-02-27
forum: Hardware
---

### Post by jerm1027 on 2012-02-27
So on my Windows partition, the synaptics driver is able to do two-finger scrolling as well as edge scrolling, so I have the option to do either or at any given time. I rather like the convenience, but I haven't found a way to do this with Ubuntu. Going through the settings manager, it seems to be one or the other, but I would like both. Any help to enable both would be much appreciated. Thanks

Specs:
Acer Aspire One 722-0473
AMD Fusion C-60 APU (dual-core 1GHz/1.33GHz w/ Radeon 6290)
2GB DDR3 1066
64GB Crucial M4
Windows 7 Ultimate x64 | Ubuntu 11.10 x64

Other:
Synaptics multitouch trackpad

---

### Post by ahsan101 on 2012-02-27
Whats the output of synclient -l , are you sure all the synaptic touchpad drivers are loaded as well?

---

### Post by jerm1027 on 2012-02-28
> **ahsan101 said:**
> Whats the output of synclient -l , are you sure all the synaptic touchpad drivers are loaded as well?

Here is the output
```
jeremy@jeremy-AO722:~$ synclient -l
Parameter settings:
    LeftEdge                = 1773
    RightEdge               = 5471
    TopEdge                 = 1665
    BottomEdge              = 4829
    FingerLow               = 24
    FingerHigh              = 29
    FingerPress             = 255
    MaxTapTime              = 180
    MaxTapMove              = 248
    MaxDoubleTapTime        = 180
    SingleTapTimeout        = 180
    ClickTime               = 100
    FastTaps                = 0
    EmulateMidButtonTime    = 75
    EmulateTwoFingerMinZ    = 280
    EmulateTwoFingerMinW    = 6
    VertScrollDelta         = 113
    HorizScrollDelta        = 113
    VertEdgeScroll          = 1
    HorizEdgeScroll         = 1
    CornerCoasting          = 0
    VertTwoFingerScroll     = 0
    HorizTwoFingerScroll    = 0
    MinSpeed                = 1
    MaxSpeed                = 1.75
    AccelFactor             = 0.0353482
    TrackstickSpeed         = 40
    EdgeMotionMinZ          = 29
    EdgeMotionMaxZ          = 159
    EdgeMotionMinSpeed      = 1
    EdgeMotionMaxSpeed      = 452
    EdgeMotionUseAlways     = 0
    TouchpadOff             = 0
    LockedDrags             = 0
    LockedDragTimeout       = 5000
    RTCornerButton          = 2
    RBCornerButton          = 3
    LTCornerButton          = 0
    LBCornerButton          = 0
    TapButton1              = 1
    TapButton2              = 3
    TapButton3              = 2
    ClickFinger1            = 1
    ClickFinger2            = 1
    ClickFinger3            = 1
    CircularScrolling       = 0
    CircScrollDelta         = 0.1
    CircScrollTrigger       = 0
    CircularPad             = 0
    PalmDetect              = 0
    PalmMinWidth            = 9
    PalmMinZ                = 199
    CoastingSpeed           = 20
    CoastingFriction        = 50
    PressureMotionMinZ      = 29
    PressureMotionMaxZ      = 159
    PressureMotionMinFactor = 1
    PressureMotionMaxFactor = 1
    ResolutionDetect        = 1
    GrabEventDevice         = 1
    TapAndDragGesture       = 1
    AreaLeftEdge            = 0
    AreaRightEdge           = 0
    AreaTopEdge             = 0
    AreaBottomEdge          = 0

```

I'm not sure if you misread or not. Both work fine, but Ubuntu will only enable one at a time. So if I want multi-touch/two-finger scrolling, it disables edge scrolling and vice versa. I want both enabled at the same time.

Here is a screen:
[IMG]http://i.imgur.com/R6sBO.png[/IMG]

As you can see, there is no option to have both enabled.

---

### Post by ahsan101 on 2012-02-28
Try to run this script from root and reload mouse and tell me if it works 

> 
***#!/bin/sh***
 ***synclient VertTwoFingerScroll=1***
 ***synclient HorizTwoFingerScroll=1***
 ***synclient EmulateTwoFingerMinW=5***
 ***synclient EmulateTwoFingerMinZ=48***
[I][B]synclient VertEdgeScroll          = 1 
synclient HorizEdgeScroll = 1
[/B][/I] 


i think it works fine!

---

### Post by jerm1027 on 2012-02-28
> **ahsan101 said:**
> Try to run this script from root and reload mouse and tell me if it works 



i think it works fine!

It works fantabulously. Thanks :D

:idea: BTW - I uploaded the script, just in case anyone else has this problem.. :)

---

