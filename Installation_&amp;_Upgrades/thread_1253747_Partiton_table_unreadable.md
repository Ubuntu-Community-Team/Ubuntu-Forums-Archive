---
title: "Partiton table unreadable"
date: 2009-08-30
forum: Installation &amp; Upgrades
---

### Post by crashed111 on 2009-08-30
Hi guys

Ive just moved to Ubuntu as ive found it to be very up to date and good on performance I even went 64 bit!

However on my primary drive I deleted an old partition using gParted (from a live CD) which was part of a logical partition set. 

I wanted to merge this with my current home partition however my partition table now seems to have become partially corrupt as I can still boot into my system and access all of my partitions but when I try to use gParted or Partition Magic I just get given errors which basically seem to point towards I have a bad partition table. Partition magic offers to fix these but it cant and just tries to do it over and over again.

Im not sure if anyone can be of help but im started to get a bit worried now

Thanks in advance

---

### Post by zvacet on 2009-08-30
Try to shrink logical partition in way that partition you deleted stay outside of logical partition as unallocated space.That unallocated space you can merge with other partition.

---

### Post by crashed111 on 2009-08-31
Thanks for your reply

At current I am unable to get any tool to recognize the drive to enable me to repair it it appears that where I deleted the NTFS partition it only got partially deleted.

Gparted gives me this error

======================
libparted : 1.8.8
======================
Invalid argument during seek for read on /dev/sda

Are there ant other tools I can try? fsck gives me errors relating to be unable to work out the drives partiton table.

---

### Post by Bartender on 2009-08-31
Create a GPartedLiveCD (GPLCD).  Similar to but not the same thing as gparted on the Ubuntu LiveCD. GPLCD is availbale on SourceForge.  You burn the download to a CD-R just like an Ubuntu CD.  Boot from the resulting disc.  It asks questions about your video drivers and such.  Try the default setting first.  If that doesn't work try Fail-Safe mode then forcevideo.
See if you can delete the errant partition from the GPLCD.  If not, are you in a position to delete all partitions and start over again?

---

### Post by crashed111 on 2009-08-31
> **Bartender said:**
> Create a GPartedLiveCD (GPLCD).  Similar to but not the same thing as gparted on the Ubuntu LiveCD. GPLCD is availbale on SourceForge.  You burn the download to a CD-R just like an Ubuntu CD.  Boot from the resulting disc.  It asks questions about your video drivers and such.  Try the default setting first.  If that doesn't work try Fail-Safe mode then forcevideo.
See if you can delete the errant partition from the GPLCD.  If not, are you in a position to delete all partitions and start over again?

Booted from Gparted unfortunately gives me the same error as the current gParted. I did forget to mention that as far as gParted is concerned my disk is blank and has no partitions on at all which I find confusing.

Its a good tool though will be adding it to my army of tools fits in my CD walltet nicely next to Clonezilla :)

As far as starting again goes yes that will be kinda fine however I dont have the space to back up all my data however I can back up all the important stuff which I do regulary anyway, however I am still trying to do it as a last ditch attempt.

---

