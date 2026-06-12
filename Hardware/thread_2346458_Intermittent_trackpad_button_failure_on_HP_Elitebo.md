---
title: "Intermittent trackpad button failure on HP Elitebook 2570P, 14.04"
date: 2016-12-15
forum: Hardware
---

### Post by bookherd on 2016-12-15
My laptop's trackpad buttons sometimes stop responding in erratic ways. Sometimes the right-click button doesn't work, sometimes none of the buttons work (I have top left, top right, bottom left, and bottom right), sometimes clicking via the trackpad also doesn't work (though moving the cursor via trackpad still does). Sometimes the right-click menu pops up at random intervals, and things that normally highlight when I mouse over them stop doing so.  

Usually a reboot or two fixes the problem, but today while I was trying to take notes for a meeting, I rebooted repeatedly and the right-click menu still kept popping up, while my cursor refused to change to the proper icon (text or pointer) and things didn't highlight when I hovered over them.  Now it's working again (after one reboot), but I don't know for how long.

I suspect this is a software issue, rather than hardware, but I'm not certain.

Here is my synclient output, if that helps:
```
Parameter settings:
    LeftEdge                = 1775
    RightEdge               = 5511
    TopEdge                 = 1668
    BottomEdge              = 4864
    FingerLow               = 25
    FingerHigh              = 30
    MaxTapTime              = 180
    MaxTapMove              = 251
    MaxDoubleTapTime        = 100
    SingleTapTimeout        = 180
    ClickTime               = 100
    EmulateMidButtonTime    = 75
    EmulateTwoFingerMinZ    = 282
    EmulateTwoFingerMinW    = 7
    VertScrollDelta         = 114
    HorizScrollDelta        = 114
    VertEdgeScroll          = 0
    HorizEdgeScroll         = 0
    CornerCoasting          = 0
    VertTwoFingerScroll     = 1
    HorizTwoFingerScroll    = 1
    MinSpeed                = 1
    MaxSpeed                = 1.75
    AccelFactor             = 0.0349956
    TouchpadOff             = 2
    LockedDrags             = 0
    LockedDragTimeout       = 5000
    RTCornerButton          = 2
    RBCornerButton          = 3
    LTCornerButton          = 0
    LBCornerButton          = 0
    TapButton1              = 1
    TapButton2              = 3
    TapButton3              = 0
    ClickFinger1            = 1
    ClickFinger2            = 1
    ClickFinger3            = 0
    CircularScrolling       = 0
    CircScrollDelta         = 0.1
    CircScrollTrigger       = 0
    CircularPad             = 0
    PalmDetect              = 0
    PalmMinWidth            = 10
    PalmMinZ                = 200
    CoastingSpeed           = 20
    CoastingFriction        = 50
    PressureMotionMinZ      = 30
    PressureMotionMaxZ      = 160
    PressureMotionMinFactor = 1
    PressureMotionMaxFactor = 1
    ResolutionDetect        = 1
    GrabEventDevice         = 0
    TapAndDragGesture       = 1
    AreaLeftEdge            = 0
    AreaRightEdge           = 0
    AreaTopEdge             = 0
    AreaBottomEdge          = 0
    HorizHysteresis         = 8
    VertHysteresis          = 8
    ClickPad                = 0

```

I found info here [https://ubuntuforums.org/showthread.php?t=1401645]("https://ubuntuforums.org/showthread.php?t=1401645") that suggests updating xserver-xorg-input-synaptics, but it's from 2010, and my Software Center indicates that "Synaptics TouchPad driver for X.Org server" is not even installed. Could doing so help, or would it just make things worse?  Or should I change synclient settings? Or something else entirely? I don't have a working backup computer, so I can't afford to mess this one up.

---

### Post by bookherd on 2016-12-22
This issue subsided gradually over the course of a few days.  I'm now convinced it was a hardware problem after all.  I have a soft-sided case for this computer, and when carrying it in the case, it's very easy to grip the laptop right along the edge where the touchpad "mouse" buttons are.  I found myself doing so earlier this week, and suspect that same grip may previously have caused some lasting compression in the buttons.  Now I make sure to grip it by the battery edge instead.  So far, so good.  If this problem re-emerges and/or I learn more, I'll return to update here.

---

### Post by bookherd on 2017-11-17
After an absence of almost a year, this problem has returned. I've pried up the mouse buttons and cleaned under them.  Still, I no longer believe this is a hardware issue, because one frequent result is that I can click on some things on the screen but not others -- for example, links in the browser window, but not in the left menu bar with the floaty buttons (I forgot the official name for this).  Or, right now, I can click to move the cursor around this window I'm typing in, and on tabs within the browser window, but nothing in the top or left menu bars... and the window control option buttons (close, hide, etc) fail to appear when I mouse over the top of the screen/window (the browser window size is maximum).  

I've googled the crap out of this problem and have found nothing like it anywhere.  Any suggestions out there?

---

