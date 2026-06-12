---
title: "Aspire One 722 - Touchpad way to sensative (fast)"
date: 2012-03-21
forum: Hardware
---

### Post by kleeman7 on 2012-03-21
Got everything running great, except the touchpad moves way to fast, its like super speed. I have searched around and have not found anything that has helped. The touchpad settings are set to completely low, and nothing seems to help.

Any help would be greatly appreciated.

Im trying to convert my wife, and thats the only thing she cant live with.

---

### Post by ajgreeny on 2012-03-21
Try the command ```
synclient -l
``` in terminal and copy back here the output you get, and it may be possible to reduce the sensitivity, or speed of movement.  As this is a laptop, and if it is a synaptics touchpad synclient should be installed and loaded by default.  If it is not a synaptics touchpad it may be more difficult, but let's go one step at a time.

---

### Post by kleeman7 on 2012-03-21
Parameter settings:
    LeftEdge                = 1773
    RightEdge               = 5471
    TopEdge                 = 1665
    BottomEdge              = 4829
    FingerLow               = 25
    FingerHigh              = 30
    FingerPress             = 256
    MaxTapTime              = 180
    MaxTapMove              = 248
    MaxDoubleTapTime        = 180
    SingleTapTimeout        = 180
    ClickTime               = 100
    FastTaps                = 0
    EmulateMidButtonTime    = 75
    EmulateTwoFingerMinZ    = 282
    EmulateTwoFingerMinW    = 7
    VertScrollDelta         = 113
    HorizScrollDelta        = 113
    VertEdgeScroll          = 1
    HorizEdgeScroll         = 0
    CornerCoasting          = 0
    VertTwoFingerScroll     = 0
    HorizTwoFingerScroll    = 0
    MinSpeed                = 1
    MaxSpeed                = 1.75
    AccelFactor             = 0.0353482
    TrackstickSpeed         = 40
    EdgeMotionMinZ          = 30
    EdgeMotionMaxZ          = 160
    EdgeMotionMinSpeed      = 1
    EdgeMotionMaxSpeed      = 452
    EdgeMotionUseAlways     = 0
    TouchpadOff             = 1
    LockedDrags             = 0
    LockedDragTimeout       = 5000
    RTCornerButton          = 0
    RBCornerButton          = 0
    LTCornerButton          = 0
    LBCornerButton          = 0
    TapButton1              = 0
    TapButton2              = 0
    TapButton3              = 0
    ClickFinger1            = 1
    ClickFinger2            = 1
    ClickFinger3            = 1
    CircularScrolling       = 0
    CircScrollDelta         = 0.1
    CircScrollTrigger       = 0
    CircularPad             = 0
    PalmDetect              = 0
    PalmMinWidth            = 10
    PalmMinZ                = 200
    CoastingSpeed           = 20
    CoastingFriction        = 50
   PressureMotionMinZ      = format mismatch (32)
   PressureMotionMaxZ      = format mismatch (32)
    PressureMotionMinFactor = 1
    PressureMotionMaxFactor = 1
    GrabEventDevice         = 1
    TapAndDragGesture       = 1
    AreaLeftEdge            = 0
    AreaRightEdge           = 0
    AreaTopEdge             = 0
    AreaBottomEdge          = 0

---

### Post by ajgreeny on 2012-03-22
The settings you need to change may be possible with **gpointing-device-settings** from the repos.  Failing that the synclient command should be able to do it with a bit of trial and error by changing your entries listed for 
```
MinSpeed                = 1
MaxSpeed                = 1.75
AccelFactor             = 0.0353482
```Use commands like ```
synclient MinSpeed=1
synclient MaxSpeed=1.25
synclient AccelFactor=0.02
```and play around with the figures till you get what you want.  You will then need to make a script that you add to the startup applications so it is executed at each session start.

---

### Post by kleeman7 on 2012-03-22
> **ajgreeny said:**
> The settings you need to change may be possible with **gpointing-device-settings** from the repos.  Failing that the synclient command should be able to do it with a bit of trial and error by changing your entries listed for 
```
MinSpeed                = 1
MaxSpeed                = 1.75
AccelFactor             = 0.0353482
```Use commands like ```
synclient MinSpeed=1
synclient MaxSpeed=1.25
synclient AccelFactor=0.02
```and play around with the figures till you get what you want.  You will then need to make a script that you add to the startup applications so it is executed at each session start.

That worked great. The last question I have is how do I make a start up script?

the settings I chose was.
MinSpeed=1
MaxSpeed=1.10
AccelFactor=0.01

---

### Post by ajgreeny on 2012-03-22
Ok here it is
```
#!/bin/bash
synclient MinSpeed=1
synclient MaxSpeed=1.10
synclient AccelFactor=0.01
```
Copy that into a txt file and save it as touchpad.sh in your home.  Make it executable with ```
chmod +x touchpad.sh
``` (or right click it in nautilus and set it as executable in the permissions tab) then add it, with full path /home/user/touchpad.sh to your startup applications list.

---

### Post by kleeman7 on 2012-03-22
Thanks works great. Its it excited to have a nice system running, I have never had a Linux build running this well before. I have been playing with Linux for years, but never been able to keep it due to little things not working for me. Thanks again.

---

