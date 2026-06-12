---
title: "Manual Partitioning"
date: 2009-02-07
forum: Installation &amp; Upgrades
---

### Post by stoneimplementor on 2009-02-07
Does anyone know if there is a guide out there for manually partitioning?  I'm trying to install ubuntu on a 10 GB partition I set up for it when I first installed the hard drive.

---

### Post by avtolle on 2009-02-07
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot) if doing a dual boot.

---

### Post by avtolle on 2009-02-07
Generally, on manual partitioning, you need to have a minimum of two partitions; one for root and one for swap. As you have already created a partition, during the installation, when you get to step 4, select manual and the partition to use. Unless you created another partition for swap, you will need to resize the existing partition to provide room for swap. Once that is done, if necessary, set the file system for the partition as ext3, and give it a mount point of /. For the swap partition, designate is as swap in the file system, and /swap as the mount point. Depending on how many other partitions you have on the drive, you may well designate both the root and swap partitions as logical partitions, given the general "no more than four primary partition' rule. Please do not hesitate to ask further questions.

---

