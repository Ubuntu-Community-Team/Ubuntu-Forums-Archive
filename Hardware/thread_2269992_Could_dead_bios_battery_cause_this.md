---
title: "Could dead bios battery cause this ?"
date: 2015-03-19
forum: Hardware
---

### Post by michael-piziak on 2015-03-19
Ubuntu 14.04 lts

Frequently, during boot up computer won't make it to desktop.
Sometimes it freezes shortly afterwards and only power off button will escape this - not even alt+print screen reisub will do anything.

I noticed the bios time is not being kept right each time I reset it, but the date is always right.  Time & date in Unity is always correct.

Could a low or dead bios/cmos battery cause such behavior ?

---

### Post by tgalati4 on 2015-03-19
Yes.  If the battery is shorted, then your power supply could be cutting out, right as everything is spinning up.  Is this a laptop or desktop computer?

---

### Post by michael-piziak on 2015-03-19
> **tgalati4 said:**
> Yes.  If the battery is shorted, then your power supply could be cutting out, right as everything is spinning up.  Is this a laptop or desktop computer?

This is my sister's desktop.

She's picking up the cmos battery today and I'm going to give that a try.  If no success, I'm going to do a reinstall.  If those 2 things don't help, I'm guessing it's a power supply, bad mother board, etc...

p.s. I just unplugged the power from the computer for a few minutes.  Ubuntu lost it's time and internet connection upon boot.  Perhaps it is the cmos battery.  I will see later on when she gets back with battery.

---

### Post by tgalati4 on 2015-03-19
If the battery doesn't work (and it's probably 80% chance that it will work), it could be a bad capacitor on the motherboard.  One bad cap can cause the battery to drain, so a new battery may only work for a few days or weeks.

---

### Post by michael-piziak on 2015-03-19
> **tgalati4 said:**
> If the battery doesn't work (and it's probably 80% chance that it will work), it could be a bad capacitor on the motherboard.  One bad cap can cause the battery to drain, so a new battery may only work for a few days or weeks.

My sister tried to find the battery at Walmart and they told her they quit selling Lithium batteries.

So I did a reinstall of 14.04 lts and it seems to have fixed the problem.  I shut it down and restarted it over a dozen times and no problem now.   Something must have got corrupted with the other 14.04

---

### Post by michael-piziak on 2015-03-21
Update.  I thought the problem was fixed and it wasn't  After a clean reinstall and a new battery, the problems persisted.

I think it is a bad monitor (or possibly bad graphics card).  The monitor started giving some crazy looking graphics upon lockup and at other times.  At one lockup the monitor was making grinding sounds inside.

Next step, buy a new monitor I suppose and see if that fixes it.

---

