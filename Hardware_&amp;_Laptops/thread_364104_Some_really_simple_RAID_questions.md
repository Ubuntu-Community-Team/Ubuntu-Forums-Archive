---
title: "Some really simple RAID questions"
date: 2007-02-17
forum: Hardware &amp; Laptops
---

### Post by Redeyes_Gambit on 2007-02-17
}{'lo fellow 'buntu-ers!

Just a couple of quick questions concerning RAID. I have a promise "fake" SATA RAID card with 2 250 GB Seagate drives attached to it. I have already installed Ubuntu Server 6.06 on a 1 GB hard drive (ok, technically it is a compact flash card that looks like a HDD to Ubuntu. Really cool) and this will not be part of the RAID array.

I have already installed dmraid via apt-get and didn't receive any complaints from the install process. I want to take the 2 (fresh, unpartitioned) Seagate 250 GB drives and put them into a RAID 1 (mirroring yes?) configuration. I have read several posts/guides/docs/man pages concerning setting up dmraid but they all go into too much depth and too many options. My head winds up spinning lol.

All I need is a few commands that will set up the array in RAID 1 and have the array mounted at boot up. No data on either of the 250 GB drives needs to be preserved but they may need to be partitioned/formatted (I was not sure if setting up the array needed to come before of after partitioning so I just left the two drives fresh.)

Oh, yes, and I am using Ubuntu server so it will all have to be done using text-based commands :)

---

