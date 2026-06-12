---
title: "Trouble installing ubuntu 9.04 on Raid 0"
date: 2009-07-19
forum: Installation &amp; Upgrades
---

### Post by eekie on 2009-07-19
At the moment I run ubuntu 9.04 on a sata disk. I am trying to install  ubuntu now at a free partition of a nvidia fake raid striping disks, also containing ntfs partitions with windows and data.
I followed the instructions at  help.ubuntu.com/community/FakeRaidHowto. If I install dmraid and abstain from installing the grub bootloader, the process runs fine. After mounting the raid partition I can see all the directories and files of the freshly installed ubuntu.
So far so good, but when I continue with the instructions at first everything goes smoothly, that is after creating the directory: /target/.  But when it comes to the command: 
grub> find /boot/grub/stage1 
I get the output:
unknown partition table signature
(hd1,1)
(hd1,4)
The latter two partitions are the boot partitions of suze and ubuntu on the sata disk.

Somehow the nvidia raid driver does not get along with grub.
How do I solve this problem?

---

