---
title: "Grub nt Detecting Windows 7"
date: 2009-08-02
forum: Installation &amp; Upgrades
---

### Post by ajithboygenius on 2009-08-02
Hi .. i have installed windows 7 lately & sday i got the ubuntu 9.04 .. so installed it

Now at the grub only ubuntu is visible .. cant find Windows

I have two HDD one of them has Linux (80 GB -Disk /dev/sda: 80.0 GB, 80026361856 bytes ) and the Other HDD has Windows 7 (160 GB -Disk /dev/sdb: 160.0 GB, 160041885696 bytes)

Even if i change the boot priority in BIOS for HDD 0 then .. it boots grub to load ubuntu bt changing the priority back to HDD 1 ... am getttin a grub error 17 ....

My Fdisk - l output is 

===========================================================

[html]
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x22c5426d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1459    11717968+  83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2            1460        2918    11719417+   c  W95 FAT32 (LBA)
Partition 2 does not end on cylinder boundary.
/dev/sda3            2919        9727    54693292+   f  W95 Ext'd (LBA)
Partition 3 does not end on cylinder boundary.
/dev/sda5            2919        4448    12289693+   7  HPFS/NTFS
/dev/sda6            4449        6998    20482843+   7  HPFS/NTFS
/dev/sda7            6999        8910    15358108+   7  HPFS/NTFS
/dev/sda8            8911        9003      746991    b  W95 FAT32
/dev/sda9            9004        9727     5815498+   b  W95 FAT32

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5fa6f80a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3916    31455238+   c  W95 FAT32 (LBA)
/dev/sdb2   *        3917        7740    30716280    c  W95 FAT32 (LBA)
/dev/sdb3            7741       19457    94116802+   f  W95 Ext'd (LBA)
/dev/sdb5            7741        9698    15727603+   b  W95 FAT32
/dev/sdb6            9699       13614    31455238+   b  W95 FAT32
/dev/sdb7           13615       16225    20972826    b  W95 FAT32
/dev/sdb8           16226       19293    24641536    7  HPFS/NTFS
/dev/sdb9           19294       19457     1317298+  82  Linux swap / Solaris
[/html]==============================================================

My **windows 7** is in ---- sdb
**The swap** is in    -------- sdb 
**Linux **is in   --------------  sda

Am unable to understand what excatly to add at the*** /boot/grub/menu.list*** :confused:


here is my output of menu.lust
[html]


title        Ubuntu 9.04, kernel 2.6.28-14-generic
uuid        a2a0c5aa-da02-4ba4-8231-71dd38b4f2b8
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=a2a0c5aa-da02-4ba4-8231-71dd38b4f2b8 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-14-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid        a2a0c5aa-da02-4ba4-8231-71dd38b4f2b8
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=a2a0c5aa-da02-4ba4-8231-71dd38b4f2b8 ro  single
initrd        /boot/initrd.img-2.6.28-14-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        a2a0c5aa-da02-4ba4-8231-71dd38b4f2b8
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=a2a0c5aa-da02-4ba4-8231-71dd38b4f2b8 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        a2a0c5aa-da02-4ba4-8231-71dd38b4f2b8
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=a2a0c5aa-da02-4ba4-8231-71dd38b4f2b8 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        a2a0c5aa-da02-4ba4-8231-71dd38b4f2b8
kernel        /boot/memtest86+.bin
quiet
[/html]

Can u please help me out soon ..... :( :(

---

