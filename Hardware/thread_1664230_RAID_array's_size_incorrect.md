---
title: "RAID array's size incorrect"
date: 2011-01-10
forum: Hardware
---

### Post by 5ER on 2011-01-10
I set up a RAID0 array consisting of two 1.5 TB hard drives. The size reported in the SATA chip's user interface is 3000470MB.
But when I go to Linux and open up a partitioning tool, I see two separate drives.
If I run "dmraid -a y" and check any partitioning tool, I see the RAID array instead of the two separate drives, but its capacity is 745 GiB.
I'm trying to make a GUID partition table and a 3TB partition on it, but this issue is preventing me from doing so.

My motherboard (Asus M3A32-MVP Deluxe) has two SATA controllers: AMD SB600 and Marvell 6121. Same problem on both.

I have tried two distributions: Mandriva 2010.2 and Fedora 14. No difference.

If this info is of any use:
-Windows XP does not see the array
-All partitioning tools in Windows XP have problems with the array's size, but they all report the size around 2TiB, which is probably the fault of MBR's limit.
-Windows 7 installer detects the size correctly, but can't create a partition big enough due to the MBR limit.
-If the array is set to be smaller than 2TiB and not surpass the MBR's limit, "dmraid -a y" detects the RAID, but fails to map it and reports "No RAID drives" or something like that. (NOTE: This may not be entirely true, as I have not experimented with it enough. This happened when the array was set to smaller sizes, but the assumption that it's the MBR limit again is mine and not proven)

---

### Post by 5ER on 2011-01-14
*ignore* triple-post due to connection error, I am sorry.

---

### Post by 5ER on 2011-01-14
*ignore* triple-post due to connection error, I am sorry.

---

### Post by 5ER on 2011-01-14
I have tried a Fedora 14 live cd and the situation is the same.

UPDATE: gparted shows a warning for the drive, saying "*Invalid argument during seek for read on /dev/dm-0*".

---

