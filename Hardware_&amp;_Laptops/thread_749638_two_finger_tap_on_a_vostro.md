---
title: "two finger tap on a vostro"
date: 2008-04-08
forum: Hardware &amp; Laptops
---

### Post by masterclam on 2008-04-08
Well... I have been trying to get this to work for a while now and finally decided to ask for help. I am trying to get the two finger tap on my touchpad to emulate the middle mouse button. The thing is, it doesn't work :). I have modified xorg.conf, changing TapButton2 (as well as 3 and some playing with 1) to 2 (and 3 and 1, etc). None of these work, except TapButton1, which works changing it to any button. Also, two finger scrolling does not seem to work either. I was curious if anyone knows something I don't about the capabilities of the touchpad on a vostro 1400 or if there is something I need to change or a workaround for this to work.

Thanks in advance

P.S. here are my current synclient settings:
Parameter settings:
    LeftEdge             = 102
    RightEdge            = 921
    TopEdge              = 76
    BottomEdge           = 660
    FingerLow            = 15
    FingerHigh           = 39
    MaxTapTime           = 220
    MaxTapMove           = 70
    MaxDoubleTapTime     = 180
    SingleTapTimeout     = 180
    ClickTime            = 100
    FastTaps             = 1
    EmulateMidButtonTime = 75
    VertScrollDelta      = 15
    HorizScrollDelta     = 20
    VertEdgeScroll       = 1
    HorizEdgeScroll      = 1
    VertTwoFingerScroll  = 0
    HorizTwoFingerScroll = 0
    MinSpeed             = 0.7
    MaxSpeed             = 1.2
    AccelFactor          = 0.1
    EdgeMotionMinZ       = 30
    EdgeMotionMaxZ       = 160
    EdgeMotionMinSpeed   = 1
    EdgeMotionMaxSpeed   = 76
    EdgeMotionUseAlways  = 0
    UpDownScrolling      = 1
    LeftRightScrolling   = 1
    UpDownRepeat         = 1
    LeftRightRepeat      = 1
    ScrollButtonRepeat   = 100
    TouchpadOff          = 2
    GuestMouseOff        = 0
    LockedDrags          = 0
    RTCornerButton       = 0
    RBCornerButton       = 0
    LTCornerButton       = 0
    LBCornerButton       = 0
    TapButton1           = 1
    TapButton2           = 0
    TapButton3           = 0
    CircularScrolling    = 0
    CircScrollDelta      = 0.1
    CircScrollTrigger    = 0
    CircularPad          = 0
    PalmDetect           = 0
    PalmMinWidth         = 10
    PalmMinZ             = 200
    CoastingSpeed        = 0
    PressureMotionMinZ   = 30
    PressureMotionMaxZ   = 160
    PressureMotionMinFactor = 1
    PressureMotionMaxFactor = 1

Edit: hope this is in the right spot, if not im sure you mods will take care of it, thanks

---

### Post by masterclam on 2008-04-13
bump :)

---

### Post by irieken on 2008-04-17
Second bump!:)

---

### Post by floyd4one on 2008-04-26
i was under the impression that the hardware on dell laptops did not support multi-touch capabilities. although i believe dell will soon be coming out with some models that will have this. i could be wrong though.

---

### Post by omegamike3 on 2008-05-19
> **floyd4one said:**
> i was under the impression that the hardware on dell laptops did not support multi-touch capabilities. although i believe dell will soon be coming out with some models that will have this. i could be wrong though.

Indeed, there isn't any multi-touch, that I'm aware of. I have a 1400 and by default, on an 8.04 install, you can use the scrolls at the side of the trackpad (horizontal has to be turned on in the mouse prefs) you can middle click by clicking both the left and right buttons at the same time (easier done than it sounds) and you can tap a right click on the pad by clicking in the lower right-hand corner (although at that point you're practically at the button anyhow :P)

---

