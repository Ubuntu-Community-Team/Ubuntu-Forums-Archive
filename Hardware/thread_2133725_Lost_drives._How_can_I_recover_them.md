---
title: "Lost drives. How can I recover them?"
date: 2013-04-09
forum: Hardware
---

### Post by lonekingc4 on 2013-04-09
Hi,

I am in a very tough situation here (scary too). Kinda' pissed off on windows, I think I will NEVER try to install it again! I have a 1 TB hard drive with Ubuntu 12.04 (32 bit) and Zorin OS 6 (32 bit) installed. I added a second 160 GB hard drive and decided to install Windows XP on it. It installed well, ran well. The Linux grub was gone but I was able to recover it with Ubuntu 12.04 live CD. But it only recovered Zorin OS and ignored Ubuntu 12.04. Now I wanted to remove Windows XP completely and booted Zorin OS and scared the hell out of me when I saw Zorin wasn't detecting any other drive but its own file system. I unplugged the second hard drive where I have Windows XP. Still, other drives are not detected in Zorin. Luckily I managed to mount all the drives using the terminal with the "mount" command. But my Ubuntu 12.04 drive is corrupted. It says "NTFS signature missing" or something. I googled and tried several solutions, none worked. But scary part is still left...

I booted gParted live and it shows my entire hard drive as unallocated space! Also I tried to reinstall Zorin OS and it also shows my hard disk as unallocated space! But normally, the installed Zorin OS seems to run fine, also the mounted drives (with terminal) have correct data.

Now I need help in 2 cases. Firstly, I need my normal drives recovered, the ones I can mount only with the terminal. Secondly, I need my Ubuntu drive recovered, where I have some important files. The second one is more important. Probably the safest thing to do now is to copy all the data from the drives into an external hard drive and reformat the entire hard drive. It's ok with me, but I would like to avoid it. Besides, some really important files are in my seemingly corrupted Ubuntu drive (yeah, I am kicking myself for not backing them up).

Anyways, here is the output of fdisk -l:

```
sudo fdisk -l /dev/sda
omitting empty partition (5)


Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x13e92cc3


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048   102416383    51207168   83  Linux
/dev/sda2       102416384   200071167    48827392   83  Linux
/dev/sda3       200073214  1854132223   827029505    f  W95 Ext'd (LBA)
/dev/sda4   *   204796683   716804234   256003776    7  HPFS/NTFS/exFAT
/dev/sda5       200073216   204795903     2361344   82  Linux swap / Solaris
/dev/sda6       716804298  1331210159   307202931    7  HPFS/NTFS/exFAT
/dev/sda7      1331212288  1781772287   225280000    7  HPFS/NTFS/exFAT
/dev/sda8      1781774336  1850132479    34179072   83  Linux
/dev/sda9      1850134528  1854132223     1998848   82  Linux swap / Solaris

```

Thanks. Cheers.

---

