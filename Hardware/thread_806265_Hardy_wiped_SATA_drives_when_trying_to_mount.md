---
title: "Hardy wiped SATA drives when trying to mount"
date: 2008-05-24
forum: Hardware
---

### Post by SmokingMan on 2008-05-24
Hi all! 
Here is the problem I have encountered:

I recently did a fresh install of Ultimate Edition of the Hardy kernel over a previous Gutsy installed partition. After the install, Hardy would not recognize either SATA drive, where Gutsy had no problem reading/writing to those drives. It would not recognize the devices with the mount command either. When I booted to Xp and looked at the SATA drives, both were wiped of all previous data. They are NTFS formatted about 300Gb each.

Hardy along with an XP partition is on the same physical boot drive and the two SATA drives are on a PCI Silicon Image SATA Raid controller. 

When doing the install, I made *sure* only the ext3 Hardy partition was to be formatted. I also tried to give each SATA drive it's mount point like the last install I did.

What did Hardy do to the drives and how can I restore the previous data?

Thanks in advance for any suggestions!

---

