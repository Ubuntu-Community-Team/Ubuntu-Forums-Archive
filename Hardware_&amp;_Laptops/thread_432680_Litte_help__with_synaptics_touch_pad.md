---
title: "Litte help  with synaptics touch pad"
date: 2007-05-04
forum: Hardware &amp; Laptops
---

### Post by ShaneR on 2007-05-04
Hey, guys.  Little help...

Tapping is not working as well as it should.

Often, it will take 2-3 taps (sometimes more), for the touchpad to respond.  Very annoying.

I tried settings in gsynaptics and editing the xorg.conf file based on some suggestions I found in other threads, nothing seems to be improving performance.

Any ideas?

Here's how my settings in xorg.conf appear now:

Section "InputDevice"
Identifier "Synaptics Touchpad"
Driver "synaptics"
Option "SendCoreEvents" "true"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
Option "SHMConfig" "true"
Option "MaxTapTime" "50"
Option "MaxDoubleTapTime" "50"
Option "VertEdgeScroll" "1"
Option "HorizEdgeScroll" "1"

Running a Dell Inspiron 6400 (Core Duo 1.6 ghz, 1GB ram, X1400)

Thanks!

EDIT: Should say that I'm running 7.04 and still pretty new to linux.

---

### Post by altrez on 2007-06-04
Hi, I had the same problem you described, and also on a Dell Inspiron 6400. I decided a while back to use the buttons just below the touchpad for left clicking, since the touchpad click was totally unreliable. However I always wanted to get the touchpad back to the same level of response I had with WinXP.

The following link proved extremely useful in improving both click speed, and click recognition for my touchpad:

[http://ubuntuforums.org/showthread.php?t=365683&highlight=dell+inspiron+6400+touch](http://ubuntuforums.org/showthread.php?t=365683&highlight=dell+inspiron+6400+touch)

Of the solutions the post mentioned, I chose to edit my xorg.conf file with the following : (additions in bold)

Section "InputDevice"
    [INDENT]Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizScrollDelta" "0"
[B]Option         "SingleTaptimeout" "0"
    Option         "FingerLow" "35"
    Option         "FingerHigh" "35"
    Option         "ClickTime" "0"
    Option         "FastTaps" "1"[/B][/INDENT]
EndSection

If you do choose this, you may want to play around with FingerLow and FingerHigh to find a setting the works for you.

---

### Post by Jasman on 2007-06-20
I've been looking for a thread like this, but just found it after a lot of playing around. I'm finding the most difficult thing to achieve with the xorg.conf touchpad settings is a wide range of tapping sensitivity. I don't think there are really enough settings to get the same responsiveness you can get in Windows. Right now, I've just set FingerHigh at 20 and FingerLow at 5, and it's not too bad, but still, the range of pressures that register as a tap seem to be pretty limited. The synaptics documentation says those two parameters should be between 10 and 20 integers apart. Can anyone explain the precise effects of choosing the two numbers and the interval between them? I'm still a little confused about these settings, and I've been playing with them for several days now. Also, do any of the GUI clients actually permanently override the xorg.conf settings? I've uninstalled gsynaptics and ksynaptics. Maybe I should also remove qsynaptics. Thanks.

---

