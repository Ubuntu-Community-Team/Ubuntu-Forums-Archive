---
title: "Can't boot Jaunty from external harddisk"
date: 2009-04-23
forum: Installation &amp; Upgrades
---

### Post by laizhuoxun on 2009-04-23
Hi there. I have successfully installed Ubuntu 8.10 onto my external harddisk, and I can boot from it normally, as if from an internal disk. But when I formatted the external one and installed Ubuntu 9.04 onto it, boot failed. The installation went quite well and it recognized my external HDD. However every time I try to boot from external disk, it drops to a BusyBox command line and tells me it can't find my root partition. I used the command "ls -al /dev/disk/by-uuid" and find out that my / partition, as well as any other partitions on USB storage devices, is not shown. It seems that the Fast Boot feature bypasses several tests including detecting USB Drives (my USB mouse is detected however). Any ideas to disable the fast boot, or to solve this problem?

I have separated the /boot partition to /dev/sdb1, so this partition is visible to the kernel. And my / partition is /dev/sdb5, immediately after /dev/sdb1.

---

