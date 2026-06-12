---
title: "Problem with RAID 5 - faulty spare after sync"
date: 2009-06-30
forum: Installation &amp; Upgrades
---

### Post by The Frog on 2009-06-30
Last weekend I wanted to set up a new multi-purpose server at home. I bought four 1.5 TB drives and wanted to use a RAID 5 for the data (mostly copies of CDs and DVDs - I'm too lazy to stand up and search for them when I sit on my couch ;)).

My partitions are as follows:
sda1 & sdb1: 15GB RAID 1 for the system
sda5 & sdb5: 500MB RAID 1 for /boot
sdc5 & sdd5: 100GB RAID 0 for VMs 
sda6, sdb6, sdc6, sdd6: 1.3 TB RAID 5 for data

I don't have any problems setting up the RAID 0 and both RAID 1s, but whenever I try to create the RAID 5 I get the response:
sda6 - active sync
sdb6 - active sync
sdc6 - active sync
sdd6 - spare

I didn't specify the fourth as spare and when I used the same "mdadm --create ..." command on a smaller sized RAID 5 it worked as intended. When I tried to add the spare to the RAID the computer started to sync and ended repetedly hours later with:
sda6 - faulty spare
sdb6 - active sync
sdc6 - active sync
sdd6 - spare

I use Ubuntu 9.04 64bit starting from the Live-CD and installing mdadm before setting up the RAID obviously. The size of the partitions for the RAID 5 is exactly the same for all four disks. I also tried to install a RAID 1 with the partitions intended for the RAID 5 which worked perfectly. I even tried openSUSE for installing the RAID and ended up with the same error.

Any ideas? Harddisk failure? Bug?

---

### Post by The Frog on 2009-07-01
Well, it seems, that the harddisk that went "faulty spare" has defects. After running smartctl and receiving an error message I am pretty sure about it.

---

