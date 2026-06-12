---
title: "Run out of space on /dev/sda1 Linux partition"
date: 2008-09-29
forum: General Help
---

### Post by stevemarkus on 2008-09-29
Hi. I am running Hardy Heron Ubuntu and have been very happy with it until this morning, when I experienced problems trying to compact folders in Thunderbird. I managed to track this down to a lack of disk space, but don't know why this should have happened - I'm not doing anything particularly disk intensive. Is there some way I can reallocate space so regain some free space and get things working again ? I have posted below the output of df. Any help would be very gratefully received - I am a bit of a Ubuntu novice !! Thanks, Steve.

steve@steve-fujitsu:~$ sudo fdisk -l
[sudo] password for steve: 

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9c7087d3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14219   114214086   83  Linux
/dev/sda2           14220       14593     3004155    5  Extended
/dev/sda5           14220       14593     3004123+  82  Linux swap / Solaris

Disk /dev/sdb: 1060 MB, 1060896768 bytes
2 heads, 63 sectors/track, 16444 cylinders
Units = cylinders of 126 * 512 = 64512 bytes
Disk identifier: 0x006065ea

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       16445     1036016    6  FAT16
steve@steve-fujitsu:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1            112420772 106666468     43600 100% /
varrun                  513020       104    512916   1% /var/run
varlock                 513020         0    513020   0% /var/lock
udev                    513020        52    512968   1% /dev
devshm                  513020        12    513008   1% /dev/shm
overflow                  1024       584       440  58% /tmp
/dev/sdb1              1035744    815040    220704  79% /media/disk
steve@steve-fujitsu:~$

---

### Post by kpkeerthi on 2008-09-29
See [http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html](http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html)

---

### Post by kpkeerthi on 2008-09-29
If you see multiple kernel entries in your GRUB menu, note down the kernel version you are happy with (usually the latest one) and uninstall the rest. See [http://ubuntuforums.org/showpost.php?p=5112848&postcount=3](http://ubuntuforums.org/showpost.php?p=5112848&postcount=3) for instructions.

---

### Post by stevemarkus on 2008-09-29
> **kpkeerthi said:**
> If you see multiple kernel entries in your GRUB menu, note down the kernel version you are happy with (usually the latest one) and uninstall the rest. See [http://ubuntuforums.org/showpost.php?p=5112848&postcount=3](http://ubuntuforums.org/showpost.php?p=5112848&postcount=3) for instructions.


Many thanks for your suggestions. I've found the cause of the problem - I had somehow turned on the backup function which had completely filled my disk with the /var/backup directory and a lot of backup files. 

Thanks again !
Steve.

---

### Post by kpkeerthi on 2008-09-29
It helps to keep backups in a separate partition and not combine with / (root).

---

