---
title: "Unable to get through Ubuntu 8.04 after installation"
date: 2009-04-10
forum: Installation &amp; Upgrades
---

### Post by amarjarubula on 2009-04-10
Hi,

I have downloaded Ubuntu 8.04 and installed on my computer with Wubi from Windows Vista Home Basic. The installation went smoothly and was successful.

I have restarted and selected Ubuntu. After selecting Ubuntu it went through Checking Installation and then **Checking New Partition**. At this point I got a dialog box saying
**No root file system is defined. Please correct this from the Partition menu** It says to press OK. I did but it did not go away and kept persisting. I got vexed and tried to reboot and again I got the same error. Pls help anybody.

---

### Post by cariboo on 2009-04-10
When setting up a partition you have to set a mount pont. Boot from the LiveCD and when at the desktop go to System-->Administration-->Partition Editor and check the mount point of you / partition, it should be set to /.

Jim

---

### Post by amarjarubula on 2009-04-11
Tx for replying,

I have tried what you have said. However I could not find where to actually mount. And I have seen a weird thing that my Vista partition was not recognized and it is showing 111.79 GB as an unpartitioned drive. If I do something to the drive, I understood that I will lose all my data. Pls explain me what is actually happening. I am totally new to Linux environment.

---

### Post by polkadotteapot on 2009-04-11
[http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)

This website and the links on it have some information about gparted and partitioning.

If you're just reying wubi you only need to use the partitioning information.

---

### Post by amarjarubula on 2009-04-11
Tx but this did not help. 

I have installed the Partition tool and executed. It is showing that I have different partitions. However, Ubuntu is still showing all the disk space as unpartitioned. 

I don't know what to do. So, I tried installing Ubuntu for 4 times all the time, the same problem occurs.

---

