---
title: "Installing Dual Boot Software RAID"
date: 2006-01-05
forum: Installation &amp; Upgrades
---

### Post by chrisWhite on 2006-01-05
Well, it's about time I reformat and install a fresh new copy of Windows XP and I'd really like to set it up as a dual-boot with Kubuntu.  The last time I did a reinstall I left a partition clear to put Linux on, but I found out it wouldn't work with the partition because it was on a RAID 0 Array (Abit HPT37x) and Linux wouldn't honor that.  So my question is, if I'm starting from scratch, is it possible to set up both Windows XP and Kubuntu on the same RAID drive?  If so, where do I need to start?

I did search the web and these forums to see if anyone detailed the process, but without knowing more about Linux I was having trouble figuring anything out.

Thanks so much for any suggestions!

Edit: Here's my Specs:
Abit KR7A RAID
AMD Athlon XP 2200+
1.5 GB Ram
NVidia Quadro FX 1100
80 GB (x2) System Drive RAID 0
40 GB Data Drive (could be the Linux Drive if that makes things easier)

---

### Post by chrisWhite on 2006-01-06
After some more searching I found the [FakeRaidHowto]("https://wiki.ubuntu.com/FakeRaidHowto") on the Wiki which appears to be what I need.  One question though, is it better to install Windows first and then add Kubuntu on, or might it be easier to begin with Kubuntu and add Windows?  I'm guessing Windows first is still the way to go as it may not recognize the way Linux set the partitions up?

Oh, one more quick question, is the Wiki howto going to be the exact same process for Kubuntu?  Or do I need to do anything different?

Thanks, hoping to get things cracking this afternoon/evening, really excited to finally get Linux dual-booted.

---

### Post by chrisWhite on 2006-01-06
Well, I figured out how to install dmraid on the Kubuntu live boot, but when I use parted it only sees one partition on it and there should be three.  I'm beginning to thing I should just eat the performance hit and not RAID the drives.  Unless anyone has any suggestions.  

I think I'll download Ubuntu and see if I like it as much as Kubuntu and see if I can get it working that way first.

---

