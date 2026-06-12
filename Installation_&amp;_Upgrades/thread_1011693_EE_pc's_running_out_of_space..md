---
title: "EE pc's running out of space."
date: 2008-12-15
forum: Installation &amp; Upgrades
---

### Post by Cheeses on 2008-12-15
Hi.
I'm having some problems regarding the disk utilization on my EEE 1000H and my 901 with Ubuntu 8.10.

So the problem is:
The /dev/sda1 is running out of space fast. The problem in on both models.
I have tried to compress the /usr and that worked briefly. On the EEE 1000H i extended the partition storing the rootfs from 6 Gigs to 12 Gigs. The result was that the partition still god swamped with data. The second issue with the 1000H is that the df command  is only showing the /dev/sda1 as 1,7 Gigs instead of the 11 Gigs i assigned the partition.

/dev/sda1             1,7G  1,6G   63M  97% /
tmpfs                 500M     0  500M   0% /lib/init/rw
varrun                500M  104K  500M   1% /var/run
varlock               500M     0  500M   0% /var/lock
udev                  500M  2,7M  498M   1% /dev
tmpfs                 500M  116K  500M   1% /dev/shm
/dev/sda3             135G  128M  128G   1% /home
/dev/loop0            1,7G  1,6G   63M  97% /usr
unionfs               1,7G  1,6G   63M  97% /usr

an fdisk on dev/sda shows the following;
/dev/sda1   *           1        1479    11880036   83  Linux
/dev/sda2            1480        1609     1044225   82  Linux swap / Solaris
/dev/sda3            1610       19457   143364060   83  Linux

and an fdisk on the partition in question /dev/sda1 just to verify the partition size:
Disk /dev/sda1: 12.1 Gb, 12165156864 byte
255 heads, 63 sectors/track, 1478 cylinders
Units = cylindre of 16065 * 512 = 8225280 bytes
Disk identifier: 0x32ccad84

The problem is identical on my 901.

Just after i compressed the /usr dir. the partitionsize was correct, but after a few reboots of the system the error occured .

any idears on how  to fix it?

Thanks

---

### Post by Cheeses on 2008-12-15
problem solved with resize2fs /dev/sda1

---

### Post by lpanebr on 2009-06-04
Hello, i am having the same  problem. My svn server is out of space... i am not shure why since its low use..

/dev/sda1              28G   28G     0 100% /
varrun                950M  104K  950M   1% /var/run
varlock               950M     0  950M   0% /var/lock
udev                  950M   60K  950M   1% /dev
devshm                950M     0  950M   0% /dev/shm
lrm                   950M   39M  912M   5% /lib/modules/2.6.24-19-generic/volatile
/dev/sda6             194G  595M  183G   1% /cubo
/dev/sda5             4.7G  154M  4.3G   4% /home

any ideas? thanks

---

### Post by lpanebr on 2009-06-04
well..  ](*,) mea-culpa.. I had a backup cron job save files on the filesystem insted of the external drive.. no comments..

---

