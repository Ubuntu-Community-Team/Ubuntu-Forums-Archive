---
title: "Faulty HD now dead HD with upgrade to Feisty"
date: 2007-10-13
forum: Hardware &amp; Laptops
---

### Post by nanogeek on 2007-10-13
Hi

I have been running Edgy on a Pentium III using a primary drive of 6GB which contains the OS and the swap files and a 20gb hard drive for my data files. The 20gb drive was dicey at best, and I think the boot sector was fried, which was why I was unable to set it up as the primary drive.

Be that as it may the system ran.

I now updated to Feisty (in anticipation of updating to Gusty) and when it came time to reboot I got an endless string of error messages that come in three basic flavors

(1) [####.######] ata1.01 exception Emask 0x0 Sact Serr 0x0 action 0x2 frozen
(2) [####.######] ata1.01 Cmd c8/00i08:18:00:00/00:00:00:00:00/f0 tag 0 cdb 0x0 data 4096 in
(3)Buffer I/) error on device sdb logical block 0 3


After disconnecting the power and the data cable to the 20gb drive, I can boot the system, but I get a terminal command line interface with a message that says  ctrl-D will resume the boot sequence. I press cntrl-D and get into the Ubuntu GUI.

I assume that all this has to do with the dead HD, which still appears in /media

Questions:
Is there anything I can do to continue using the defective drive, as it was able to run under Edgy. despite what I suspect are bad sectors, including in the boot sector? 
Assuming that the disk is a lost case, how do I tell Ubuntu that the disk is no longer a part of the system so it won't look for it during boot? I assume I need to unmount it.

Thanks

---

