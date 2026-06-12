---
title: "cdrdao hang on read"
date: 2006-10-23
forum: Hardware &amp; Laptops
---

### Post by danielph on 2006-10-23
Hi,

I am getting problems with cdrdao locking up with a particular device. I have isolated the device and checked cabling and hardware settings. I can only put if down to firmware, but I believe that is the latest. Here is the problem:

cdrdao read-cd or cdrdao read-toc cause complete lock up of system.

Reproducible: Always

Ver 1.2.1 and 1.2.2
Other Info:
libscg ver schily-0.8
SCSI-3/MMS Version 2 Option 0x0000

Hardware:
Benq LS DW1655 rev BCDB (sept 06)
Software:
Linux 2.6.17-10 and previous
Dist: Ubuntu 6.10 edgy and 6.06 dapper



any ideas?

Dan

---

### Post by jpolega on 2007-04-02
I read somewhere else that it was because the IDE channel was pushing the drive too fast.  (it was a gentoo forum, I think)

I backed my POS dvd burner off from UDMA2 to UDMA1 and it appears to be working fine now.  You can do this with hdparm...but the exact switch escapes me right now.  "man hdparm"

---

### Post by danielph on 2007-04-03
As everything else was working on the Benq I decided to stick an old Pioneer DVD in as a slave for the purpose of ripping CD's and it works really well. I just won't use abcde with the BenQ

---

