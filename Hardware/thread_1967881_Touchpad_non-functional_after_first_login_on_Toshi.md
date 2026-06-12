---
title: "Touchpad non-functional after first login on Toshiba NB505"
date: 2012-04-28
forum: Hardware
---

### Post by ismarc on 2012-04-28
Hey folks,
I have a Toshiba NB505 netbook and previously had Maverick installed.  I did a fresh install (including completely clean /home partition) of 12.04 and everything went well (including wifi working out of the box now!).  After the install completed, got to login screen, everything working fine.

Shortly after logging in (around when I hit alt-f2 to launch a terminal), the touchpad completely stopped responding.

Troubleshooting steps completed including testing as well as rebooting after each step and verifying the config change stayed:
# Had no effect
$ synclient TouchpadOff=0
# Had no effect
$ gconftool-2 --set --type boolean /desktop/gnome/peripherals/touchpad/touchpad_enabled true
# Had no effect
Under System Settings -> Mouse and Touchpad -> Touchpad tab -> uncheck Disable touchpad while typing

I've also verified the latest xserver-xorg-input-synaptics is installed.

In a virtual terminal (alt-ctrl-f1) evtest /dev/input/eventN (the appropriate number based on what was listed in dmesg for the Synaptics touchpad) shows no events at all from the device.

Xorg.0.log shows no errors (just the initial Synaptics device discovered for eventN and then again for mouseN).

The key combination to turn on/off the touchpad (Fn+F9) does not have any effect when all the other Fn combinations seem to work (wifi, numpad, brightness, mute/unmute).  The BIOS doesn't have an indicator for the touchpad or an option to enable/disable it there.

One interesting point I've noticed is that on every boot, the eventN corresponding to the touchpad increments by 1 (it's now up to event10).

For completeness:
$ synclient -l
Parameter settings:
    LeftEdge                = 1761
    RightEdge               = 5323
    TopEdge                 = 1632
    BottomEdge              = 4394
    FingerLow               = 25
    FingerHigh              = 30
    FingerPress             = 256
    MaxTapTime              = 180
    MaxTapMove              = 230
    MaxDoubleTapTime        = 180
    SingleTapTimeout        = 180
    ClickTime               = 100
    FastTaps                = 0
    EmulateMidButtonTime    = 75
    EmulateTwoFingerMinZ    = 282
    EmulateTwoFingerMinW    = 7
    VertScrollDelta         = 104
    HorizScrollDelta        = 104
    VertEdgeScroll          = 1
    HorizEdgeScroll         = 0
    CornerCoasting          = 0
    VertTwoFingerScroll     = 1
    HorizTwoFingerScroll    = 0
    MinSpeed                = 1
    MaxSpeed                = 1.75
    AccelFactor             = 0.0381825
    TrackstickSpeed         = 40
    EdgeMotionMinZ          = 30
    EdgeMotionMaxZ          = 160
    EdgeMotionMinSpeed      = 1
    EdgeMotionMaxSpeed      = 419
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
    GrabEventDevice         = 1
    TapAndDragGesture       = 1
    AreaLeftEdge            = 0
    AreaRightEdge           = 0
    AreaTopEdge             = 0
    AreaBottomEdge          = 0
    HorizHysteresis         = 26
    VertHysteresis          = 26
    ClickPad                = 0

$ grep -A 9 -B 2 -i touch /proc/bus/input/devices 

I: Bus=0011 Vendor=0002 Product=0007 Version=01b1
N: Name="SynPS/2 Synaptics TouchPad"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input10
U: Uniq=
H: Handlers=mouse1 event10 
B: PROP=9
B: EV=b
B: KEY=6420 0 30000 0 0 0 0 0 0 0 0
B: ABS=2608000 11000003

I'm really stuck as to where to look next, having gone through walls of bug reports where the listed workarounds had no effect and/or the bug listed as fixed.

I'm a developer and more than comfortable building any particular components, applying patches and advanced troubleshooting if necessary.

I'm cross-posting to ubuntu-users as well.  If I find a solution, will update here.

---

