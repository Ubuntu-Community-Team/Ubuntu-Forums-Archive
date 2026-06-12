---
title: "Ubuntu Karmic Freezes On External Monitor Detection/Change"
date: 2009-11-22
forum: Hardware
---

### Post by inkhorn on 2009-11-22
Hi All,

I have a Toshiba Satellite A200-AH6 laptop running Ubuntu 9.10.  Any time the status of the external display changes (After it detects when I plug it in, or I take it out) while the computer is still on, Ubuntu freezes!  It seems like if I want to take the VGA cable out or put it in, the laptop has to be off!  Here are a few specs:

Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
Monitor: Samsung 20"

Anyone have an idea why Ubuntu freezes when it detects that the monitor is in or out?

Cheers,
Inkhorn

---

### Post by inkhorn on 2009-11-26
I've found that I can help my situation a little bit.  

Before I unplug the VGA cable I go to System > Preferences > Display and turn the external monitor off and the laptop monitor on.  I then unplug the VGA cable and it doesn't freeze (presumably because it is no longer trying to detect the external monitor!).

When I put the VGA cable in and try to detect the external monitor, or if it is trying to use the external monitor and I take the VGA cable out, that's when Ubuntu karmic freezes!

Should I log this as a bug?

Inkhorn

---

### Post by Doughy on 2009-12-11
Having the same problem. So annoying.  I  love Ubuntu, but it absolutely sucks when it comes to using projectors.  I have been bitten by projector problems 3 times, all during presentations and demos in conferences.  It's so frustrating.

---

### Post by inkhorn on 2009-12-14
I found out a bug report for this behaviour.  Check the following link:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/419328](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/419328)

---

