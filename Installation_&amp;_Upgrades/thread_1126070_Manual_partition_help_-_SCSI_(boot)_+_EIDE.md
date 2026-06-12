---
title: "Manual partition help - SCSI (boot) + EIDE"
date: 2009-04-15
forum: Installation &amp; Upgrades
---

### Post by OWize1 on 2009-04-15
[FONT="Arial"]**Can someone please tell me exactly what to enter/create for manual partitioning? Complete the table below.**

I have no choice - I must boot from my 4GB SCSI drive, but I would rather not use the SCSI drive at all if possible (but it's not possible). From my research I believe I must create a "/boot" partition that is twice the size of my RAM, then I must create a small "swap" partition on the EIDE drive. Can I then devote/partition the remainder of the 2nd (EIDE) drive to installing Ubuntu 8.10? How do I divide and partition the 40GB EIDE drive? Please complete the table below for me. This old computer only has 512MB RAM.[/FONT] 

[FONT="Courier New"]**Device :: Type :: Mount_Pt :: Size**
/dev/sda
 /dev/sda1 :: ext3 :: /boot :: 1024MB
/dev/sdb
 ??? :: ??? :: ??? :: ???[/FONT]

[FONT="Arial"]I just noticed as I was typing this out, the 2nd hard drive should be /dev/hda, not /sdb - is this the root of my problem? How do I correct that?[/FONT]

---

