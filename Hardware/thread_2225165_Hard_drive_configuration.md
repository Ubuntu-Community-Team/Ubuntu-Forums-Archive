---
title: "Hard drive configuration"
date: 2014-05-20
forum: Hardware
---

### Post by conormclaughlin on 2014-05-20
Hello,

I'm new to Ubuntu and need to upgrade a server 8.04 LTS to at least 12.04 LTS. Before doing this, I want to create an image of the disk(s) and also rsync all important files using

```
rsync -aAXv /* /path/to/backup/folder --exclude={/dev/*,/proc/*,/sys/*,/tmp/*,/run/*,/mnt/*,/media/*,/lost+found}
```

However, I'm not 100% sure how to understand the hard drive configuration below (and currently can't open the box to check). I have ran df -h and fdisk -l, the results are below.

As far as I can understand, there are two drives (500GB and 250GB). However, I can't understand how they have been logically partitioned, and more important what exactly I should back up or clone with Clonezilla.

Thanks!
Conor 

```
user1@test:~$ df -h

Filesystem            Size  Used Avail Use% Mounted on
/dev/md0               28G  6.0G   21G  23% /
varrun               1013M  1.9M 1011M   1% /var/run
varlock              1013M  4.0K 1013M   1% /var/lock
udev                 1013M   92K 1013M   1% /dev
devshm               1013M   12K 1013M   1% /dev/shm
/dev/sda5             278G  114G  150G  44% /home
/dev/md2               93G   38G   51G  43% /srv
/dev/sdb5              28G  173M   27G   1% /tmp
gvfs-fuse-daemon       28G  6.0G   21G  23% /home/user1/.gvfs


user1@test:~$ fdisk -l
user1@test:~$ sudo fdisk -l


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000365ce


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3647    29294496   fd  Linux raid autodetect
/dev/sda2            3648        4133     3903795   fd  Linux raid autodetect
/dev/sda3            4134       16291    97659135   fd  Linux raid autodetect
/dev/sda4           16292       52764   292969372+   5  Extended
/dev/sda5           16292       52764   292969341   83  Linux


Disk /dev/sdb: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        3647    29294496   fd  Linux raid autodetect
/dev/sdb2            3648        4133     3903795   fd  Linux raid autodetect
/dev/sdb3            4134       16291    97659135   fd  Linux raid autodetect
/dev/sdb4           16292       19938    29294527+   5  Extended
/dev/sdb5           16292       19938    29294496   83  Linux


Disk /dev/md0: 29.9 GB, 29997465600 bytes
2 heads, 4 sectors/track, 7323600 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000


Disk /dev/md0 doesn't contain a valid partition table


Disk /dev/md1: 3997 MB, 3997368320 bytes
2 heads, 4 sectors/track, 975920 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000


Disk /dev/md1 doesn't contain a valid partition table


Disk /dev/md2: 100.0 GB, 100002824192 bytes
2 heads, 4 sectors/track, 24414752 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000


Disk /dev/md2 doesn't contain a valid partition table
```

---

### Post by norbert23 on 2014-05-20
Please also show your /etc/fstab.
You are having a software-raid setup here. But from your output I don't yet understand what sda5 and sdb5 are good for.
they are not equal in size.

---

### Post by conormclaughlin on 2014-05-20
Thanks for your help!

```
# /etc/fstab: static file system information.#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/md0
UUID=87a0b71f-91aa-4d20-87f8-840ced6fda2b /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=61d77158-5177-482c-80bf-20bc22e350b8 /home           ext3    relatime        0       2
# /dev/md2
UUID=a46413ae-5d15-4ea2-a780-b37d8d212de5 /srv            ext3    relatime        0       2
# /dev/sdb5
UUID=e3c6b3f9-1972-48e1-a490-17eaffa12bcf /tmp            ext3    relatime        0       2
# /dev/md1
UUID=d1c60a5a-71c1-4692-87f8-a1d3327bd614 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

---

### Post by norbert23 on 2014-05-20
okay, clear now - so what exactly are you trying to do?
you wanna setup a new system or "just" upgrade?
what is your plan in case of an emergency (something goes wrong)?

if you just want to 'backup' your data start with 'home' and use rsync to an ext4 partition (so all settings stay alive).
do you have a lot of specific configuration, etc on this machine? then it will get tricky since I don't think it is easy to just copy i.e. etc and be sure all the config files, etc are on their location after the upgrade.
besides that... it requires a lot of know-how to do it.
so please tell me what your plans are and what you are trying to do...

---

