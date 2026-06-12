---
title: "Problems with SATA drives Ubuntu 8.10"
date: 2009-01-26
forum: Installation &amp; Upgrades
---

### Post by finker282 on 2009-01-26
Hi, using the crunchbang derivative and I can not get my SATA drive to be recognized. It is recognized in the bios and xp will boot from it but no luck on the live cd. In terminal if i type 'sudo fdisk - l' the only drive listed is a 10gb ide drive. I have tried switching from SATA to RAID in the bios but either way the drive is not recognized. It has 3 partitions 2 ntfs one ext3.

Any help would be appreciated :)

---

### Post by mount_evans on 2009-01-30
I am in the same boat, except I haven't tried the RAID thing yet.  My motherboard is an XFX 8200 GeForce, and my drives are Seagate Barracudas.  What is your hardware?  Have you heard anything?

---

### Post by dabl on 2009-01-30
In BIOS, try setting the SATA mode to "AHCI", then boot the Live CD and see whether it is recognized.

---

### Post by mount_evans on 2009-02-01
> **dabl said:**
> In BIOS, try setting the SATA mode to "AHCI", then boot the Live CD and see whether it is recognized.

Sorry, been following this up in other threads.  AHCI, RAID, makes no difference.

---

### Post by r m h on 2009-02-01
See my possible fix in this thread:

[http://ubuntuforums.org/showthread.php?t=1057366&highlight=SATA+RAID](http://ubuntuforums.org/showthread.php?t=1057366&highlight=SATA+RAID)

---

