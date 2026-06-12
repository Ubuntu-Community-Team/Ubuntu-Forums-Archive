---
title: "Cannot modify Stnaptics Touchpad behavior"
date: 2008-03-03
forum: Hardware &amp; Laptops
---

### Post by djrh on 2008-03-03
I've searched a lot before posting, but nothing seemed to be able to help.

I would like to have the tapping function on my touchpad disabled (using it ONLY for cursor movement) because the cursor jumping DRIVES ME CRAZY, but cannot seem to modify its behavior.

I'have edited the xorg.conf to set "SHMConfig" to "on", and this is the most I can do.

Ever since I have tried setting  

TapButton1, TapButton2, TapButton3 to "0"

TouchpadOff to "2" (and even "0")

“MaxTapTime” and “MaxTapMove” to “0&#8243;

but NOTHING seems to modify its behavior.

Could anyone assist?
Thanks a lot!

PS
My  synclient -l is as follows:
```

    LeftEdge             = 1872
    RightEdge            = 5072
    TopEdge              = 1712
    BottomEdge           = 4144
    FingerLow            = 25
    FingerHigh           = 30
    MaxTapTime           = 0
    MaxTapMove           = 0
    MaxDoubleTapTime     = 180
    SingleTapTimeout     = 180
    ClickTime            = 100
    FastTaps             = 0
    EmulateMidButtonTime = 75
    VertScrollDelta      = 60
    HorizScrollDelta     = 0
    VertEdgeScroll       = 1
    HorizEdgeScroll      = 0
    VertTwoFingerScroll  = 0
    HorizTwoFingerScroll = 0
    MinSpeed             = 0.0822368
    MaxSpeed             = 0.197368
    AccelFactor          = 0.00164474
    EdgeMotionMinZ       = 30
    EdgeMotionMaxZ       = 160
    EdgeMotionMinSpeed   = 1
    EdgeMotionMaxSpeed   = 304
    EdgeMotionUseAlways  = 0
    UpDownScrolling      = 1
    LeftRightScrolling   = 1
    UpDownRepeat         = 1
    LeftRightRepeat      = 1
    ScrollButtonRepeat   = 100
    TouchpadOff          = 2
    GuestMouseOff        = 0
    LockedDrags          = 0
    RTCornerButton       = 2
    RBCornerButton       = 3
    LTCornerButton       = 0
    LBCornerButton       = 0
    TapButton1           = 0
    TapButton2           = 0
    TapButton3           = 0
    CircularScrolling    = 0
    CircScrollDelta      = 0.1
    CircScrollTrigger    = 0
    CircularPad          = 0
    PalmDetect           = 1
    PalmMinWidth         = 10
    PalmMinZ             = 200
    CoastingSpeed        = 0
    PressureMotionMinZ   = 30
    PressureMotionMaxZ   = 160
    PressureMotionMinFactor = 1
    PressureMotionMaxFactor = 1

```

---

### Post by AmericanYellow on 2008-03-04
Sorry buddy for your troubles. I think I know how you can fix this problem.

If you are using Ubuntu (assuming Gusty Gibbon, I haven't try hardy yet), do the following:

Go System --> Preferences --> Mouse

There will be a tab that says "Touchpad". You should see an option that say "Tap to click". Uncheck the box and you should see that you problem is gone. Have fun!:guitar:

---

### Post by djrh on 2008-03-05
thanks for your input!

Did as you suggested (I do have Gutsy) - still no go
even unchecked vertical scrolling - same issue

please help me not to smash my laptop ](*,)

---

### Post by AmericanYellow on 2008-03-05
> please help me not to smash my laptop

lol. What are your specs?

---

### Post by djrh on 2008-03-09
Acer 5920G:
T5250, 8600 GT w/ HDMI, 4g PC5300, HD-DVD (already obsolete :( I HATE SONY :mad: )

I first tried the 64bit Ubuntu, but could not make aircrack work under the x64 with Intel 3945 drivers. Hence, I was forced to go 32-bit Ubu. It's dual-boot with Vista x64 Premium.

What sucks the most is that under Vista I managed to disable the tapping, so now I'm stuck working in Vista :-k

BTW, after some research, I found this:
[http://www.compass.com/tpconfig/touchpad](http://www.compass.com/tpconfig/touchpad)

Will try it and let you know.

---

### Post by jlh68 on 2008-03-10
On my Acer I had to add gsynaptic.  This synaptic is not related to the synaptic package loader.

After loading gsynaptic, I had to add the touchpad info to X-org.conf. Which you had done some of it.

Then you can open the touchpad pull down menu and check or uncheck the tapping function.

[http://ubuntuforums.org/showthread.php?t=372953](http://ubuntuforums.org/showthread.php?t=372953)

---

