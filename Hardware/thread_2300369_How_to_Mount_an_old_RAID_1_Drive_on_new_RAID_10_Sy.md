---
title: "How to Mount an old RAID 1 Drive on new RAID 10 System"
date: 2015-10-25
forum: Hardware
---

### Post by SedaliaSteve on 2015-10-25
I'm marking this solved since it sort of worked out. I could never mount it so I borrowed a motherboard and power supply. I got the old RAID 1 up and running and copied it over to a spare. This was a plain old Linux partition so it was a snap to get it mounted. I then copied all the data over and then put it in my new machine, mounted it and got the data. Not exactly an elegant solution but it worked.



(If Hardware isn't the right place to post this, please point me to the right one.)

I've had a software RAID 1 system for a long time and it always worked well until the motherboard died recently. I used that as an excuse to build a new system. It has an SSD for boot and 4 2T drives to make a UEFI RAID 10. That's all working now. The fun came when I tried putting one of the old drives into the new machine so I could copy the data. I can only bring one drive over since the motherboard has 6 SATA slots, 4 for the RAID, one for the SSD and one free.

I've been looking into all the threads here and other Linux boards and nothing works for me. My system sees the 1T drive and it sees the RAID 1 it was part of. First I tried many methods of mounting the individual drive in read only and other modes. They all failed since the partition type is RAID auto detect.

I've tried mounting it as a degraded RAID 1 but this causes problems and fails since I named my new RAID md0, same as the old. There are various ways of renaming an md but they seem like aliasing or risk wiping the new md0. If I stopped the new RAID and started the old one that wouldn't help me since the SSD is small and the old disk has 800 GB of data on it. Has anybody solved this or can point me to a link with a solution?

For the details, the old system ended up at 12.04. The RAID disks were the only ones in there so it booted off them. The main partition is ext3. The drives were 1T Seagate barracudas. The new box is 15.10 on an Asus M5A97 R2.0 with 2T Western Digitals in ext4.

Steve

---

