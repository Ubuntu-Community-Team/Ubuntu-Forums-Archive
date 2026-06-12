---
title: "Install CD doesn't detect RAID array"
date: 2009-03-12
forum: Installation &amp; Upgrades
---

### Post by MGT Systems on 2009-03-12
I'm trying to install Kubuntu, on a 3-disk RAID5 array.  I want hardware RAID as the motherboard supports it and I've set the disks up in the BIOS RAID configuration utility, but when the installer scans the disks, it shows up as three separate disks.

There is probably some driver or something missing from the standard install CD I guess.  Is there any way around this?  The motherboard manual has instructions for creating driver disks for windows (on a floppy disk!  I haven't used one of those for a while) but obviously that's no use.

---

### Post by TrickerZ on 2009-03-12
It's not a true hardware RAID.  You will likely need dmraid to do this.  See [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto) for step-by-step instructions.

---

### Post by MGT Systems on 2009-03-12
Ok that makes sense...
A little disappointing perhaps!  It's false advertising on the part of motherboard manufacturers if you ask me.  But at least it explains why RAID cards cost like £500+.

Thanks.

---

