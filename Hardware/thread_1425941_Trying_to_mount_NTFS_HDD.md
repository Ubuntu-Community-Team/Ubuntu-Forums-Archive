---
title: "Trying to mount NTFS HDD"
date: 2010-03-09
forum: Hardware
---

### Post by elzzid on 2010-03-09
So I am quite new to Ubuntu and Linux in general, but I have been doing my best to just look things up and learn on my own. I seem to have hit a bit of a snag however, and I was hoping for some insight.

I have two HDDs on my desktop computer.
-One is a IDE 120GB that contains Ubuntu ONLY
-The other is a 320GB SATA HDD that contains Windows XP ONLY

I am trying to mount the SATA so that I can snag files from it like, music, documents, etc. The problem I'm having is that when I do a fdisk -l all it is showing is the following:

Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb21189d6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14333   115129791   83  Linux
/dev/sda2           14334       14946     4923922+   5  Extended
/dev/sda5           14334       14946     4923891   82  Linux swap / Solaris

No mention whatsoever of the SATA HDD... I was just wondering what is going on? Could it have to do with the fact that I am booting straight into Ubuntu? I haven't been able (haven't tried REALLY hard tbh) to get GRUB working so in order to get into Ubuntu I just go into my BIOS and switch the IDE to be HDD 1 and the SATA to be HDD 1 when I want to get into XP.

Thanks ahead of time for any helpful advice.:)

---

