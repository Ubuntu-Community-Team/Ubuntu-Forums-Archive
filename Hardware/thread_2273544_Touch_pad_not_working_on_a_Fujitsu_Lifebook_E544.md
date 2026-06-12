---
title: "Touch pad not working on a Fujitsu Lifebook E544"
date: 2015-04-13
forum: Hardware
---

### Post by robert48 on 2015-04-13
Hello

Just bought a Fujitsu Lifebook E544, took out the windows HDD drive and dropped in a SSD, loaded Ubuntu, cracking performance....then noticed touch pad and left/right buttons not working. Ordinary USB mouse works, FN + FunctionKey4 which shows a little mouse icon does not switch on the touch pad, even when the USB mouse is not plugged in (on reboot or if taken out while OS up).

With the original HDD in, Windows 7 pro, the touch pad works as expected. Is it possible to get the touch pad working with Ubuntu?

---

### Post by Pilot6 on 2015-04-14
That depends on what touchpad is installed in this laptop.

---

### Post by robert48 on 2015-04-14
I've had a look with ```
sudo lshw
``` and can't see anything obvious that refers to a touchpad. How would I find out about the touchpad?

---

### Post by robert48 on 2015-04-15
Ubuntu shows the touchpad as "ETPS/2 Elantech Touchpad"

---

### Post by robert48 on 2015-04-15
I don't understand the signigicance of the output but it is recognised here:-

lcf@lcf-LIFEBOOK-E544:~$ xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; ETPS/2 Elantech Touchpad                    id=14    [slave  pointer  (2)]
&#9116;   &#8627; PixArt USB Optical Mouse                    id=11    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Fujitsu FUJ02E3                             id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Fujitsu FUJ02B1                             id=8    [slave  keyboard (3)]
    &#8627; Power Button                                id=9    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=10    [slave  keyboard (3)]
    &#8627; FJ Camera                                   id=12    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=13    [slave  keyboard (3)]
lcf@lcf-LIFEBOOK-E544:~$ synclient -l
Parameter settings:
    LeftEdge                = 90
    RightEdge               = 2181
    TopEdge                 = 70
    BottomEdge              = 1234
    FingerLow               = 1
    FingerHigh              = 1
    MaxTapTime              = 180
    MaxTapMove              = 115
    MaxDoubleTapTime        = 180
    SingleTapTimeout        = 180
    ClickTime               = 100
    EmulateMidButtonTime    = 75
    EmulateTwoFingerMinZ    = 282
    EmulateTwoFingerMinW    = 7
    VertScrollDelta         = -52
    HorizScrollDelta        = -52
    VertEdgeScroll          = 0
    HorizEdgeScroll         = 0
    CornerCoasting          = 0
    VertTwoFingerScroll     = 1
    HorizTwoFingerScroll    = 1
    MinSpeed                = 1
    MaxSpeed                = 1.75
    AccelFactor             = 0.0763942
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
    HorizHysteresis         = 13
    VertHysteresis          = 13
    ClickPad                = 0

---

### Post by robert48 on 2015-05-15
For those with similar problems upgrade to Vivid to solve them.

---

