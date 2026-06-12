---
title: "Laptop Suspend(Compaq NW8440)"
date: 2009-05-04
forum: Hardware
---

### Post by peregrine on 2009-05-04
I have a compaq nw8440 and when I try to suspend or hibernate I cannot reload my computer. My gfx card is ATI Firegl v5200 and I'm using the opensource radeon driver. I've tried to add  Option "AccelMode" "EXA" to my device section in xorg.conf with no results. 

I've also tried the other laptop suspend sudo 2ram or 2hd modes but they also don't work.

Any suggestions?

---

### Post by peregrine on 2009-05-04
Bump. Anyone have experience with the FireGL?

Suspend is kind of necessary.

---

### Post by peregrine on 2009-05-07
Bump!!
Why doesn't suspend/hibernate work? It worked in the last version but not now?

Someone please help.

---

### Post by yoasif on 2009-05-07
[https://wiki.ubuntu.com/DebuggingKernelSuspendHibernateResume](https://wiki.ubuntu.com/DebuggingKernelSuspendHibernateResume)

be sure to file a [bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+filebug") and mention that it worked in the last version.

---

### Post by peregrine on 2009-05-07
I figured out how to do do it...Add this to the Device section of xorg.conf

ection "Device"
        Identifier      "Configured Video Device"
        Option          "UseFBDev"              "true"
        Option          "AccelMethod"           "XXA"
[COLOR="Yellow"]        Option          "Composite"             "on"[/COLOR]
        Option          "DynamicClocks"         "on"
EndSection


It makes suspend and hibernate work.

Jason Stiebs

---

### Post by peregrine on 2009-05-07
Scratch that no longer works. What the hell? It just worked now its failing to work.

---

