---
title: "System not recognize Marvell Sata RAID disk on boot."
date: 2011-05-25
forum: Hardware
---

### Post by leoadias on 2011-05-25
Hi,

Yesterday I upgraded my system to Ubuntu 11.04. After upgrade, the system not boot. a Kernel panic occurred informing that the disk book is inaccessible.

My system boots on a disk connected to a Marvell Sata Raid 88SE6145 controler. No raid configured, just the disk.

Before upgrade, it was using kernel 2.6.35-28 and I had to use the boot option "ahci.marvell_enable=1" to recognize the disk and boot. It was working fine.

After upgrade, the process installed the kernel 2.6.38-8 and the system not recognize boot disk anymore and the boot process fail.

It seems that the new kernel (or new grub version) does not accept the "ahci.marvell_enable=1" boot option, so it doesn't find the disk and not boot.

I had to choose an old kernel image to boot.

Any ideas?

---

