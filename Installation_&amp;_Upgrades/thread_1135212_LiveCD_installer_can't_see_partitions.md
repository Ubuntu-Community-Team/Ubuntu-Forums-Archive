---
title: "LiveCD installer can't see partitions"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by jamesclish on 2009-04-24
Hi all

My Jaunty image is finally downloaded and burned, after an overnight 15kbps download...

First of all, I'm upgrading from Hardy - I skipped Intrepid, so I can't just update through the update manager.

When I go to install with the LiveCD, the installer can't see any of my partitions (it just sees one big unpartitioned drive). This is not true, as I have a Vista partition as well as my Hardy partition. If I go  into Vista's disc management utility, all my partitions are there and not corrupt.

The Hardy installer originally installed to my partition with no complaints, but now even the Hardy LiveCD cannot see the partitions.

Any ideas as to why this might be the case? Are there any alternative ways to upgrade?

Thanks!

---

### Post by jncs12 on 2009-04-24
Hi!

I have the same problem!

Please help!

---

### Post by jncs12 on 2009-04-24
I found an workaround to this problem:


[LIST=1]
[*]In Windows Vista or with some other software (like Norton Partition Magic or Paragon Partition Manger), create a new FAT32 partition;
[*]Run installation and the Partition Manager will recognize the NTFS and the new FAT32 partition;
[*]Go to manual partition;
[*]Delete the FAT32 partition;
[*]Create a new partition as a SWAP;
[*]Create a new partition to mount /;
[*]Proceed with installation.
[/LIST]
It worked fine with my computer!

---

### Post by jamesclish on 2009-04-24
> **jncs12 said:**
> I found an workaround to this problem:


[LIST=1]
[*]In Windows Vista or with some other software (like Norton Partition Magic or Paragon Partition Manger), create a new FAT32 partition;
[*]Run installation and the Partition Manager will recognize the NTFS and the new FAT32 partition;
[*]Go to manual partition;
[*]Delete the FAT32 partition;
[*]Create a new partition as a SWAP;
[*]Create a new partition to mount /;
[*]Proceed with installation.
[/LIST]
It worked fine with my computer!

Great! I'll give it a try.

---

### Post by manqueller on 2009-04-29
Try this partition maker, it works fine for me and the home edition is free:  [http://www.partition-tool.com/](http://www.partition-tool.com/)

---

### Post by fchambers on 2009-05-01
> **jncs12 said:**
> I found an workaround to this problem:


[LIST=1]
[*]In Windows Vista or with some other software (like Norton Partition Magic or Paragon Partition Manger), create a new FAT32 partition;
[*]Run installation and the Partition Manager will recognize the NTFS and the new FAT32 partition;
[*]Go to manual partition;
[*]Delete the FAT32 partition;
[*]Create a new partition as a SWAP;
[*]Create a new partition to mount /;
[*]Proceed with installation.
[/LIST]
It worked fine with my computer!
Thanks for the tip.  Unfortunately it doesn't work for me.
Windows XP Pro SP2
2 hdd
First drive has XP and a partition setup for Ubuntu
2nd drive has an NTFS and a FAT32 partition.

Atttempting to install the 64 bit version of 9.04
It sees the second drive but tells me it has no operating system installed.

Looks like I will try 64 bit 8.1 and upgrade

---

