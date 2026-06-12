---
title: "i cant install grub loader using live cd after re installing xp"
date: 2009-04-03
forum: Installation &amp; Upgrades
---

### Post by xihad76 on 2009-04-03
while trying to install grub loader according to the instruction stated in that [post]("http://ubuntuforums.org/showthread.php?t=224351") i found the following messages:

grub> root (hd0,5)
grub> setup (hd0)
Checking if "/boot/grub/stage1" exists... yes
Checking if "/boot/grub/stage2" exists... yes
Checking if "/boot/grub/e2fs_stage1_5" exists... yes
Running "embed /boot/grub/e2fs_stage1_5 (hd0)"... 16 sectors are embedded.
succeeded
Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,5)/boot/grub/stage2
/boot/grub/menu.lst"... failed
Error 12: Invalid device requested


# here are the outputs of the commands suggested by  [meierfra]("http://ubuntuforums.org/member.php?u=552151").   

ubuntu@ubuntu:~$ sudo fdisk -lu
omitting empty partition (5)

Disk /dev/sda: 40.0 GB, 40019582464 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78163247 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xab3fab3f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    14329979     7164958+   7  HPFS/NTFS
/dev/sda2        14329980    78140159    31905090    f  W95 Ext'd (LBA)
/dev/sda3        28660023    45046259     8193118+   b  W95 FAT32
/dev/sda5        14330106    25655804     5662849+  83  Linux
/dev/sda6        25655868    28659959     1502046   82  Linux swap / Solaris
/dev/sda7        45046323    61432559     8193118+   b  W95 FAT32
/dev/sda8        61432623    78140159     8353768+   b  W95 FAT32

ubuntu@ubuntu:~$ sudo sfdisk -d
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 14329917, Id= 7, bootable
/dev/sda2 : start= 14329980, size= 63810180, Id= f
/dev/sda3 : start= 28660023, size= 16386237, Id= b
/dev/sda4 : start=        0, size=        0, Id= 0
/dev/sda5 : start= 14330106, size= 11325699, Id=83
/dev/sda6 : start= 25655868, size=  3004092, Id=82
/dev/sda7 : start= 45046323, size= 16386237, Id= b
/dev/sda8 : start= 61432623, size= 16707537, Id= b


plz help me.. looking forward to hear from u..

---

### Post by Rocket2DMn on 2009-04-03
Moved to Installation & Upgrades - please don't post support questions in Tutorials & Tips.  Threads there require staff approval and are for Guides and HowTos only.  Thanks and good luck.

---

### Post by meierfra. on 2009-04-03
The OP already had realized  the mistake and started a new thread:

[http://ubuntuforums.org/showthread.php?t=1114935](http://ubuntuforums.org/showthread.php?t=1114935)

---

