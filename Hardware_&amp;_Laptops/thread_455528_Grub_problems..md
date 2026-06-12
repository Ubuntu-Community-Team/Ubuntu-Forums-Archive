---
title: "Grub problems."
date: 2007-05-26
forum: Hardware &amp; Laptops
---

### Post by AmbigFish on 2007-05-26
Hey guys. I did a lot of partitioning editing and installed a Windows OS. I then had to restore my grub bootloader.

Well, I go into my Ubuntu 7.04 LiveCD and go into the terminal and type the following:

```
sudo grub
find /boot/grub/stage1

```
it gives me [hd0,2]
```
root (hd0,2)
setup (hd0)

```

It then tells me it was done, I type quit and reboot. Grub re-appears and I select Ubuntu and I get:

Error 17: Cannot mount selected partition

Please help. Thank you.

---

### Post by merlinus on 2007-05-26
It is possible that your UUIDs changed during all the partitioning.

Boot from the live cd, and in a terminal enter:

```

sudo fdisk -l
blkid

```

The first will give you the partitions and filesystems.  The second will give you the UUIDs.

Check these against the entries in /etc/fstab.

Good luck!

-merlin

---

### Post by AmbigFish on 2007-05-28
I have no idea what I'm looking for or at, but I think you're right about the UUIDs. I know the partitions got swapped around (best way to describe it). Like, my Swap used to be 3 out of 4 partitions on the HDD, now it's last, and my Ubuntu partition was last and now it's 3 out of 4.

Here is what my sudo fdisk -l says:

```

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         509     4088511   12  Compaq diagnostics
/dev/sda2   *         510        7519    56307825    c  W95 FAT32 (LBA)
/dev/sda3            7520       14462    55769647+  83  Linux
/dev/sda4           14463       14593     1052257+  82  Linux swap / Solaris

```

Here is what my blkid says:

```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         509     4088511   12  Compaq diagnostics
/dev/sda2   *         510        7519    56307825    c  W95 FAT32 (LBA)
/dev/sda3            7520       14462    55769647+  83  Linux
/dev/sda4           14463       14593     1052257+  82  Linux swap / Solaris

```

Here is what is in my /etc/fstab when I type sudo gedit /etc/fstab:

```
unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda4 swap swap defaults 0 0
```

Please help me. I don't want to reformat at all.

---

### Post by AmbigFish on 2007-05-28
apparently I didn't look at the right fstab.

Here is the one from my Ubuntu partition:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=4ae98113-c8bc-49cb-b934-64e4c5ec62d4 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=0E4E-05CE  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=320D-180E  /media/sda2     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda3
UUID=1aaa508e-1abd-4956-a32c-0eeaeaebf150 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/swapfile1 swap swap defaults 0 0
```

It looks like it has my stuff wrong, as my sda4 is my swap, and my sda 3 is my ubuntu (it looks like it has the old information???)

Does this look right?

---

### Post by merlinus on 2007-05-28
blkid is not giving you the UUIDs you need to change in fstab.  Maybe because you booted from the live cd.

You can try this:

sudo vol_id /dev/sda3

and then:

sudo vol_id /dev/sda4

This should give you the UUIDs for these partitions, which you can place in /etc/fstab.  Just be sure you are editing the correct one!  And you may have to change around / and /swap as well.

BTW, it is very unlikely that the UUIDs for your windows partitions (sda1, sda2) have changed.

Good luck_

-merlin

---

