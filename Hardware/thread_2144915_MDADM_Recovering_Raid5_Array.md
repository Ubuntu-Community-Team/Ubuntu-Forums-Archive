---
title: "MDADM Recovering Raid5 Array"
date: 2013-05-13
forum: Hardware
---

### Post by Hondo88 on 2013-05-13
I have a home server that runs Ubuntu 10.04, I had an issue with the OS drive. I reinstalled Ubuntu 10.04 on the OS drive (sba) and then re-installed mdadm. I recovered the array a year or so ago and my notes say to use "mdadm --create /dev/md0 --chunk=64 --level=5 --raid-devices=3 /dev/sdb1 /dev/sdc1 /dev/sdd1" and I used that. 

The Disk utility in Ubuntu says State: Degraded, Action: Recovering (25% done), and /proc/mdstat says recovery=32% 

But looking at some of the how to's on the interweb, they say to use mdadm --assemble. 

Now I'm worried that I'm currently deleting all my data ? Did I screw things up? Should I stop the recovery? 

Help.

---

### Post by SaturnusDJ on 2013-05-14
Yes, create is wrong. Assemble is the only good way of starting a already present array. Create is only used once and in situations of corruption, problems, etc.

If you created with the exact same parameters as the first time, the data most likely will still be there.
I guess by this time the process is already done.

---

### Post by Hondo88 on 2013-05-14
SaturnusDJ, thanks for the reply. 

I let it finish its sync and the raid seems to be active and intact. I'm currently backing up any newer data that I didn't have backed up. 

I haven't added the array to the mdadm config file, but I have 2 immediate concerns:

In the nautilus browser, I have 2 locations. The original 4TB Filesystem (RAID) that I can access and see all of my existing data and a new 2TB Filesystem. When I click on the 2TB filesystem, I get an error "Unable to mount. One or more block devices are holding /dev/sdb1". But, /dev/sdb1 is device 0 of 3 in the 4TB raid. I'm not sure how this file system got linked to this drive or how to remove it. 
EDIT: I Updated the mdadm.config and fstab, rebooted and the 2TB issue is gone. 

Also GParted lists the raid /dev/md0 as /dev/md0p1 and gives the following warnings; /dev/md0p1: No such file or directory, fatal error -- couldn't initialize XFS library, Unable to read contents of this file system. Is this a concern? 
EDIT: This is still shown, but not sure if its a problem?

---

### Post by SaturnusDJ on 2013-05-22
Looks like Gparted is missing something needed to read XFS partitions. If you don't experience problems with mounting etc, then it doesn't matter.

---

