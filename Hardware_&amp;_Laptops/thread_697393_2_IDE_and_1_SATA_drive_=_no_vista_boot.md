---
title: "2 IDE and 1 SATA drive = no vista boot"
date: 2008-02-15
forum: Hardware &amp; Laptops
---

### Post by imdeemvp on 2008-02-15
Hello there.....

I have 3 hard drives: 2 ide and 1 sata drive: 1= ubuntu (ide primary 2= xp (slave)  3= vista (SATA)

my fdisk -l:

**Disk /dev/hda: 160.0 GB**, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0fa860c

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       18700   150207718+  83  Linux
/dev/hda2           18701       19457     6080602+   f  W95 Ext'd (LBA)
/dev/hda5           18701       19457     6080571   82  Linux swap / Solaris

**Disk /dev/hdb: 300.0 GB**, 300090728448 bytes
240 heads, 63 sectors/track, 38764 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0xb4d18d95

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       38745   292912168+   7  HPFS/NTFS
/dev/hdb2           38746       38764      143640    7  HPFS/NTFS

**Disk /dev/sda: 500.1 GB**, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd5de4cee

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60802   488384512    7  HPFS/NTFS
/dev/sda4   *           1           1           0    0  Empty
Partition 4 does not end on cylinder boundary.
power2liv@power2liv-pc:~$ 

my grub


title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=23447548-e6de-437a-8866-d9450a6acee3 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
title		Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

[B][COLOR="Red"]
#on /dev/sda1
title WINDOWS VISTA ULTIMATE
root              (hd2,0)
map              (hd2) (hd0)
map              (hd0) (hd2)
makeactive
chainloader +1:[/COLOR][/B]

CAN someone here help me set it up correctly.....tia:popcorn:

---

### Post by klytu on 2008-02-15
> **imdeemvp said:**
> Hello there.....

I have 3 hard drives: 2 ide and 1 sata drive: 1= ubuntu (ide primary 2= xp (slave)  3= vista (SATA)

my fdisk -l:

**Disk /dev/hda: 160.0 GB**, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0fa860c

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       18700   150207718+  83  Linux
/dev/hda2           18701       19457     6080602+   f  W95 Ext'd (LBA)
/dev/hda5           18701       19457     6080571   82  Linux swap / Solaris

**Disk /dev/hdb: 300.0 GB**, 300090728448 bytes
240 heads, 63 sectors/track, 38764 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0xb4d18d95

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       38745   292912168+   7  HPFS/NTFS
/dev/hdb2           38746       38764      143640    7  HPFS/NTFS

**Disk /dev/sda: 500.1 GB**, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd5de4cee

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60802   488384512    7  HPFS/NTFS
/dev/sda4   *           1           1           0    0  Empty
Partition 4 does not end on cylinder boundary.
power2liv@power2liv-pc:~$ 

my grub


title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=23447548-e6de-437a-8866-d9450a6acee3 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
title		Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

[B][COLOR="Red"]
#on /dev/sda1
title WINDOWS VISTA ULTIMATE
root              (hd2,0)
map              (hd2) (hd0)
map              (hd0) (hd2)
makeactive
chainloader +1:[/COLOR][/B]

CAN someone here help me set it up correctly.....tia:popcorn:

What happens if you disconnect the two IDE drives and try to boot from the Vista drive all by itself? Does it boot?

---

