---
title: "Booting installer from HDD (grub)"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by Arancaytar on 2009-10-30
I do not have an optical drive on my computer, so I tried this with the 9.10 iso:

- boot Puppy Linux
- mount the iso
- copy the iso's contents to an empty primary ext3 partition on my hard drive
- created a boot/grub path on this partition, and copied stage1, stage2 and e2fs_stage1_5 into it.
- installed grub on the partition using "setup (hd2,0)"
- created a menu.lst with the following contents:

```

default=0
timeout=10
root=(hd0,0)

title Ubuntu 9.10 Karmic Koala Installer
kernel /casper/vmlinuz
initrd /casper/initrd.lz
root (hd0,0)

```

The kernel apparently loads, but then (after waiting for maybe 15 seconds) says that the root filesystem does not exist after waiting. I am then dropped into a busybox shell.

Does my menu.lst contain an error? 

[This article](http://www.freesoftwaremagazine.com/articles/grub_intro/) told me that the first disk in the boot priority is hd0, and that I should therefore put in hd0,0 instead of hd2,0 as root.

---

