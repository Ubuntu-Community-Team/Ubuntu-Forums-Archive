---
title: "grub loader do not open after format on windows xp"
date: 2009-04-16
forum: Installation &amp; Upgrades
---

### Post by NoktasizvirguL on 2009-04-16
I format on my Windows XP and I lost my GRUB loader I cannot enter either Ubuntu nor Windows. I read most of the forums I tried a lot of things but I cannot fix it.

The output of `sudo fdisk -lu` command

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2bbbfc8e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    14329979     7164958+   7  HPFS/NTFS
/dev/sda2        14329980    78140159    31905090    f  W95 Ext'd (LBA)
/dev/sda5        14330106    25655804     5662849+  83  Linux
/dev/sda6        25655868    28659959     1502046   82  Linux swap / Solaris
/dev/sda7        28660023    45046259     8193118+   b  W95 FAT32
/dev/sda8        45046323    61432559     8193118+   b  W95 FAT32
/dev/sda9        61432623    78140159     8353768+   b  W95 FAT32

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xfe4f892a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   488392064   244196001    c  W95 FAT32 (LBA)

```

The output of ` sudo sfdisk -d` code

```
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 14329917, Id= 7, bootable
/dev/sda2 : start= 14329980, size= 63810180, Id= f
/dev/sda3 : start=        0, size=        0, Id= 0
/dev/sda4 : start=        0, size=        0, Id= 0
/dev/sda5 : start= 14330106, size= 11325699, Id=83
/dev/sda6 : start= 25655868, size=  3004092, Id=82
/dev/sda7 : start= 28660023, size= 16386237, Id= b
/dev/sda8 : start= 45046323, size= 16386237, Id= b
/dev/sda9 : start= 61432623, size= 16707537, Id= b
# partition table of /dev/sdb
unit: sectors

/dev/sdb1 : start=       63, size=488392002, Id= c, bootable
/dev/sdb2 : start=        0, size=        0, Id= 0
/dev/sdb3 : start=        0, size=        0, Id= 0
/dev/sdb4 : start=        0, size=        0, Id= 0

```

The output of `sudo parted /dev/sda print` command

```
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      32.3kB  7337MB  7337MB  primary   ntfs         boot 
 2      7337MB  40.0GB  32.7GB  extended               lba  
 5      7337MB  13.1GB  5799MB  logical                     
 6      13.1GB  14.7GB  1538MB  logical                     
 7      14.7GB  23.1GB  8390MB  logical                     
 8      23.1GB  31.5GB  8390MB  logical                     
 9      31.5GB  40.0GB  8554MB  logical                     

Information: Don't forget to update /etc/fstab, if necessary. 
```

I am waiting your reply. I am newbie on Ubuntu. Thanks for your help.

---

### Post by ronparent on 2009-04-16
What do the boot lines in menu.lst look like?

---

### Post by MarkM06 on 2009-04-17
Hey,

This should do it.

sudo grub-install /dev/hda

or sda rather than hda

---

