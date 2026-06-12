---
title: "How to increase size of partition"
date: 2009-10-14
forum: Installation &amp; Upgrades
---

### Post by vksingh on 2009-10-14
Hi,

I am install Ubuntu with giving / home to be 20 GB. I am working on it. But, now the size is insufficient, so I attached another hard disk and I want to increase the size of /home .

Please help............:(

---

### Post by dstew on 2009-10-14
If you attached another hard disk, what you probably want to do is create a **new** /home partition on the new disk. That is fairly simple. You create and format the new partition, copy your files over to it, then edit the /etc/fstab file to mount the new /home partition at boot time. Here is a [How-To for creating a new /home partition]("http://www.psychocats.net/ubuntu/separatehome"). The How-To creates a new partiton on the same disk, but you can use a different disk if you want.

It is possible to combine two different physical partitions on two different disks into a single logical partition, if you want to try that instead. You would use the technique of logical volume management (LVM) to do it. However, that is an advanced technique, and I don't think Ubuntu provides a simple way of doing it, other than re-installing from an Alternate Install CD.

---

