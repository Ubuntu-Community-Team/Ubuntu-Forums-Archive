---
title: "Qemu Partition problem"
date: 2008-12-25
forum: Installation &amp; Upgrades
---

### Post by Nosss on 2008-12-25
Hi,

I am running Ubuntu through an emulator(QEMU) and I am attempting to install it properly with a partition and Gparted does not detect my hard-drives. When i type in fdisk -l

Disk /dev/hda: 1073 MB, 1073741824 bytes
255 heads, 63 sectors/track, 130 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         130     1044193+  fd  Linux raid autodetect

However it is only 1073MB?!? I have tried re-sizing it but it says its already at maximum space allowed...but i have 160GB free and have allocated 40GB and also 500GB external hard-drive, which is where I am running the emulation from. Any ideas?

---

