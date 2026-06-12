---
title: "Synaptic touchpad scrolling issue"
date: 2007-06-11
forum: Hardware &amp; Laptops
---

### Post by srilyk on 2007-06-11
Every post I've seen about a touchpad has been either for tapping or their scrolling does or doesn't work.

My problem is too much of my touchpad is used for the scrolling, and I can't find any instructions on how to change that.

My touchpad has one of those scroll areas on the right side of the pad, and it works for scrolling just fine - but part of the pad, in equal width (about 1cm / 1/4") scrolls, too.

Does anyone know how to redefine the area that's used for scrolling?

---

### Post by dbarbour on 2008-02-17
Same issue. Any resolution?

---

### Post by mahill on 2008-03-16
I was just about to make a topic asking about this, but thought I should search first.  I'm having the exact same issue.  This still hasn't been fixed as of 7.10.  I'm on a Gateway MX7120 if that matters.  I've tried messing with qsynaptics to see if there were any options, and didn't find any there.

---

### Post by mahill on 2008-04-12
quick bump

---

### Post by WesleyClifford on 2008-06-04
I found a solution to this problem. I'm not sure how specific it is to my setup, but here's my touchpad section in my /etc/X11/xorg.conf file:
```

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizEdgeScroll"       "0"
        Option          "MaxTapTime"            "0"
        Option          "HorizScrollDelta"      "0"
[B]        Option          "VertScrollDelta"       "100"
        Option          "SHMConfig"             "on"
        Option          "RightEdge"             "5980"[/B]
EndSection
```

I bolded the important stuff.

First, I set SHMConfig to "on" and ran ```
synclient -m 100
``` to see the layout of my touchpad. I noticed that the entire scrollwheel area returned a x position of 8176, and the largest number I could get in the mouse area was 5981 (Yes, there was a gap in numbers)

I set RightEdge to 7000 (a number between the two) and the scrollbar did not work at all (but the entire mouse section worked as a mouse).

I then set RightEdge to 5980 (I rounded down for fun) and bam, it worked.  It still picks up the scroll action right on the little rib between the mouse and scroll areas, but that doesn't bug me too much.

VertScrollDelta has to be anything but 0. I believe 100 is the default (so you may not need it) but I'm not going to mess with it any more.

**NOTE: As with any config file, BACK UP YOUR XORG.CONF FILE BEFORE MUCKING WITH IT and be confident that you can restore it from backup if it fails. This means, with xorg.conf, that you may have to do it from the command line with no gui. If you are not sure, get your local friendly linux guru to do this for you :)**

---

### Post by justinrichey on 2008-06-14
Thanks for the info.  Based on this I added the line below to my xorg.conf and it's working perfectly now on my T61p.

Option	"RightEdge"	"5700"

---

