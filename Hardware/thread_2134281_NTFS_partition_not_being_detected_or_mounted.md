---
title: "NTFS partition not being detected or mounted"
date: 2013-04-10
forum: Hardware
---

### Post by isaac12345 on 2013-04-10
Hi all,

I recently had a problem on my terabyte hard disk which resulted in a resistor coming off the PCB. I soldered it back on and now it works fine,except for that it doesnt show up one of the partitions in Ubuntu. It is an NTFS partition of 886.50GB. It works fine in Windows 7 but doesnt show up in ubuntu. Storage Device Manager(psydm) cant seem to detect it, although it can detect the other partitions on the hard disk. Gparted on the other hand seems to, but as unmounted. Gigolo shows it too but nothing happens when I click on 'Open' or 'Connect' for that partition. I am quite new to Ubuntu and cant quite figure out which settings I should look at. Any help would be much appreciated. I am running Ubuntu 12.04 32-bit

Thanks!

---

### Post by Derxst on 2013-04-10
Is the drive BitLocker encrypted (or any other encryption, for that matter) in Windows 7?

---

### Post by Bashing-om on 2013-04-11
isaac12345; Hi !

Does the terminal command:
```
 sudo fdisk -l
``` show that mystery partition ?[INDENT=3]
we be look'n

[/INDENT]

---

### Post by isaac12345 on 2013-04-11
@Derxst - I run Windows 7 Professional which doesnt come with BitLocker so its not encrypted by it. Also I dont remember encrypting the drive unless it was automatically encrypted by some program! 
@Bashing-om -  Yes. Its sda1. Here's the output of that command, in red -

[COLOR=#ff0000]Disk /dev/sda: 1000.2 GB, 1000203804160 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953523055 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4e86b563

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63  1859120114   929560026    7  HPFS/NTFS/exFAT
/dev/sda2      1859121152  1890576383    15727616    7  HPFS/NTFS/exFAT
/dev/sda3   *  1890577395  1953520064    31471335    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 320.1 GB, 320071851520 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625140335 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xdd674f75

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb2   *        2046   625137344   312567649+   f  W95 Ext'd (LBA)
/dev/sdb5        50974308   501533234   225279463+   7  HPFS/NTFS/exFAT
/dev/sdb6       501533298   595474431    46970567    7  HPFS/NTFS/exFAT
/dev/sdb7            2048      503807      250880   83  Linux
/dev/sdb8          505856     4409343     1951744   82  Linux swap / Solaris
/dev/sdb9        27848704    50972671    11561984   83  Linux
/dev/sdb10       19453952    27840511     4193280   82  Linux swap / Solaris
/dev/sdb11        4411392    19439615     7514112   83  Linux
/dev/sdb12      595476480   625135615    14829568   83  Linux

Partition table entries are not in disk order

[/COLOR]

---

### Post by Bashing-om on 2013-04-11
isaac12345; Morning to ya

If all that you have on that big drive is the 3 partitions, then I see nothing wrong. 
info: If those partitions are not setup in /etc/fstab to "automount" then those partitions are not mounted, thus not seen -> until clicked on in the file manager; which will mount the respective partition.

When you click on a partition in the file manager do you have access to the files ?[INDENT=2]
just try'n to help

[/INDENT]

---

### Post by isaac12345 on 2013-04-11
The problem is that unlike before, the sda1 is not even showing up on the file manager or the storage device manager(which helps me set it to automount). I have attached two screenshots for your convenience.

---

### Post by isaac12345 on 2013-04-14
*bump*

---

### Post by Mark Phelps on 2013-04-14
In my experience, when Gparted shows an NTFS partition but won't mount it, that's often due to some kind of file system  corruption or simply the "dirty bit" being ON.  You can try to address this by running a disk check in win7.

---

### Post by isaac12345 on 2013-04-26
I ran checkdisk on that partition in windows 7 and it didnt find any errors. Any other suggestions?

---

### Post by prodigy_ on 2013-04-26
Open terminal and type ```
sudo mount -t ntfs /dev/sda1 /mnt
``` 

If that works, you can [edit /etc/fstab](https://help.ubuntu.com/community/MountingWindowsPartitions#Configuring_.2BAC8-etc.2BAC8-fstab) to mount the partition at boot time.

---

