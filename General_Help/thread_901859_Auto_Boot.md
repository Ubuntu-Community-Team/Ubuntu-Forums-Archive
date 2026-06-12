---
title: "Auto Boot?"
date: 2008-08-26
forum: General Help
---

### Post by Wickd on 2008-08-26
Hi there I would like to do the following three things:

1) Ad Skype to the boot file so that when Ubuntu starts it automatically opens skype?

2) I have 5 workspaces. Is there any way that I can assign each workspace a set of programs to open at startup?

3) Auto mound my other partition at startup?

Is there anyone that can help

Thanks in Advance

---

### Post by aysiu on 2008-08-26
I can't help with #2, but...

#1 Go to System > Preferences > Sessions. Add a new item to the startup programs. The command should be ```
skype
```

#3 Can you paste these commands into [the terminal](http://www.psychocats.net/ubuntu/terminal) and then paste the output back here? ```
sudo fdisk -l
df -h
cat /etc/fstab
```

---

### Post by Wickd on 2008-08-27
> **aysiu said:**
> I can't help with #2, but...

#1 Go to System > Preferences > Sessions. Add a new item to the startup programs. The command should be ```
skype
```

#3 Can you paste these commands into [the terminal](http://www.psychocats.net/ubuntu/terminal) and then paste the output back here? ```
sudo fdisk -l
df -h
cat /etc/fstab
```

Hi there

Thank You with your quick response

Com #1: 255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x316f316f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         932     7486258+   c  W95 FAT32 (LBA)
/dev/sda2             933        3262    18715725   83  Linux
/dev/sda3            3263        3386      996030   82  Linux swap / Solaris
/dev/sda4            3387       30401   216997987+   b  W95 FAT32

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x870beafd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9729    78148161    7  HPFS/NTFS

Com #2: Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2              18G  4.2G   13G  25% /
varrun                497M  112K  497M   1% /var/run
varlock               497M     0  497M   0% /var/lock
udev                  497M   60K  497M   1% /dev
devshm                497M   12K  497M   1% /dev/shm
/dev/sda1             7.2G  4.7G  2.6G  65% /media/sda1
/dev/sda2              18G  4.2G   13G  25% /media/sda2
/dev/sda4             207G   72G  136G  35% /media/sda4
/dev/sdb1              75G   61G   15G  81% /media/sdb1
gvfs-fuse-daemon       18G  4.2G   13G  25% /home/ivan/.gvfs
/dev/scd0             4.0G  4.0G     0 100% /media/cdrom0

Com #3: # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                    0  0  
# /dev/sda2
UUID=e2bac77c-5345-412e-916c-ecd413648e29  /              ext3         relatime,errors=remount-ro  0  1  
# /dev/sda3
UUID=6e744cea-0361-43ec-b05d-3443b7e91971  none           swap         sw                          0  0  
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8       0  0  
/dev/sda1                                  /media/sda1    vfat         defaults                    0  0  
/dev/sda2                                  /media/sda2    ext3         defaults                    0  0  
/dev/sda4                                  /media/sda4    vfat         users                       0  0  
/dev/sda3                                  /media/sda3    swap         defaults                    0  0  
/dev/sdb1                                  /media/sdb1    ntfs         defaults                    0  0  

There You go. I hope that helps

Thank You in advance

---

### Post by aysiu on 2008-08-27
It looks as if they're all mounted. Which drive are you having problems with?

---

### Post by Wickd on 2008-08-27
Hi thanks for your help

But I managed to sort out the problem on my own. Thanks alot for your quick response to my question.

Thanks :)

---

### Post by Wickd on 2008-08-27
Hi thanks for your help

But I managed to sort out the problem on my own. Thanks alot for your quick response to my question.

Thanks :)

---

