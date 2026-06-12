---
title: "External Hard drive"
date: 2008-01-16
forum: Hardware &amp; Laptops
---

### Post by lacroixmouz on 2008-01-16
I wanted to plug in my external hard drive, but I get the following message

Unable to mount the volume 'H'.

what Should I do? I am new user

---

### Post by pavallokazzo on 2008-01-16
volume H???
seems like you are using a windows device name!!!
anyway try 
sudo fdisk -l
and check the output:

Disco /dev/sda: 80.0 GB, 80026361856 byte
255 heads, 63 sectors/track, 9729 cylinders
Units = cilindri of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc3bf4bd9

Dispositivo Boot      Start         End      Blocks   Id  System
/dev/sda1               1         243     1951866   1b  W95 FAT32 nascosto
/dev/sda2   *         244        5941    45769185    c  W95 FAT32 (LBA)
/dev/sda3            5942        9729    30427110    f  W95 Esteso (LBA)
/dev/sda5            6834        9729    23262088+   b  W95 FAT32
/dev/sda6            5942        6006      522049+  82  Linux swap / Solaris
/dev/sda7            6007        6833     6642846   83  Linux

Le voci nella tabella delle partizioni non sono nello stesso ordine del disco

that's mine in italian but you can easily spot the HD information and partition table
you got to find the PARTITION you are interested and mount it as sudo, in a given mount point (that corrispond to a directory already existing)
for ex. if you want to mount /dev/sda7 (that use ext3 filesystem) on /media/temp
mount /dev/sda7 /media/temp -t ext3

however this way you can only work there as root user but you got to avoid that so add a line in your fstab:
sudo nano /etc/fstab
/dev/sda7          /media/temp        ext3      defaults, user, noauto    0  0
of course you got to change partition name, device and fs in what you need...
this way you can easily mount the drive whenever you want with:
mount /dev/sda7
or
mount /media/temp

PS = the options I have specified should be right, maybe someone can confirm that?
PPS = in order to be able to access the device as a normal user you got to:
- give a user-ownered moint point (sudo chown user:usergroup /media/temp i.e.)
- be sure you specified user in the options list on the fstab
- work around those last 2 numbers (0,1,2) :) sorry but every filesystem wants his own

---

