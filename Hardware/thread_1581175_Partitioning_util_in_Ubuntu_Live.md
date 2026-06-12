---
title: "Partitioning util in Ubuntu Live"
date: 2010-09-24
forum: Hardware
---

### Post by thrubovc on 2010-09-24
Hello folks, I happened to screw up my disk with Ubuntu as a dual boot, my Mac OS doesn't recognize the ubuntu filesystems and thus it thinks it is a MBR (master boot record), and not a GUID. I think that by removing ubuntu together with its partitions would resolve that problem, but I cannot find out how. When I run the latest ubuntu live cd or installation, it will only allow me to mess with the partitions provided that I create new partitions for ubuntu ant install it there afterwards. any ideas how I could use that utility to remove all the linux partitions, leave the mac partitions untouched and skip installation? Thanks

---

### Post by efflandt on 2010-09-24
Boot to a live system from the install CD, then use System, Administration, Gparted.

However, if grub is in the mbr of the drive, removing the Linux partitions will not necessarily fix a boot problem, because that is only part of grub and if it cannot find the rest of itself (in /boot/grub of the Linux partition), it will not boot anything.  So you may need to restore whatever mbr Mac OS uses.

Did you put the grub boot loader in the mbr or on a partition?

---

### Post by thrubovc on 2010-09-24
well loading is not the problem, mac os works well, it just cannot work with the linux filesystems. I found the util in ubuntu so now I just have the mac os partition and about 20 gigs of unallocated  disk space and can do nothing about it. I will probably have to reformat the partition as the status stayed at MBR and didn't go back to guid after i'd removed the linux partitions. what a pity.

---

### Post by srs5694 on 2010-09-24
First, download and install [GPT fdisk (gdisk)](http://sourceforge.net/projects/gptfdisk/files/) in Ubuntu. Then, run the following commands in Ubuntu and post their output, preferably between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings to improve legibility:

```

sudo fdisk -lu /dev/sda
sudo gdisk -l /dev/sda

```

If you've got additional hard disks, run the same commands on them, too.

This will show us how both your MBR and GPT partitions are set up.

Speaking more broadly, I don't think that OS X's inability to parse the Ubuntu filesystems could possibly confuse it about how the disk is partitioned (MBR vs. GPT). If OS X thinks the disk uses MBR, that's probably either because it does or because there's a corrupted [hybrid MBR](http://www.rodsbooks.com/gdisk/hybrid.html) on the disk. There could be something else going on that's contributing to the trouble, though, like mis-set partition type codes.

---

