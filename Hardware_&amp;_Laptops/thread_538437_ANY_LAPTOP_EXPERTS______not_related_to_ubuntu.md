---
title: "ANY LAPTOP EXPERTS?      not related to ubuntu"
date: 2007-08-30
forum: Hardware &amp; Laptops
---

### Post by pgar23 on 2007-08-30
Sorry to post a thread that is not ubuntu related, but I alwayz get the best support from this community than ANY OTHER FORUM.

I have a Toshiba Satellite M45. Recently it has been malfunctioning.
List of known malfunctions:

1. When restarting the laptop, I get a resized toshiba screen and it is stuck on this screen...it never boots past this (only on restart).

Solution: (for now) I have to unplug the AC adapter for about 1 minute, then reconnect it and the laptop will boot fine.

2. The laptop intermittently reboots, but when it does I get problem 1.

3. Also sometimes when I boot, hasn't happened recently, but every so often a screen occurs befor boot and displays an error like: 
Preboot somethingx environment
PXE-60     Media test failure
PXE-MOF  check cable
exiting PXE
press any key... (and when I press a key it restarts this screen again and I receive same error)

I dismanttled the laptop completely, just to make sure there wasn't any unplugged plugs, nothing was out of the ordinary there.

Does anyone know what is wrong with my laptop? I need expert assistance for this one. Im baffled by this.

Thanks for the help Ubuntu community, you haven't failed me YET. hahaha

---

### Post by tgalati4 on 2007-08-30
Try removing the battery and leave it out overnight.  Clean the contacts on the battery and inside the laptop with an eraser.  Clean off the crumbs.  How old is the battery?

If your battery is not providing enough juice, you can get all kinds of weirdness.  Your power conditioning circuitry inside the laptop could also be going.

If the laptop was ever dropped, then there could be damage to the motherboard that is showing up as odd behavior.

Try reseating the RAM--clean the gold contacts with an eraser.  Be sure to ground yourself by holding some metal--like a metal computer case that is plugged into a grounded outlet.

Run memtest86+ (it's on the Live CD).  Let it run for 10 complete PASS cycles.

---

### Post by pgar23 on 2007-08-30
the battery isnt old, this problem occurs even when the battery is not in. I am running the laptop right now without the battery in it, only the AC adapter, and the stupid thing reboots when I change positions.

---

### Post by pgar23 on 2007-08-31
on top of the existing problems, now the darn thing wont even turn on/boot...
Explanation: When I press power button, receive power, LEDs come on, evrything goes well, then right b4 it gets even to Toshiba screen, CRASH!

But, I found out that when I unplug video cable, the lappy boots fine...What the heck???

What is going on...


I NEED HELP PLEASE!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by PmDematagoda on 2007-08-31
> But, I found out that when I unplug video cable, the lappy boots fine...What the heck???

What do you mean by this? What cable is it?

---

### Post by pgar23 on 2007-08-31
> **PmDematagoda said:**
> What do you mean by this? What cable is it?

Sorry for being so vague...I meant the video cable that connects the LCD screen to the laptop itself...I think that is video cable correct?

When I disconnect this cable, the laptop boots normally(found this out by external monitor and also, if I plug the "video cable in SLIGHTLY but not all the way, I get image on screen, but when plug in all the way, CRASH!)

---

### Post by pgar23 on 2007-08-31
SIMILAR THREAD OF MINE...[http://ubuntuforums.org/showthread.php?p=3288823#post3288823](http://ubuntuforums.org/showthread.php?p=3288823#post3288823)

---

### Post by tgalati4 on 2007-09-01
I repaired an iBook that was shorting through the hinge.  The video cable that drives the display has a metal braid over it and it runs through the hinge assembly.  After so many flexes, it wore through the insulation, shorting, causing spontaneous shutdowns.  I simply cut open the braid and wrapped the (unbelievably thin) wires with electrical tape, then closed up the braid.

Your computer could have a similar problem, an internal short that won't allow a full boot.

---

### Post by pgar23 on 2007-09-01
Man, I am just going to buy a new video cable off ebay. This is too much and I need my laptop for school.

---

