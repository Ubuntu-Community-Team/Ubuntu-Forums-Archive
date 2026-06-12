---
title: "EXT4 for older Hard Drive causing drive to fail?"
date: 2013-05-24
forum: Hardware
---

### Post by SpecChum on 2013-05-24
Hey all, new to these forums but not new to Linux in general :)

I'm having a weird issue with an old Maxtor 500Gb hard drive that  completely locks up when formatted to EXT4 in Linux with GParted but  works absolutely fine when formatted to NTFS in Windows!

And when  I say locks up, I mean locks up, it's not even recognised in the BIOS  anymore unless I do a full power down, then there it is again!

Oddly,  the drive first did this 2 years ago but has since been formatted to  NTFS it worked fine and dandy, no issues at all.  I decided yesterday to  EXT4 it again, and BANG! Oops.

SMART returns all OK and  badblocks reports no (more) bad blocks(I've got a few but these are from  years ago and the drive has been working in Windows fine for years with  these).

Are there any issues with EXT4 on older drives? Also as a  point of note, I've got the Seagate version of the same drive which  continues to work fine on EXT4 but is a year or so newer. Firmware  related perhaps?

Many thanks

---

### Post by ajgreeny on 2013-05-24
You don't say how old it is but I have Maxtor 160 and 40 GB drives, both from Feb 2005, which have both always worked faultlessly with ext4 filesystems on, and before that with ntfs, when they were both Win XP.

I somehow doubt a firmware problem and am just wondering if it has been in a raid assembly in the past.  Perhaps you need to use gparted and make a new partition table on the device, as opposed to just re-formatting it.

---

### Post by lethall1 on 2013-05-24
Why didn't you try to format it in... FAT32, or ext3, or smth else? try in from win, and from linux (i mean format it in windows). you have to make experiments ;)

---

### Post by SpecChum on 2013-05-25
> **ajgreeny said:**
> You don't say how old it is but I have Maxtor 160 and 40 GB drives, both from Feb 2005, which have both always worked faultlessly with ext4 filesystems on, and before that with ntfs, when they were both Win XP.

I somehow doubt a firmware problem and am just wondering if it has been in a raid assembly in the past.  Perhaps you need to use gparted and make a new partition table on the device, as opposed to just re-formatting it.

Thanks for the reply, it's probably about 7 years old; 500Gb was about the biggest you could get when I got it, so that might give you some idea.

It has been part of a RAID array, yes, in Windows, but I've put a new partition table on it a few times over the years.

It does format to EXT4 fine and it does work for a short while, as in it doesn't just fail right away if I format it to EXT, it can be a couple of hours.

It's no biggie really, I've got 5 disks in total so using this one for Windows only is not a problem, I was just curious :)

---

### Post by SpecChum on 2013-05-28
I've got to the bottom of this 


It would appear there's something physically wrong with the drive near the end, as when I benchmark the (unformatted) driver it locks up at the same place every time, which is about 2/3rds in. Why badblocks doesn't make it bail I don't know, but this happens each and every time I benchmark the drive whether it's NFTS, EXT4 or unformatted.


In the bin it goes...

---

