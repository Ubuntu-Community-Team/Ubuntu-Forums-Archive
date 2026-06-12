---
title: "Setting up Dell E153FPT Touchscreen monitor on Hardy Heron 8.04"
date: 2008-08-02
forum: Hardware
---

### Post by rmflagg on 2008-08-02
Hi everyone,

   I have a Dell E153FPT 15" touchscreen monitor with a USB interface.  I would like to get it working with Hardy Heron 8.04.  The monitor identifies itself as a Microtouch monitor and when I tried to install the monitors under Windows, it's get identified as a Microtouch EX II, which is the touchscreen controller model.

   I have already installed the xorg-microtouch package.  It seems to work, but the calibration is way off and the axis go in opposite directions.  I don't know how to set up the xorg.conf file and I don't know how to identify what device name it falls under. ](*,)

   Has anyone had any luck with the configuration AND calibration of this monitor under Hardy?  If so, could you please share the wealth with others?!? :)  

Thanks,
RMFlagg

---

### Post by cybagorilla on 2008-08-08
try something like this in your xorg.conf
```
Section "InputDevice"
        Identifier      "touchscreen"
        Driver          "evtouch"
        Option          "device"        "/dev/input/event3"
#you can try to define a udev rule to use a permanent symlink ...
        Option          "MinX"          "0"
        Option          "MinY"          "0"
        Option          "MaxX"          "4000"
        Option          "MaxY"          "4000"
        Option          "MoveLimit"     "1"
        Option          "sendCoreEvents"        "On"
        Option          "SwapY" "On"
EndSection
```

i spent hours finding the correct values of MinX MaxX MinY MaxY, trying values and restarting xorg until the calibration is okay becaus i found no working calibration tool.

I found the SwapY option in ... "man xorg.conf" (always start by this one), i remember that there is also a "man evtouch"

The MoveLimit is critical on ubuntu Hardy, it seems that you HAVE TO set it.

I hope it helps ...

---

### Post by rmflagg on 2008-08-09
I hope this works, or at least starts me down the right path.  I won't be able to to get to this in the next few days, but I will report back!

Thanks!


> **cybagorilla said:**
> try something like this in your xorg.conf
```
Section "InputDevice"
        Identifier      "touchscreen"
        Driver          "evtouch"
        Option          "device"        "/dev/input/event3"
#you can try to define a udev rule to use a permanent symlink ...
        Option          "MinX"          "0"
        Option          "MinY"          "0"
        Option          "MaxX"          "4000"
        Option          "MaxY"          "4000"
        Option          "MoveLimit"     "1"
        Option          "sendCoreEvents"        "On"
        Option          "SwapY" "On"
EndSection
```

i spent hours finding the correct values of MinX MaxX MinY MaxY, trying values and restarting xorg until the calibration is okay becaus i found no working calibration tool.

I found the SwapY option in ... "man xorg.conf" (always start by this one), i remember that there is also a "man evtouch"

The MoveLimit is critical on ubuntu Hardy, it seems that you HAVE TO set it.

I hope it helps ...

---

### Post by fromhereon on 2008-09-01
I've been trying to set up this same model on hardy heron for a while now and can't seem to get it to work. Have you had any luck with this. I've been setting it to /dev/input/mouse2 but it doesn't seem to do anything no matter what i change the values to in xorg.conf

---

### Post by rmflagg on 2008-09-04
> **fromhereon said:**
> I've been trying to set up this same model on hardy heron for a while now and can't seem to get it to work. Have you had any luck with this. I've been setting it to /dev/input/mouse2 but it doesn't seem to do anything no matter what i change the values to in xorg.conf

I still haven't gotten anything to work.  When you plug the monitor in, it is receiving input, it just isn't calibrated and the X axis is reversed.

I find it really hard to believe that there isn't someone out there who could give us some good information on this subject.  I am even having a hard time finding ANY information about Ubuntu with ANY touchscreen monitors(this doesn't include the tablet PC/embedded market).

SOMEONE PLEASE!?!

RMF

---

### Post by v.peregoncev on 2008-11-05
Guys,
Hey it looks like no one of you could get that to work :(
Let me know if any of you had a luck. I am thinking about buying this unit to test on the Ubuntu 8.10 with Compiz
Vladimir

---

