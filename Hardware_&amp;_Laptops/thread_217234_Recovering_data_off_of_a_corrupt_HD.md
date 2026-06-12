---
title: "Recovering data off of a corrupt HD"
date: 2006-07-16
forum: Hardware &amp; Laptops
---

### Post by progrock on 2006-07-16
My friend's HD has become corrupt (not sure why.. not sure whats actual broek either).... It was a windows pc, so i'm guessing its ntfs.  I was hoping linux could come to the rescue and maybe the live cd will have some way for me to get data off of the corrupt disk.

If anyone can point me in the right direction, it would be amazing.

---

### Post by Jagot on 2006-07-16
It depends how corrupt the disk is.  Assuming files are retrievable, Ubuntu has never automounted NTFS partitions for me.  You may want to try a Knoppix Live CD for that:

[http://www.knoppix.org/](http://www.knoppix.org/)

If you have the Ubuntu CD hanging around you may want to give it a go but you'd need to manually mount the partitions:

[https://help.ubuntu.com/5.10/ubuntu/faq/C/fg-windows-partitions.html](https://help.ubuntu.com/5.10/ubuntu/faq/C/fg-windows-partitions.html)

---

### Post by tturrisi on 2006-07-17
Find out exactly what friend means when says "drive is corrupted".  Hard disk failure?  Corrupted boot files?  Different solutions for different causes.  Best way to test is to yank the drive & slave it in another computer & if drive is accessable then backup data to other drive or media.  If just corrupted windows boot files then can repair by booting w/ the xp cd.

---

