---
title: "Help with partitioning for a triple-boot"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by trot2millah on 2009-04-25
I currently have 4 primary partitions under the partition table /dev/sda, and I am dual-booting Windows XP and Linux Mint 6.   /dev/sda1 is ntfs and my Windows XP partition.  /dev/sda2 is FAT32 and my D: drive backup hard drive partition.  From there, I have /dev/sda3 which is my "/" partition for my Linux Mint install.  The last one I have is /dev/sda4, which is an extended partition that contains swap, /tmp, /usr, /home and /var for Linux.  This leaves me with 4 primary partitions, and I cannot create any more to go to a triple-boot setup with Jaunty.  What are my options?  Could I create a new partition table and be fine?  Or is the only way for me to run Jaunty is by using Wubi, which I had before?  Any help would be greatly appreciated.

---

### Post by trot2millah on 2009-04-25
Bump, could really use some help as I cannot go forward until I find this out.

---

### Post by Feelin_froggy8877 on 2009-04-25
Pretty sure Wubi is your only option.  Unless you wanna just repartition the whole hdd and add the 5th. Pretty sure If you try to add/repartition the hdd now it will be wiped clean.

---

### Post by trot2millah on 2009-04-25
Alright I'm just going to go through Wubi.  Thanks for the help.

---

### Post by tommcd on 2009-04-25
> **trot2millah said:**
>  The last one I have is /dev/sda4, which is an extended partition that contains swap, /tmp, /usr, /home and /var for Linux.  This leaves me with 4 primary partitions, and I cannot create any more to go to a triple-boot setup with Jaunty.
An extended partition usually contains one or more logical partitions. For example, consider my fdisk -l:
```

bash-3.1# fdisk -l
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x01680167
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551        4080    12289725   83  Linux
/dev/sda3            4081        4207     1020127+  82  Linux swap
/dev/sda4            4208       30401   210403305    5  Extended
/dev/sda5            4208        5737    12289693+  83  Linux
/dev/sda6            5738        7267    12289693+  83  Linux
/dev/sda7            7268       30401   185823823+  83  Linux
bash-3.1# 

```
Note that /dev/sda4 is an extended partition that contains 3 logical partitions. Post your "sudo fdisk -l" here. If you have logical partitions inside your extended partition you should be able to repartition those. Try a Parted Magic live CD.

---

### Post by Feelin_froggy8877 on 2009-04-26
I was unaware you you repartition extended part's without affecting the primary.

---

