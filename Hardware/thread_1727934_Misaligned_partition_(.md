---
title: "Misaligned partition :("
date: 2011-04-13
forum: Hardware
---

### Post by Azyx on 2011-04-13
Hi.
Have make an RAID 5 of 3 300GB disks and afte hours of syncronizations and stuff I try to format with MBR and partition with EXT4 them but get this error message in Disks Utiliies:

"The partition is misaligned by 2048 bytes. This may result in a very poor preformance. Repartition is suggested"

I reformat with GUID instead and get the same message exept that it said 3072 bytes instead.

It is ATA Seagate with good SMART status.

---

### Post by AllGamer on 2011-05-05
i'm having the same trouble with a RAID5 of many 2TB disks, i've been trying all kind of different sizes in partitions and formats, still the same message

the HDDs are indeed Western Digitals, which i've been reading might have those "advanced format" 4096 instead of 512 problem, so i've also been trying to work around that without much success :(

---

### Post by Azyx on 2011-06-12
> **AllGamer said:**
> i'm having the same trouble with a RAID5 of many 2TB disks, i've been trying all kind of different sizes in partitions and formats, still the same message

the HDDs are indeed Western Digitals, which i've been reading might have those "advanced format" 4096 instead of 512 problem, so i've also been trying to work around that without much success :(

There should be some 2TB disks as i recall.

Do you know some guide to how-to create?

I have som questions:_
Do I make raidcomponents from partitions and not devices?
Do I need to partitions every partition before I make a raid5 and ho in that cae? ext2, exxt 3 or ext4?
How do I partition the raidarray?

When I think i.m finished and i check the array (md0) it says: Degraded and idle. How do I fix it?

/Cheers

---

