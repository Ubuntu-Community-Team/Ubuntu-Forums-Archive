---
title: "Synaptic Touchpad Sensitivity"
date: 2006-02-19
forum: Hardware &amp; Laptops
---

### Post by powdercarrot on 2006-02-19
Adjusting the sensitivity on my  synaptic touchpad (HP dv1000 notebook) has no effect in Breezy.  How can I get this thing to move less than five feet when I move my finger 2mm?

---

### Post by ebarrere on 2008-02-04
This is sort of a bump.  Does anyone have a solution for this?  I've tried {g,q,k}synaptics and none of them work!  (the sensitivity scroller has no effect)

Anybody have any ideas?

Thanks in advance!

---

### Post by ebarrere on 2008-02-04
Okay guys, solved my own problem, I'll post the answer for progeny. :)

I should actually yell at myself too because the answer was right there in "man synaptics" but I was moving too fast to see it.  Note to self: RTFM!

Anyway, editing my xorg.conf file and changing the following solved my issue (tweak as necessary):
```

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"        "/dev/psaux"
        Option          "Protocol"      "auto-dev"
        Option          "HorizScrollDelta"      "0"
[B]        Option          "MinSpeed"              "1"
        Option          "MaxSpeed"              "3"
[/B]EndSection
```

---

