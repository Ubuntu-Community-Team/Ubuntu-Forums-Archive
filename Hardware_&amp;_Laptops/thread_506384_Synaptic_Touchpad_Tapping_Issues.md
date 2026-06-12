---
title: "Synaptic Touchpad: Tapping Issues"
date: 2007-07-21
forum: Hardware &amp; Laptops
---

### Post by ObeyMyDog on 2007-07-21
Hello all,

I initially set out to fix the slow cursor motion of my touchpad, ended up editing xorg.conf with the help of this thread [http://ubuntuforums.org/showthread.php?t=428839](http://ubuntuforums.org/showthread.php?t=428839)

Cursor speedup worked great but my tapping functionality was gone when I applied the changes!  Looking near the end of the aforementioned thread, I saw that someone had needed to add values for tap speeds

Option "MaxTapTime" "300"
Option "MaxDoubleTapTime" "300"

I've tried playing around with smaller numbers here to restore my brisk tapping recognition, but to no avail.  The best I can get is about 3x the length of the originally recognized taps.  I'm co-managing these settings in gsynaptics and have messed with the tapping settings there following each change to xorg.conf.  Here's the relevant part of that file as it stands now:

Edit: apparently I hadn't tried restarting the XWindow server after applying the initial ("300") setting; that works fine after the restart.  D'oh.

---

### Post by EXCiD3 on 2007-07-22
What about the Synaptic Touchpad Tool in the repositories? I installed it, but never played around with it much, as i mainly use my regular mouse...I remember there was tapping options though.

---

