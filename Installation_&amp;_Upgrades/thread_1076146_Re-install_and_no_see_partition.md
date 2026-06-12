---
title: "Re-install and no see partition"
date: 2009-02-21
forum: Installation &amp; Upgrades
---

### Post by Shingerzu on 2009-02-21
I installed ubuntu. Now, i re-install it. But in step "partition" -> My hdd is empty, don't see any partition.
I see same thread there [http://ubuntuforums.org/showthread.php?p=6620587](http://ubuntuforums.org/showthread.php?p=6620587)
But i don't know how to correct my problem.

----------------------------------------
ubuntu@ubuntu:~$ sudo fdisk -lu
omitting empty partition (5)

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xfc7efc7e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    87232949    43616443+   7  HPFS/NTFS
/dev/sda2        87234560   148674559    30720000    7  HPFS/NTFS
/dev/sda3       148681636   488394751   169856558    f  W95 Ext'd (LBA)
/dev/sda4       169156608   230596607    30720000    7  HPFS/NTFS
/dev/sda5       148681638   169148384    10233373+  83  Linux
/dev/sda6       230598656   314566655    41984000    7  HPFS/NTFS
/dev/sda7       314568704   488394751    86913024    7  HPFS/NTFS

--------------------------------------------
ubuntu@ubuntu:~$ sudo sfdisk -d
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 87232887, Id= 7, bootable
/dev/sda2 : start= 87234560, size= 61440000, Id= 7
/dev/sda3 : start=148681636, size=339713116, Id= f
/dev/sda4 : start=169156608, size= 61440000, Id= 7
/dev/sda5 : start=148681638, size= 20466747, Id=83
/dev/sda6 : start=230598656, size= 83968000, Id= 7
/dev/sda7 : start=314568704, size=173826048, Id= 7


Help me. :( Thx

---

### Post by caljohnsmith on 2009-02-21
> **Shingerzu said:**
> ```

ubuntu@ubuntu:~$ sudo fdisk -lu
[COLOR="Red"]omitting empty partition (5)[/COLOR]

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xfc7efc7e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    87232949    43616443+   7  HPFS/NTFS
/dev/sda2        87234560   148674559    30720000    7  HPFS/NTFS
[COLOR="Red"]/dev/sda3       148681636   488394751[/COLOR]   169856558    f  W95 Ext'd (LBA)
[COLOR="Red"]/dev/sda4       169156608   230596607[/COLOR]    30720000    7  HPFS/NTFS
/dev/sda5       148681638   169148384    10233373+  83  Linux
/dev/sda6       230598656   314566655    41984000    7  HPFS/NTFS
/dev/sda7       314568704   488394751    86913024    7  HPFS/NTFS

```

As shown highlighted in red above, it looks like the problem is that your sda4 primary partition is inside your sda3 extended partition; therefore sda4 should be a logical partition. In order to correct the problem, how about downloading the attached "partition_table.txt" file to your Ubuntu Live CD desktop, and then do:
```
sudo sfdisk --no-reread -f /dev/sda  < ~/Desktop/partition_table.txt
```
And please post the output. Next reboot to your Live CD, and please post the output of:
```
sudo fdisk -lu
sudo parted /dev/sda print
sudo grub
grub> root (hd0,4)
grub> setup (hd0)
grub> quit
```
And we can work from there.

---

