---
title: "How do you tell the system about a new disk partition without having to reboot?"
date: 2009-06-19
forum: Installation &amp; Upgrades
---

### Post by bobtestact on 2009-06-19
Here's what happened:

1: I used GParted to delete all partitions on a disk (/dev/sda), and then I created one new partition.  I applied the changes, and then GParted claimed that the partition "/dev/sda1" had now been created.

2: I couldn't format a filesystem on the new partition, because /dev/sda1 did not actually exist when I did "ls /dev".

3: So I rebooted.  Upon booting, Linux discovered /dev/sda1.  Then I could format the filesystem.

So my question is:  Is there a way that I can have the disk "rescanned" and force the /dev/sda* entries to be updated to reflect the new partitions?    That would save me a reboot in the future.

---

### Post by dstew on 2009-06-19
After you create the new partition, try **sudo fdisk -l**. That should list it. Maybe that will cause a new entry to be created in /dev, but I am not sure. Just something to try.

---

