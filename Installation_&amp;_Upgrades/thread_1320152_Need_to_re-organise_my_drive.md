---
title: "Need to re-organise my drive"
date: 2009-11-09
forum: Installation &amp; Upgrades
---

### Post by josephe on 2009-11-09
Hi all,
 
I hope this is not too fuzzy, but I really think I need to start fresh again. In a nutshell I have Ubuntu 9.10, and Windows 7 partitions with a shared Data1 drive. I shrunck the Windows 7 partition to put Ubuntu Studio as an alternate booting os. Problem is that all the PM tools I try both Windows and Linux basically tell me I have too many Primary partitions.
 
What to do,what to do???
 
I think my cleanest option is to take images of both OS partitions and then wipe the whole 320 gb drive then repartition the drive into 3 Bootable partitions and 1 data partition (maybe 2 a small NTFS will prob be necessary)
 
I'd really appreciate any advice on the best opensource tool to use for this and suggestions on size of partitions
 
Regards
 
Joseph

---

### Post by efflandt on 2009-11-09
If you want more than 4 partitions, you have to make at least 1 an extended partition, and then you can put multiple logical partitions into that.  The first 4 partitions are 1-4, but even if you have less than that, the first logical partition is 5.  So for example you might have sda1, sda2, sda3, sda4 <sda5, sda6> where sda4 is an extended partition and sda5 and sda6 or more are within that.

Actually I think Windows only likes one primary partition it recognizes and then logical partitions for any others on the same drive.  So if you are going to share another Windows partition, it may be a good idea to make that one a logical partition (within an extended partition).

---

### Post by josephe on 2009-11-10
Hi Efflandt
 
Thanks very much for the feedback, so just to confirm my understanding, if I have one primary for Windows 7 and 2 logical of which one will be split into 2 primary (bootables for Linux) and 1 for data (split into 1 NTFS and 1 EXT) that should work ?

---

