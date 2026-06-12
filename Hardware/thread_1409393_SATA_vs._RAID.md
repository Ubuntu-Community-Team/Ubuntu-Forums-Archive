---
title: "SATA vs. RAID"
date: 2010-02-17
forum: Hardware
---

### Post by Shibblet on 2010-02-17
My motherboard will allow me to set up my Hard Drives as separate SATA Drives or together as a RAID.

Right now they are set up SATA, will I get any performance increase by setting them up as RAID?

---

### Post by pirateghost on 2010-02-17
> **Shibblet said:**
> My motherboard will allow me to set up my Hard Drives as separate SATA Drives or together as a RAID.

Right now they are set up SATA, will I get any performance increase by setting them up as RAID?
motherboard raid is fakeraid, and do not use a TRUE hardware controller, despite what you think.  you will gain NOTHING by it in linux.  if you are using 2 identical harddrives you can set up raid from within Linux and utilize it.

if you dont know what RAID actually is, i suggest you read up on it, because its most likely not worth the hassle unless you know what you are doing and can actually reap the benefits...

---

### Post by Dayofswords on 2010-02-17
unless you know what your doing with RAID, you really should stick with normal setup

RAID on wikipedia
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)

you can get a performance increase in certain raids, or no performance change, or even a lower performance

depends on the raid type, but still, stick with the normal

---

### Post by Objekt on 2010-02-17
The simple answer is, "no, you will not get a performance increase, and you shouldn't even try to use your motherboard RAID controller."  This page ([https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)) explains some reasons why this is true.

Generally, the firmware-based, aka "fake" RAID controllers, included in many motherboards today, are not very useful.  They are not really usable under Linux, and are of questionable benefit under Windows.  I don't know why motherboard manufacturers keep throwing them in.

If you really want the speed increase of RAID 0, or the redundancy of RAID 1, you're better off spending $100-$300 on a true RAID controller card.

---

