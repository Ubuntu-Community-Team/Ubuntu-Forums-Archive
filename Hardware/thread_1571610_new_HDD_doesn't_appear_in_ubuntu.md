---
title: "new HDD doesn't appear in ubuntu"
date: 2010-09-09
forum: Hardware
---

### Post by raptor222 on 2010-09-09
Hi,
I decided to install a new hard disk in my computer, I installed an Western Digital 80 GB IDE I had.
Although the new HDD is recognized by the BIOS and I even installed Windows XP on it, in Ubuntu it isn't recognized (not even in the live CD).
My PC also has an IDE DVD-ROM and two SATA HDD's.
In my BIOS the two SATA HDD's are configured on **channel 0** as **master** and **slave**.
My DVD is configured on **channel 1** as **master** and the new HDD as **slave**
and here is my "fdisk -l" output:
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00093981

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19458   156289024   83  Linux

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c91f8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         498     3998720   82  Linux swap / Solaris
Partition 1 does not end on cylinder boundary.
/dev/sdb2             499        9730    74148865    5  Extended
/dev/sdb5             499        9730    74148864   83  Linux
shaul@shaul-desktop:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found memtest86+ image: /boot/memtest86+.bin
done
```

update:
If I change the boot order in the BIOS and boot into the problematic drive (has win xp) I can see the ubuntu drives.

---

### Post by PRC09 on 2010-09-09
Seen some odd things lately with IDE drives.Try it with the jumper on the new drive as cable select.....maybe...

---

### Post by Hobgoblin on 2010-09-09
> **raptor222 said:**
> 
My PC also has an IDE DVD-ROM 
My DVD is configured on **channel 1** as **master** and the new HDD as **slave**


Try with the HDD as master and the DVD as slave.  Preferably using cable select with the drives in the relevant positions on the cable (master usually on the end) rather than setting the jumpers on the drives to master and slave.

---

### Post by raptor222 on 2010-09-10
Thank you PRC09 and Hobgoblin the your solution worked perfectly.
both IDE devices on cable select and HDD as master and DVD slave.

---

