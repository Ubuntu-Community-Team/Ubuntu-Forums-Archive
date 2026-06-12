---
title: "Can't boot from CD"
date: 2009-07-21
forum: Installation &amp; Upgrades
---

### Post by ktat on 2009-07-21
Recently I have been playing around with installing a variety of OSs on my pc.  I have 2 HDDs, the first is 250Gb sata, on it I run Jaunty and have all my other personal files.  The 2nd is an 80Gb IDE drive which has Fedora and Karmic and others.  This was working fine until I decided I need to be able to use EXPee.

After some hiccups in installing EXpee it seemed to be working ok.  Then my problem.  I started having issues with getting access to other OSs, so I tried booting SGB from a cd to sort out GRUB - I wasn't having much success and then, for no apparent reason, I could no longer boot ***anything*** from my cd drive.

I achieve a workaround by swapping the 80Gb HDD for another and found I can still access the 250Gb HDD as well as boot cds.  But when I put the 80Gb HDD back in it doesn't matter what boot order I have things in the BIOS - all I get is:

Grub loading, please wait...
then nothing (sometimes gives error 5)

---

### Post by Mighty_Joe on 2009-07-21
> **ktat said:**
> I achieve a workaround by swapping the 80Gb HDD for another and found I can still access the 250Gb HDD as well as boot cds.  But when I put the 80Gb HDD back in it doesn't matter what boot order I have things in the BIOS

Sure sounds like a bad hard drive.

---

### Post by Theory5 on 2009-07-21
Sounds more like a device conflict to me. Im not too familiar with grub and I have no idea what EXPee is. I have never heard of a HDD failing and blocking access to others but I bet it could happen. is EXPee on the 80gb? look around online, it might be causing some sort of conflict. What device is master and slave?

---

### Post by philcamlin on 2009-07-21
> **Theory5 said:**
> Sounds more like a device conflict to me. Im not too familiar with grub and I have no idea what EXPee is. I have never heard of a HDD failing and blocking access to others but I bet it could happen. is EXPee on the 80gb? look around online, it might be causing some sort of conflict. What device is master and slave?

windows xp :P

it looks liek a bad hdd though

---

### Post by ktat on 2009-07-22
> **Mighty_Joe said:**
> Sure sounds like a bad hard drive. Ok, so is there an easy way to determine whether or not my 80Gb HDD has died.

I will try it in isolation on another pc, by the way - yes, Expee is on the 80Gb HDD.

---

### Post by ktat on 2009-07-27
Thanks for your help - seems the HDD is ok - works fine in another pc.  It's the CD player that's dead.

---

