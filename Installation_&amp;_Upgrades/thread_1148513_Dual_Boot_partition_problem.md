---
title: "Dual Boot partition problem"
date: 2009-05-04
forum: Installation &amp; Upgrades
---

### Post by tobiasolesen on 2009-05-04
Hi

I've got an Eee 1000H netbook and I want to do a dual boot with windows xp.

I plan to use around 18gb for my ubuntu installation being:

swap = 3gb
system = 5gb
\home = 10gb

The problem is that I can't make these partitions under the install process number 4. I have a partition that I want to use.. which is a 60gb FAT32 for now. When I go for manual partition I can create a 3gb swap file from the 60gb FAT32 but the 57gb that is left is leaves as unallocated space that will then not be made into \home and system. So I can't make the three partitions that I want... 

I have tried to find a good dual booting guide for the UBR but can't.

So I can't create the necessary partitions for the installation. Anybody who can help?

thanks
tobias

---

### Post by caljohnsmith on 2009-05-04
I would suggest running Ubuntu's gparted partition editor first (System > Admin > Partition Editor), and you can use that to manually set up all your partitions prior to going through the installation. Let me know how that goes or if you run into problems.

Cheers,
John

---

### Post by tobiasolesen on 2009-05-05
Hi John...

I tried doing what you suggested but I still get the same problem. But Gparted a least tells me that it has something to do with 4 primary partitions. My xp has 3 primaries that it uses... 

so I still can't get the partitions I want. I am know considering waiting till my exams are done with and then do a clean install. 

other ideas?
tobias

---

### Post by Topsiho on 2009-05-05
A hard disk can have no more than 4 primary partitions. If you need more then you should have no more than 3 primary partitions, and one extended partition as a container for a number (up to 16?) of logical partitions.
So you should make room for an extended partition, and then in this create the logical partitions that you need.

Hope this helps :)

Topsiho

---

### Post by caljohnsmith on 2009-05-05
> **Topsiho said:**
> A hard disk can have no more than 4 primary partitions. If you need more then you should have no more than 3 primary partitions, and one extended partition as a container for a number (up to 16?) of logical partitions.
So you should make room for an extended partition, and then in this create the logical partitions that you need.

Hope this helps :)

Topsiho
+1. Tobias, if XP is all ready using three primary partitions, then instead of creating a fourth primary partition, do what Topsiho suggests and create an "extended" partition; inside of the extended partition you can create about as many "logical" partitions as you want. If you still have problems though, how about opening a terminal (applications > accessories > terminal) and posting the output of:
```
sudo fdisk -lu
```
Otherwise let us know how it goes.

John

---

### Post by tobiasolesen on 2009-05-06
Hi Guys!

Thanks for the help!! I managed to change the partition to a logic one and then insert the boot-usb again. Then I could install along side windows and choose the logical partition for this:)

again thanks..

tobias

---

### Post by Topsiho on 2009-05-06
Great :)

Enjoy your system,

Topsiho

---

