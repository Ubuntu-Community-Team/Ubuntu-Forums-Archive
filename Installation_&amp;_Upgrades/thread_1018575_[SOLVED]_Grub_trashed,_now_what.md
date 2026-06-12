---
title: "[SOLVED] Grub trashed, now what?"
date: 2008-12-22
forum: Installation &amp; Upgrades
---

### Post by ajblogger on 2008-12-22
Like some mindless moron on a late night, I hit "Install Xubuntu" and used Guided Formatting to completely linux-ize...My flash drive. Improper way, improper results. Grub worked fine for the first night, allowing me to boot into Vista, Xubuntu, and memtest. I liked it. A bit strange, but it was okay. Then, the next morning, I get a message telling me that "GRUB stage1.5...  GRUB Error 17." When I take out the flash drive and boot, I get "GRUB stage1.5...  GRUB Error 21." I've been monkeying around for hours with my device.map and menu.lst, no avail. I booted off of a Ubuntu Hardy live disc and created a startup usb drive properly. And that's where I am.

This is the result of ```
fdisk -ul
```:
```

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x83557f0f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048     3074047     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *     3074048   123783167    60354560    7  HPFS/NTFS
/dev/sda3       123783168   165726207    20971520    7  HPFS/NTFS
/dev/sda4       165726208   234438655    34356224    f  W95 Ext'd (LBA)
/dev/sda5       165728256   234438655    34355200    7  HPFS/NTFS

Disk /dev/sdb: 8061 MB, 8061451776 bytes
255 heads, 63 sectors/track, 980 cylinders, total 15745023 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000c57f1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    15743699     7871818+   c  W95 FAT32 (LBA)
```

/dev/sda is my hard drive, and /dev/sdb is my flash drive.

Can't seem to find my device.map any more...

Anything else you guys would want to help debug? Thanks in advance.

---

### Post by upchucky on 2008-12-22
get advanced supergrub to fix mbr, and knoppix in case you need to edit files using its live cd tools.
knoppix also has tools to fix partitions and broken windows

---

### Post by ajblogger on 2008-12-22
Thank you upchucky. Super Grub Disk let me try and boot Windows without Grub, and I got the message that "BOOTMGR Not Found. Press Ctrl+Alt+Del to Restart." So I had trashed Vista's MBR. Now, this is one of Vista's real unexpected quirks: You can boot off of the Vista Anytime Upgrade disc. So I did a couple times, selecting "Repair My Computer..." every time. The first boot it trashed grub, the second it fixed Vista. I'm back how I want my computer, with an Ubuntu flash drive and Vista on my hard drive. I now have a SuperGrubDisk too...

Super Grub Disc can be found at [http://www.supergrubdisk.org/]("http://www.supergrubdisk.org/").

Vista Anytime Upgrade discs are shipped with OEM Vista laptops and Desktops. They are mostly generic, so ask your friend to lend you theirs if you can't find yours.

---

