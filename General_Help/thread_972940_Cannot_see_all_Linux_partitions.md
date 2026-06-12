---
title: "Cannot see all Linux partitions"
date: 2008-11-06
forum: General Help
---

### Post by RobHK on 2008-11-06
I have just installed 8.10 on a desktop with multiple partitions on two internal hard drives, already running XP and Mint 5 (which is Ubuntu 8.4 based). I used separate new partitions for / and /home. All Linux partitions are ext2.

After installation, "Computer" in 8.10  displays all NTFS partitions but only one Linux partition -- the one where "/" is. Filesystem displays. All displayed partitions appear with a mounted icon, but if I click I have the message: "Unable to mount location. Internal error: no mount object for mounted volume". However if I click again, I have normal access to the partition. If I close it and come back later, there is no error message and access is normal. Partitions appear in "/media" only after mounting (normal behaviour).

When I go to Mint, it is the same. NFTS partitions are displayed, but among Linux partitions, only Mint's "/" partition. But I do not have the error message.

I have an ext2 partition on a USB external drive and this displays on Mint and Ubuntu. All partitions are visible in Partition Editor in Mint and Ubuntu.

Yet on my laptop, where I have Ubuntu 8.4 and Mint 5, "Computer" displays all drives, though  Linux drives are initially unmounted (not "Filesystem"), but they mount by simply clicking on them, which is the normal behaviour. (No error message here.)

I have had multiple Ubuntu/Mint systems on the desktop before, and IIRC they worked normally, like the laptop, so this could be an 8.10 issue.

---

