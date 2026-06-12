---
title: "Quad monitor setup ?"
date: 2008-09-20
forum: Hardware
---

### Post by ceti331 on 2008-09-20
Anyone got a quad-screen setup going with linux ?
if so please post details on hardware/software setup.

At the minute i've a desktop machine with geforce 8800 and would need to add a second card.

does it make things harder to have different resolutions for examples (when i've seen a laptop drive a second screen that way it was buggy..)

What are the issues with GL (the ability to run GL on one display at least would be good)

How do various window managers take to it (i'm a fan of FluxBox)

Thanks for any info.

---

### Post by ladr0n on 2008-09-20
Yes, it's possible with a couple cards that can handle it.  You'll want to use Xinerama to get it working.  Fortunately, the nvidia configuration utility can set all of that up for you.  
Running GL will be iffy at best (depends on the resolution of the monitors and the specs of the cards).  I have a geforce 8400 in my laptop, and I can't get it to drive two monitors AND run something GL-intensive at the same time.  What I would do in your case is create two xorg.conf files, one for quad-monitors and one for two (one on each card) so that you can run GL apps when necessary by restarting X to use the other config file.  
Most window managers are Xinerama-aware and handle multihead setups exactly the way you would expect them to.  Gnome, for example, will place new windows on the active screen, try to avoid placing things across screens, etc.  I have no reason to think that FluxBox wouldn't be able to do that.

---

