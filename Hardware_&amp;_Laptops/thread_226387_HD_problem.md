---
title: "HD problem"
date: 2006-07-31
forum: Hardware &amp; Laptops
---

### Post by Amar_ze on 2006-07-31
I bougt new HD today and it's slave( my old disk with OS on is still here). Now I have problems mounting it(can't do a thing with it). I see partitions but can't open it. I put this two lines in /etc/fstab 

/dev/hdd5       /media/hdd5     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hdd6       /media/hdd6     vfat    defaults,utf8,umask=007,gid=46 0       1

but when I try to open partition it says

Unable to mount the selected volume.
mount: only root can mount /dev/hdd6 on /media/hdd6


SO how to do this? I am pretty noob when it comes to this.Here is screenshot of partitions in attacment.And also fhen I do df -h this is output

```
root@playboy:/home/amar# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hdb7              15G  3.0G   12G  21% /
varrun                252M  104K  252M   1% /var/run
varlock               252M  4.0K  252M   1% /var/lock
udev                  252M  124K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M   19M  234M   8% /lib/modules/2.6.15-23-386/volatile
/dev/hdb8              22G  3.4G   19G  16% /home
/dev/hdb1              16G   14G  2.3G  86% /media/hdb1
/dev/hdb10            2.0G  2.0G   46M  98% /media/hdb10
/dev/hdb5              18G   17G  969M  95% /media/hdb5
/dev/hdb9             2.0G  2.0G   65M  97% /media/hdb9
root@playboy:/home/amar#


```

So only this disk with Os on it.. Please help :)

---

### Post by Ocxic on 2006-07-31
type sudo fdisk -l to list your drives and partions filesystems, edit you fstab in needed.

---

