---
title: "Cant mount my drive"
date: 2009-12-15
forum: Hardware
---

### Post by Atlus117 on 2009-12-15
When i try to mount my drive which is called Slave it give's me this. "cannot mount volume. Your are not privileged to mount the volume 'Slave'"

I've tried just about everything that other forums say do and cant get it to work. What happend was windows gave me the blue screen of death, and i couldn't start windows so thank god i had Ubuntu. But now i cant get to my other drive. I really need the stuff i have on my slave it has all of my bands songs on it. 

This could help when i type in fdisk -l i get 

mount: can't find /slave in /etc/fstab or /etc/mtab
atlus@atlus-desktop:~$ sudo fdisk -l
[sudo] password for atlus: 

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8fd7a7f7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *           1       38914   312569794    f  W95 Ext'd (LBA)
/dev/sda5            3825       38914   281847808    7  HPFS/NTFS
/dev/sda6               1        3824    30716217   83  Linux

Partition table entries are not in disk order

---

### Post by asqn34 on 2009-12-17
Hi Atlus,
had the same probleme with external hdd.
I edited my fstab using sudo, to point it in the right direction.
Concerning the dual booting, i edited grub.


[http://ubuntuguide.org/wiki/Dapper#Windows](http://ubuntuguide.org/wiki/Dapper#Windows)


Hope it help..

---

### Post by Atlus117 on 2009-12-19
I have no clue what i need to change in the fstab.

---

