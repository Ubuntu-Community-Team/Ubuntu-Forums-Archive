---
title: "Synaptics Touchpad Xorg.conf All Options"
date: 2006-01-07
forum: Hardware &amp; Laptops
---

### Post by Teddy-O on 2006-01-07
Does anyone know where I can find *[COLOR="Red"]all[/COLOR]* the Xorg.conf options for the Synaptics Touchpad? 

I find examples of various subsets of these options but not an official listing of all of them and what they actually do.

Thanks.

--Teddy-O

---

### Post by [Rui] on 2006-01-07
GUI: System menu -> help, Manual pages, Configuration files, synaptics
CLI: man synaptics

---

### Post by Michael Steinberg on 2006-01-07
I don't have that on my Breezy system.

---

### Post by mpvano on 2006-01-07
On some machines, the full driver doesn't load and you are stuck with whatever emulation is built in to the machine (i.e. my older Sony VAIO), but if you really have a working synaptics driver, then try adding the following line to the xorg.conf file:
       Option "SHMConfig"   "true"

if you do this and reboot, the "synclient" command should work and will dump all the settings and their current values and let you change them from the command line to experiment with them. Once you have values you like, you can then add them to xorg.conf to make them defaults....

FYI: Here are my current T30 settings, but they're a work in progress. Also note that there are at least two different kinds of touchpads that the driver works with and they take completely different parameters. 

Parameter settings:
    LeftEdge             = 1900
    RightEdge            = 5400
    TopEdge              = 1900
    BottomEdge           = 4000
    FingerLow            = 35
    FingerHigh           = 50
    MaxTapTime           = 180
    MaxTapMove           = 220
    MaxDoubleTapTime     = 180
    ClickTime            = 50
    EmulateMidButtonTime = 75
    VertScrollDelta      = 70
    HorizScrollDelta     = 0
    MinSpeed             = 0.03
    MaxSpeed             = 0.15
    AccelFactor          = 0.03
    EdgeMotionMinZ       = 30
    EdgeMotionMaxZ       = 160
    EdgeMotionMinSpeed   = 0
    EdgeMotionMaxSpeed   = 0
    EdgeMotionUseAlways  = 0
    UpDownScrolling      = 1
    TouchpadOff          = 0
    GuestMouseOff        = 0
    LockedDrags          = 0
    RTCornerButton       = 0
    RBCornerButton       = 0
    LTCornerButton       = 0
    LBCornerButton       = 0
    TapButton1           = 1
    TapButton2           = 2
    TapButton3           = 3
    CircularScrolling    = 0
    CircScrollDelta      = 0
    CircScrollTrigger    = 0
    CircularPad          = 0

I think this is an ALPS touchpad.(CORRECTION - it's a SYNAPTICS)

hope this helps,

Mario

PS: The full documentation for the driver and these parameters  is in /usr/share/doc/xorg-driver-synaptics/README.gz on my machine....
mv

---

