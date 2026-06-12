---
title: "USB Hard Drive Works in Windows but not in Ubuntu"
date: 2007-06-01
forum: Hardware &amp; Laptops
---

### Post by mr_slayer on 2007-06-01
I have an old 40 gig hard drive that I put into a enclosure recently and when I try to connect it to my Inspiron 6000 laptop with Edgy, the drive is not even seen by the kernel let alone mounted. But when I take it to my desktop with Windows XP Home SP2 it sees the drive perfectly.

I will recall everything that has happened to the drive recently that may be what might cause the problem to speed up the troubleshooting process.

The drive is an old WD 40 gig that I've had for a couple of years. Up until recently, the drive was 2 partitions. But when I was prepping it for being put into the enclosure, I no longer wanted 2 partitions. So I used Partition Magic on my Windows machine to merge the partitions (which were empty, by the way) and create a new FAT32 partition. Since then I have not been able to use it on my laptop under Edgy but it is seen and loaded by Windows.

Could the process of merging the partitions with Partition Magic and then creating the FAT32 partition done something to the drive? But even if the partition table was confusing to Linux, the drive should still show up on the dev listing shouldn't it?

I'm a bit new to Linux and Ubuntu and have loved everything so far. It's not a huge deal if the drive can't be read by Linux because I can just use it solely for my Windows PC then, but this would make things more convenient if I could fix this problem. Thanks!

---

### Post by Jorge on 2007-06-01
I had a problem with the new linux kernel (2.6.20-16) which I upgraded few days ago: I couldn't mount two different USB flash drives. When I rebooted with the old kernel (2.6.20-15), Ubuntu recognized and mounted them right away.

Maybe the same is happening to you.

---

### Post by mijj on 2007-06-01
I had *exactly* the same problem ... but with a new 350GB seagate external usb2 drive.

winXP = no probs whatsoever.

Ubuntu: I tried ext3 partitions, ntfs partitions with ntfs-3g - it didnt make any difference - i could never get it to recognise automatically on boot up.  I *could* force it to be recognised *after* boot up .. but i was suspicious.

... the weird thing was that i had a small older firewire external drive that was recognised with no probs.

I finally sored the prob out by using a ***USB connector at the back of my pc*** rather than the usb connector at the front of the pc.

Why that would make a difference to Ubuntu and not XP, who know. ... But that was what it took to make it work.

And drive's now recognised without fail.
[I][SIZE="1"]
<whew! it was a tough day!>[/SIZE][/I]

---

