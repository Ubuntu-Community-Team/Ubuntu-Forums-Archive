---
title: "Attempting to format my boot partition"
date: 2009-11-03
forum: Installation &amp; Upgrades
---

### Post by artix123 on 2009-11-03
Hi guys,

Currently having system state of:

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1020     8192000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *        1020        6757    46080000    7  HPFS/NTFS
/dev/sda3            6757       23249   132468052    7  HPFS/NTFS
/dev/sda4           23250       38913   125821080    5  Extended
/dev/sda5           28229       38913    85825715    7  HPFS/NTFS
/dev/sda6           23250       28228    39993754+  83  Linux

sda1 -> Vista, recovery
sda2 -> Vista, boot
sda3 -> storage
sda5 -> 7
sda6 -> Ubuntu 9.10

Installed 7 and wants to remove Vista, but sda2 is my current boot partition; was wondering how do I go about formatting sda2 and then restoring the grub2 bootloader.
Any help would be appreciated. Thanks! :)

---

### Post by bashphoenux on 2009-11-03
sda2 is your boot partition and you have your Grub in that drive????
format the partition and get grub re-installed using super grub disk :)
google for super grub disk

---

### Post by artix123 on 2009-11-04
Ah never mind I solved it. My boot partition was vista, deleted it, won't boot. After a few Windows 7 Startup repairs, booted into Windows 7. Used livecd to restore grub2, did a update-grub, voila!

:)

---

