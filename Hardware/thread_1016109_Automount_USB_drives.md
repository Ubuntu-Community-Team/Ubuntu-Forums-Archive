---
title: "Automount USB drives?"
date: 2008-12-19
forum: Hardware
---

### Post by rhcm123 on 2008-12-19
I have a usb drive that I am sharing with samba. I have found that it only auto mounts if i login graphically on the server. (HAL takes over and mounts it). 

I administer that server via ssh, and it is very annoying to have to go over and login to get that drive mounted. (and unsecure!). How do i mount it /etc/fstab?

---

### Post by taurus on 2008-12-19
What filesystem is it and where do you want to mount it to?

```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
```

---

### Post by rhcm123 on 2008-12-21
> **taurus said:**
> What filesystem is it and where do you want to mount it to?

```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
```

It's ext3 and I want to mount it to /media/BACKUP

The output you asked for:
```

ussr@USSR-VLADIVOSTOK:~$ sudo fdisk -l
[sudo] password for ussr: 

Disk /dev/sda: 20.0 GB, 20003880960 bytes
255 heads, 63 sectors/track, 2432 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0004d416

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2310    18555043+  83  Linux
/dev/sda2            2311        2432      979965   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f9c798a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9729    78148161    7  HPFS/NTFS


ussr@USSR-VLADIVOSTOK:~$ sudo blkid
/dev/sda1: UUID="b2b9ebdd-2be7-4248-8120-5eaa96cfd115" TYPE="ext3" 
/dev/sda2: TYPE="swap" UUID="6169933a-d11c-4b43-bf83-0960f32daffa" 
/dev/sdb1: UUID="666A2E5C1612E9EC" LABEL="BACKUP" TYPE="ntfs" 


ussr@USSR-VLADIVOSTOK:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=b2b9ebdd-2be7-4248-8120-5eaa96cfd115 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=6169933a-d11c-4b43-bf83-0960f32daffa none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
//192.168.2.193/share /media/remote smbfs username=ussr,password=(I'M NOT STUPID ENOUGH TO SHOW THIS!) :),auto,user,rw 0 0


ussr@USSR-VLADIVOSTOK:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              18G  2.4G   15G  15% /
varrun                220M  292K  219M   1% /var/run
varlock               220M     0  220M   0% /var/lock
udev                  220M   48K  220M   1% /dev
devshm                220M   44K  220M   1% /dev/shm
gvfs-fuse-daemon       18G  2.4G   15G  15% /home/ussr/.gvfs
/dev/sdb1              75G   67M   75G   1% /media/BACKUP
//192.168.2.193/share
                      232G   62G  159G  28% /media/remote


```

---

