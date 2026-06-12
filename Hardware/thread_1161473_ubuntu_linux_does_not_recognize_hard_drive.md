---
title: "ubuntu linux does not recognize hard drive"
date: 2009-05-16
forum: Hardware
---

### Post by gemone on 2009-05-16
Hello,
I am having issues with Ubuntu recognizing my other hdd. I can access the master and external but not the slave. Any ideas?

Thanks

---

### Post by taurus on 2009-05-16
Open a terminal and post the outputs of these commands, running one line at a time.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
```

---

### Post by gemone on 2009-05-16
Thanks.
I tried the commands and they identified the other hdd. But it is still not popping in places.This is the response I am receiving from the command:

Disk /dev/sda: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x88028802

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4499    36138186    7  HPFS/NTFS

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x88888888

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001    7  HPFS/NTFS

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5b6ac646

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       30401   244196001    c  W95 FAT32 (LBA)
mike@ubuntu:~$ sudo blkid
/dev/loop0: UUID="c2161976-a109-44a1-8427-4b39120a350f" TYPE="ext3" 
/dev/sda1: UUID="5A38126D38124881" TYPE="ntfs" 
/dev/sdb1: UUID="28983E3D983E09B8" LABEL="New Volume" TYPE="ntfs" 
/dev/sdc1: LABEL="WD Passport" UUID="4B1A-02BD" TYPE="vfat" 
mike@ubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext3    loop,errors=remount-ro 0       1
/host/ubuntu/disks/boot /boot           none    bind            0       0
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
mike@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/host/ubuntu/disks/root.disk
                       13G  5.8G  6.5G  47% /
tmpfs                 994M     0  994M   0% /lib/init/rw
varrun                994M  120K  994M   1% /var/run
varlock               994M     0  994M   0% /var/lock
udev                  994M  164K  994M   1% /dev
tmpfs                 994M  144K  994M   1% /dev/shm
/dev/sdb1             932G  567G  366G  61% /host
lrm                   994M  2.7M  991M   1% /lib/modules/2.6.28-11-generic/volatile
/dev/sdc1             233G  216G   18G  93% /media/WD Passport
/dev/sda1              35G   24G   11G  69% /media/disk

---

### Post by gemone on 2009-05-22
I am still having a issue. Any suggestions?

Thanks

---

