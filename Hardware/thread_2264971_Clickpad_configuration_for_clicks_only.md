---
title: "Clickpad configuration for clicks only"
date: 2015-02-11
forum: Hardware
---

### Post by jcerruti on 2015-02-11
I have a Lenovo Thinkpad T440s which includes the new Synaptics Clickpad which basically bundles buttons and trackpad all in the same surface. It is a single button whose function depends on where the finger was when you clicked.

In my case, I am very used to the all system in which the buttons where separated form the trackpad, and I normally only use the trackpoint with the top buttons.

After a lot of fighting, I sort of have things working, except for one minor detail which is driving me crazy and I can´t figure out how to configure: If I perform a regular left click by pressing down and clicking the clickpad but then leave my finger lightly touching the  surface, I get a  ´click and drag´ action instead of a regular click. 

I am doing this on Ubuntu 14.10

Is there any way to disable dragging on the top surface (or the whole surface for that matter) while keeping the possibility to click?

Here are my current synclient settings:

```

Parameter settings:
    LeftEdge                = 1310
    RightEdge               = 4826
    TopEdge                 = 2220
    BottomEdge              = 4636
    FingerLow               = 25
    FingerHigh              = 30
    MaxTapTime              = 180
    MaxTapMove              = 2000
    MaxDoubleTapTime        = 180
    SingleTapTimeout        = 180
    ClickTime               = 100
    EmulateMidButtonTime    = 0
    EmulateTwoFingerMinZ    = 282
    EmulateTwoFingerMinW    = 7
    VertScrollDelta         = 99
    HorizScrollDelta        = 99
    VertEdgeScroll          = 0
    HorizEdgeScroll         = 0
    CornerCoasting          = 0
    VertTwoFingerScroll     = 1
    HorizTwoFingerScroll    = 1
    MinSpeed                = 1
    MaxSpeed                = 1.75
    AccelFactor             = 0.0403307
    TouchpadOff             = 2
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
    ClickFinger2            = 0
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
    PressureMotionMinZ      = 80
    PressureMotionMaxZ      = 160
    PressureMotionMinFactor = 1
    PressureMotionMaxFactor = 1
    ResolutionDetect        = 1
    GrabEventDevice         = 0
    TapAndDragGesture       = 0
    AreaLeftEdge            = 0
    AreaRightEdge           = 0
    AreaTopEdge             = 3200
    AreaBottomEdge          = 6000
    HorizHysteresis         = 1000
    VertHysteresis          = 1000
    ClickPad                = 1
    RightButtonAreaLeft     = 3476
    RightButtonAreaRight    = 0
    RightButtonAreaTop      = 0
    RightButtonAreaBottom   = 0
    MiddleButtonAreaLeft    = 2863
    MiddleButtonAreaRight   = 3272
    MiddleButtonAreaTop     = 0
    MiddleButtonAreaBottom  = 0


```

---

### Post by jcerruti on 2015-02-11
Another way to ask this (after looking at what events are being generated using xev) is: how can I configure the Clickpad so that the ButtonRelease event is triggered right after the physical click is done and not after I lift my finger from the touchpad (which is what currently happens)

---

### Post by tgalati4 on 2015-02-12
Try enabling vertical edge scrolling.  That will at least filter out vertical swipes.  If that is not enough, then try enabling horizontal edge scrolling.  Sometimes there are touchpad settings in BIOS that you can set.

Otherwise, print out your settings, and take careful notes on how the behavior changes as you change each one, individually.

My Thinkpad T43p has two sets of buttons, on top and on the bottom of the trackpad.  That's an arrangement that I really like.

---

### Post by jcerruti on 2015-02-12
Thanks tgalati4 for the ideas.

Unfortunately enabling vert or horiz scroll didn't change the behavior of the click events in any way.

I had been playing with the settings individually for a long time before posting. At this point I am not sure what else I could change.

---

