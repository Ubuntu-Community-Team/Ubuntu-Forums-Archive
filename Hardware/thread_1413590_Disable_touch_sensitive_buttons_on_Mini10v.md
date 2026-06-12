---
title: "Disable touch sensitive buttons on Mini10v"
date: 2010-02-22
forum: Hardware
---

### Post by ArkAngel06 on 2010-02-22
Hi guys, I have a weird problem with my new Dell Mini10v touchpad. I am running Ubuntu Netbook Remix 9.10. On the Mini10v, Dell made the right click and left click buttons part of the touchpad, and they are also touch sensitive. This makes it impossible to hold left click to highlight text, drag and drop, etc. If you are holding left click and touch anywhere else on the pad, the cursor will shoot to the top of the screen. From searching this doesn't seem to be a problem for most people once the correct driver is installed.

I have the correct driver installed (xorg-input-synaptic). Now what makes my problem really weird is this: It works absolutely correct half the time. The buttons will not be touch sensitive, and it works perfectly. But the other half of the time it will be as described in the first paragraph, with sensitive buttons. It changes after reboots, and shutdowns. It is completely random. Sometimes I have to restart 4 or 5 times to get it working right again. Then sometimes it wont be a problem for a few sessions. Why would it work sometimes, and not others?

I have tried using "synclient BottomEdge=XXXX", but it doesnt seem to do anything. "XXXX" is anything between 2000 - 100000. Nothing seems to effect the touch sensitive areas. SHMConfig is enabled.

So for some reason, something is loading correct on half of my load-ups, and the rest of the time, something is not loading correctly. This problem has persisted after numerous reformats/installations. Any ideas on what is going on?

Thanks.

---

### Post by pi/roman on 2010-02-22
BottomEdge only adjusts the position of horizontal scrolling.  In order to disable objects on the bottom of the touchpad you have to set AreaBottomEdge:
>        Option "AreaBottomEdge" "boolean"
              Ignore movements, scrolling and tapping which take place below this edge.  The option is disabled by default and can be enabled by setting the AreaBottomEdge  option  to  any integer value other than zero. Property: "Synaptics Area"

---

### Post by ArkAngel06 on 2010-02-22
Thanks

What do you think would be the correct setting? I saw this option when I was messing around with it, and I tried setting it to 1, but that didn't seem to do anything either.

---

### Post by pi/roman on 2010-02-22
BottomEdge is usually very close to the bottom of the touchpad so AreaBottomEdge should be somewhere near it.  If you wish to use horizontal scrolling then AreaBottomEdge must be a larger number.

---

### Post by ArkAngel06 on 2010-02-22
Thank you so much for your help so far!

I have narrowed it down to this: When the touch pad is working properly, the AreaBottomEdge is set to 4100. When it isn't working properly, it is set to 0. For some reason it changes back and forth randomly after a restart. Are these commands located in a file that I can maybe change to read only? Would that work?

Thanks again.

---

### Post by pi/roman on 2010-02-22
The following command will list the path to your touchpad configuration files:
```
sudo find /usr/share/hal /etc/hal -name *synaptics.fdi
```This would be the only place you are able to permanently change the area of the touchpad in karmic.

---

### Post by ArkAngel06 on 2010-02-22
OK, so it's already read only. It's correct in that file whether it is working or its not working.

Another problem has arisen now. While that command "AreaBottomEdge" disables the buttons' sensitivity, it doesn't fix the other problem, which is actually the main problem. If you hold a click and touch the pad with another finger, the cursor freaks out. I compared the synclient settings in terminal when it's working to when it's not working, and everything is exactly the same, except the AreaBottomEdge line.

So back to my original theory...I think something isn't loading everytime like it's supposed to. :-?

---

### Post by pi/roman on 2010-02-23
Please post your synclient settings, hal configuration, and xinput settings so maybe we will see if something isn't loading.
```
synclient -l  #which may return an error
sudo find /usr/share/hal /etc/hal -name *synaptics.fdi -print0 |  xargs -0 -t cat
xinput list --short | grep -i 'touchpad' | grep -o '"[^"]*"' | xargs xinput list-props
```

---

### Post by ArkAngel06 on 2010-02-23
Here it is when its working:

```
*@*-Netbook:~$ synclient -l
Parameter settings:
    LeftEdge                = 1752
    RightEdge               = 5192
    TopEdge                 = 1620
    BottomEdge              = 4236
    FingerLow               = 24
    FingerHigh              = 29
    FingerPress             = 255
    MaxTapTime              = 180
    MaxTapMove              = 221
    MaxDoubleTapTime        = 180
    SingleTapTimeout        = 180
    ClickTime               = 100
    FastTaps                = 0
    EmulateMidButtonTime    = 75
    EmulateTwoFingerMinZ    = 280
    EmulateTwoFingerMinW    = 7
    VertScrollDelta         = 100
    HorizScrollDelta        = 100
    VertEdgeScroll          = 1
    HorizEdgeScroll         = 0
    CornerCoasting          = 0
    VertTwoFingerScroll     = 0
    HorizTwoFingerScroll    = 0
    MinSpeed                = 0.4
    MaxSpeed                = 0.7
    AccelFactor             = 0.00995223
    TrackstickSpeed         = 40
    EdgeMotionMinZ          = 29
    EdgeMotionMaxZ          = 159
    EdgeMotionMinSpeed      = 1
    EdgeMotionMaxSpeed      = 401
    EdgeMotionUseAlways     = 0
    UpDownScrolling         = 1
    LeftRightScrolling      = 1
    UpDownScrollRepeat      = 1
    LeftRightScrollRepeat   = 1
    ScrollButtonRepeat      = 100
    TouchpadOff             = 1
    GuestMouseOff           = 0
    LockedDrags             = 0
    LockedDragTimeout       = 5000
    RTCornerButton          = 0
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
    PalmMinWidth            = 10
    PalmMinZ                = 199
    CoastingSpeed           = 0
    PressureMotionMinZ      = 29
    PressureMotionMaxZ      = 159
    PressureMotionMinFactor = 1
    PressureMotionMaxFactor = 1
    GrabEventDevice         = 1
    AreaLeftEdge            = 0
    AreaRightEdge           = 0
    AreaTopEdge             = 0
    AreaBottomEdge          = 4100
    JumpyCursorThreshold    = 90

*********************************************************************************************
*********************************************************************************************
*********************************************************************************************
**********************************************************************************************

*@*-Netbook:~$ sudo find /usr/share/hal /etc/hal -name *synaptics.fdi -print0 |  xargs -0 -t cat
[sudo] password for ***: 
cat /usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi 
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.capabilities" contains="input.touchpad">
        <merge key="input.x11_driver" type="string">synaptics</merge>
        <!-- Arbitrary options can be passed to the driver using
             the input.x11_options property since xorg-server-1.5. -->
        <!-- EXAMPLES:
        Switch on shared memory, enables the driver to be configured at runtime
    <merge key="input.x11_options.SHMConfig" type="string">true</merge>

    Maximum movement of the finger for detecting a tap
    <merge key="input.x11_options.MaxTapMove" type="string">2000</merge>

    Enable vertical scrolling when dragging along the right edge
    <merge key="input.x11_options.VertEdgeScroll" type="string">true</merge>

    Enable vertical scrolling when dragging with two fingers anywhere on the touchpad
    <merge key="input.x11_options.VertTwoFingerScroll" type="string">true</merge>

    Enable horizontal scrolling when dragging with two fingers anywhere on the touchpad
    <merge key="input.x11_options.HorizTwoFingerScroll" type="string">true</merge>

    If on, circular scrolling is used
    <merge key="input.x11_options.CircularScrolling" type="string">true</merge>

    For other possible options, check CONFIGURATION DETAILS in synaptics man page
        -->
        <match key="/org/freedesktop/Hal/devices/computer:system.hardware.product" string="Inspiron 1011">
            <merge key="input.x11_options.JumpyCursorThreshold" type="string">90</merge>
            <merge key="input.x11_options.AreaBottomEdge" type="string">4100</merge>
        </match>
        <match key="/org/freedesktop/Hal/devices/computer:system.hardware.product" string="Inspiron 1012">
            <merge key="input.x11_options.JumpyCursorThreshold" type="string">90</merge>
            <merge key="input.x11_options.AreaBottomEdge" type="string">4100</merge>
        </match>
        <match key="/org/freedesktop/Hal/devices/computer:system.hardware.product" string="HP MiniNote 1000">
            <merge key="input.x11_options.JumpyCursorThreshold" type="string">200</merge>
        </match>
    </match>
  </device>
</deviceinfo>

*********************************************************************************************
*********************************************************************************************
*********************************************************************************************
*********************************************************************************************

*@*-Netbook:~$ xinput list --short | grep -i 'touchpad' | grep -o '"[^"]*"' | xargs xinput list-props
Device 'SynPS/2 Synaptics TouchPad':
    Device Enabled (97):    1
    Synaptics Edges (242):    1752, 5192, 1620, 4236
    Synaptics Finger (243):    24, 29, 255
    Synaptics Tap Time (244):    180
    Synaptics Tap Move (245):    221
    Synaptics Tap Durations (246):    180, 180, 100
    Synaptics Tap FastTap (247):    0
    Synaptics Middle Button Timeout (248):    75
    Synaptics Two-Finger Pressure (249):    280
    Synaptics Two-Finger Width (250):    7
    Synaptics Scrolling Distance (251):    100, 100
    Synaptics Edge Scrolling (252):    1, 0, 0
    Synaptics Two-Finger Scrolling (253):    0, 0
    Synaptics Move Speed (254):    0.400000, 0.700000, 0.009952, 40.000000
    Synaptics Edge Motion Pressure (255):    29, 159
    Synaptics Edge Motion Speed (256):    1, 401
    Synaptics Edge Motion Always (257):    0
    Synaptics Button Scrolling (258):    1, 1
    Synaptics Button Scrolling Repeat (259):    1, 1
    Synaptics Button Scrolling Time (260):    100
    Synaptics Off (261):    0
    Synaptics Guestmouse Off (262):    0
    Synaptics Locked Drags (263):    0
    Synaptics Locked Drags Timeout (264):    5000
    Synaptics Tap Action (265):    0, 3, 0, 0, 1, 3, 2
    Synaptics Click Action (266):    1, 1, 1
    Synaptics Circular Scrolling (267):    0
    Synaptics Circular Scrolling Distance (268):    0.100000
    Synaptics Circular Scrolling Trigger (269):    0
    Synaptics Circular Pad (270):    0
    Synaptics Palm Detection (271):    0
    Synaptics Palm Dimensions (272):    10, 199
    Synaptics Coasting Speed (273):    0.000000
    Synaptics Pressure Motion (274):    29, 159
    Synaptics Pressure Motion Factor (275):    1.000000, 1.000000
    Synaptics Grab Event Device (276):    1
    Synaptics Area (277):    0, 0, 0, 4100
    Synaptics Capabilities (278):    1, 1, 1, 0, 0
    Synaptics Jumpy Cursor Threshold (279):    90

```And here the same during a session when its not working:

```
*@*-Netbook:~$ synclient -l
Parameter settings:
    LeftEdge                = 1752
    RightEdge               = 5192
    TopEdge                 = 1620
    BottomEdge              = 4236
    FingerLow               = 24
    FingerHigh              = 29
    FingerPress             = 255
    MaxTapTime              = 180
    MaxTapMove              = 221
    MaxDoubleTapTime        = 180
    SingleTapTimeout        = 180
    ClickTime               = 100
    FastTaps                = 0
    EmulateMidButtonTime    = 75
    EmulateTwoFingerMinZ    = 280
    EmulateTwoFingerMinW    = 7
    VertScrollDelta         = 100
    HorizScrollDelta        = 100
    VertEdgeScroll          = 1
    HorizEdgeScroll         = 0
    CornerCoasting          = 0
    VertTwoFingerScroll     = 0
    HorizTwoFingerScroll    = 0
    MinSpeed                = 0.4
    MaxSpeed                = 0.7
    AccelFactor             = 0.00995223
    TrackstickSpeed         = 40
    EdgeMotionMinZ          = 29
    EdgeMotionMaxZ          = 159
    EdgeMotionMinSpeed      = 1
    EdgeMotionMaxSpeed      = 401
    EdgeMotionUseAlways     = 0
    UpDownScrolling         = 1
    LeftRightScrolling      = 1
    UpDownScrollRepeat      = 1
    LeftRightScrollRepeat   = 1
    ScrollButtonRepeat      = 100
    TouchpadOff             = 1
    GuestMouseOff           = 0
    LockedDrags             = 0
    LockedDragTimeout       = 5000
    RTCornerButton          = 0
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
    PalmMinWidth            = 10
    PalmMinZ                = 199
    CoastingSpeed           = 0
    PressureMotionMinZ      = 29
    PressureMotionMaxZ      = 159
    PressureMotionMinFactor = 1
    PressureMotionMaxFactor = 1
    GrabEventDevice         = 1
    AreaLeftEdge            = 0
    AreaRightEdge           = 0
    AreaTopEdge             = 0
    AreaBottomEdge          = 0
    JumpyCursorThreshold    = 0

***********************************************************************************
***********************************************************************************
***********************************************************************************
***********************************************************************************

@ark-Netbook:~$ sudo find /usr/share/hal /etc/hal -name *synaptics.fdi -print0 |  xargs -0 -t cat
[sudo] password for ***: 
cat /usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi 
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.capabilities" contains="input.touchpad">
        <merge key="input.x11_driver" type="string">synaptics</merge>
        <!-- Arbitrary options can be passed to the driver using
             the input.x11_options property since xorg-server-1.5. -->
        <!-- EXAMPLES:
        Switch on shared memory, enables the driver to be configured at runtime
    <merge key="input.x11_options.SHMConfig" type="string">true</merge>

    Maximum movement of the finger for detecting a tap
    <merge key="input.x11_options.MaxTapMove" type="string">2000</merge>

    Enable vertical scrolling when dragging along the right edge
    <merge key="input.x11_options.VertEdgeScroll" type="string">true</merge>

    Enable vertical scrolling when dragging with two fingers anywhere on the touchpad
    <merge key="input.x11_options.VertTwoFingerScroll" type="string">true</merge>

    Enable horizontal scrolling when dragging with two fingers anywhere on the touchpad
    <merge key="input.x11_options.HorizTwoFingerScroll" type="string">true</merge>

    If on, circular scrolling is used
    <merge key="input.x11_options.CircularScrolling" type="string">true</merge>

    For other possible options, check CONFIGURATION DETAILS in synaptics man page
        -->
        <match key="/org/freedesktop/Hal/devices/computer:system.hardware.product" string="Inspiron 1011">
            <merge key="input.x11_options.JumpyCursorThreshold" type="string">90</merge>
            <merge key="input.x11_options.AreaBottomEdge" type="string">4100</merge>
        </match>
        <match key="/org/freedesktop/Hal/devices/computer:system.hardware.product" string="Inspiron 1012">
            <merge key="input.x11_options.JumpyCursorThreshold" type="string">90</merge>
            <merge key="input.x11_options.AreaBottomEdge" type="string">4100</merge>
        </match>
        <match key="/org/freedesktop/Hal/devices/computer:system.hardware.product" string="HP MiniNote 1000">
            <merge key="input.x11_options.JumpyCursorThreshold" type="string">200</merge>
        </match>
    </match>
  </device>
</deviceinfo>

***********************************************************************************
***********************************************************************************
***********************************************************************************
***********************************************************************************

*@*-Netbook:~$ xinput list --short | grep -i 'touchpad' | grep -o '"[^"]*"' | xargs xinput list-props
Device 'SynPS/2 Synaptics TouchPad':
    Device Enabled (97):    1
    Synaptics Edges (242):    1752, 5192, 1620, 4236
    Synaptics Finger (243):    24, 29, 255
    Synaptics Tap Time (244):    180
    Synaptics Tap Move (245):    221
    Synaptics Tap Durations (246):    180, 180, 100
    Synaptics Tap FastTap (247):    0
    Synaptics Middle Button Timeout (248):    75
    Synaptics Two-Finger Pressure (249):    280
    Synaptics Two-Finger Width (250):    7
    Synaptics Scrolling Distance (251):    100, 100
    Synaptics Edge Scrolling (252):    1, 0, 0
    Synaptics Two-Finger Scrolling (253):    0, 0
    Synaptics Move Speed (254):    0.400000, 0.700000, 0.009952, 40.000000
    Synaptics Edge Motion Pressure (255):    29, 159
    Synaptics Edge Motion Speed (256):    1, 401
    Synaptics Edge Motion Always (257):    0
    Synaptics Button Scrolling (258):    1, 1
    Synaptics Button Scrolling Repeat (259):    1, 1
    Synaptics Button Scrolling Time (260):    100
    Synaptics Off (261):    0
    Synaptics Guestmouse Off (262):    0
    Synaptics Locked Drags (263):    0
    Synaptics Locked Drags Timeout (264):    5000
    Synaptics Tap Action (265):    0, 3, 0, 0, 1, 3, 2
    Synaptics Click Action (266):    1, 1, 1
    Synaptics Circular Scrolling (267):    0
    Synaptics Circular Scrolling Distance (268):    0.100000
    Synaptics Circular Scrolling Trigger (269):    0
    Synaptics Circular Pad (270):    0
    Synaptics Palm Detection (271):    0
    Synaptics Palm Dimensions (272):    10, 199
    Synaptics Coasting Speed (273):    0.000000
    Synaptics Pressure Motion (274):    29, 159
    Synaptics Pressure Motion Factor (275):    1.000000, 1.000000
    Synaptics Grab Event Device (276):    1
    Synaptics Area (277):    0, 0, 0, 0
    Synaptics Capabilities (278):    1, 1, 1, 0, 0
    Synaptics Jumpy Cursor Threshold (279):    0

```

---

### Post by pi/roman on 2010-02-23
Here is the difference I see when it is working and not
> #working
AreaBottomEdge          = 4100
 JumpyCursorThreshold    = 90
#not working
    AreaBottomEdge          = 0
    JumpyCursorThreshold    = 0So in order to make those settings always on they can be added to your hal configuration and also make shmconfig enabled:
```
gksudo gedit /usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi
```Copy the red lines into your fdi file:
```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.capabilities" contains="input.touchpad">
        <merge key="input.x11_driver" type="string">synaptics</merge>
[COLOR=Red]        <merge key="input.x11_options.SHMConfig" type="string">true</merge>
        <merge key="input.x11_options.AreaBottomEdge" type="string">4100</merge>
        <merge key="input.x11_options.JumpyCursorThreshold" type="string">90</merge>[/COLOR]
        <!-- Arbitrary options can be passed to the driver using
             the input.x11_options property since xorg-server-1.5. -->
        <!-- EXAMPLES:
        Switch on shared memory, enables the driver to be configured at runtime
    <merge key="input.x11_options.SHMConfig" type="string">true</merge>

    Maximum movement of the finger for detecting a tap
    <merge key="input.x11_options.MaxTapMove" type="string">2000</merge>

    Enable vertical scrolling when dragging along the right edge
    <merge key="input.x11_options.VertEdgeScroll" type="string">true</merge>

    Enable vertical scrolling when dragging with two fingers anywhere on the touchpad
    <merge key="input.x11_options.VertTwoFingerScroll" type="string">true</merge>

    Enable horizontal scrolling when dragging with two fingers anywhere on the touchpad
    <merge key="input.x11_options.HorizTwoFingerScroll" type="string">true</merge>

    If on, circular scrolling is used
    <merge key="input.x11_options.CircularScrolling" type="string">true</merge>

    For other possible options, check CONFIGURATION DETAILS in synaptics man page
        -->
        <match key="/org/freedesktop/Hal/devices/computer:system.hardware.product" string="Inspiron 1011">
            <merge key="input.x11_options.JumpyCursorThreshold" type="string">90</merge>
            <merge key="input.x11_options.AreaBottomEdge" type="string">4100</merge>
        </match>
        <match key="/org/freedesktop/Hal/devices/computer:system.hardware.product" string="Inspiron 1012">
            <merge key="input.x11_options.JumpyCursorThreshold" type="string">90</merge>
            <merge key="input.x11_options.AreaBottomEdge" type="string">4100</merge>
        </match>
        <match key="/org/freedesktop/Hal/devices/computer:system.hardware.product" string="HP MiniNote 1000">
            <merge key="input.x11_options.JumpyCursorThreshold" type="string">200</merge>
        </match>
    </match>
  </device>
</deviceinfo>
```

---

