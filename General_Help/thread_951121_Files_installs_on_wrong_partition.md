---
title: "Files installs on wrong partition"
date: 2008-10-17
forum: General Help
---

### Post by friisk on 2008-10-17
Synaptic package manager installs files to the same partition as the system files. That partition gets filled up very quick.

How can I choose where to install files when using spm?

---

### Post by Slim Odds on 2008-10-17
What does your partition layout look like now?

If you only have one partition, that's where it will go.

---

### Post by friisk on 2008-10-17
I don't really know so much about these things but i think have two partitions (or 4?):

/dev/sda
[INDENT]sda1[/INDENT]
[INDENT]sda2[/INDENT]
[INDENT]sda5(swap)[/INDENT]
/dev/sdb (mounted on /media/home)

the sda has the system files and a swap partition, it's the smallest one, and where all files are installed. I'd rather the files where installed in sdb.

---

### Post by Slim Odds on 2008-10-18
What does "mount" show?

My guess is that sda1 is /
and sda2 is /home

your swap partition is sda5

/media/home is non-standard;    where did that come from?

It appears that you only real choice is to backup your data and reinstall with a better partition plan.

---

### Post by friisk on 2008-10-18
that won't be a problem, 'cause i've just recently started using ubuntu. but how should i configure the partitions? i remember i had no clue what so ever when i did it the last time, and i didn't really know what i was doing. hehe...

---

### Post by sisco311 on 2008-10-18
post the output of:
```
df -h
```

also to free up some space empty the apt cache:
```
sudo apt-get clean
```

and empty root's trash:
 
```
gksu nautilus trash://
```

---

### Post by friisk on 2008-10-18
when i did that i got:

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             3.6G  2.2G  1.2G  66% /
varrun                502M  112K  502M   1% /var/run
varlock               502M     0  502M   0% /var/lock
udev                  502M   44K  502M   1% /dev
devshm                502M   24K  502M   1% /dev/shm

I guess sdb isn't mounted? i tried to mount it (didn't really know what to type but...). anyway, this happened:

erik@Eee901:~$ $mount /dev/sdb1 /home
bash: /dev/sdb1: Permission denied

erik@Eee901:~$ mount /dev/sdb1 /home
mount: must be superuser to use mount

---

### Post by sisco311 on 2008-10-18
post:
```
sudo fdisk -l
```
```
sudo blkid
```
```
cat /etc/fstab
```
and
```
mount
```

---

### Post by friisk on 2008-10-19
erik@Eee901:~$ sudo fdisk -l
[sudo] password for erik: 

Disk /dev/sda: 4034 MB, 4034838528 bytes
255 heads, 63 sectors/track, 490 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc36ac36a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         462     3710983+  83  Linux
/dev/sda2             463         490      224910    5  Extended
/dev/sda5             463         490      224878+  82  Linux swap / Solaris

Disk /dev/sdb: 16.1 GB, 16139354112 bytes
255 heads, 63 sectors/track, 1962 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf26d47c4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1962    15759733+  83  Linux
erik@Eee901:~$ sudo blkid
/dev/sda1: UUID="259bb623-0e22-4a95-857b-f38517a3d36c" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="f60938c5-2d47-49d7-b117-9060a5fa21b2" 
/dev/sdb1: UUID="fe8086fa-5e11-48f5-b9f2-e2c2349bb7b6" TYPE="ext2" 
erik@Eee901:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=259bb623-0e22-4a95-857b-f38517a3d36c /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=f60938c5-2d47-49d7-b117-9060a5fa21b2 none            swap    sw              0       0
# /dev/sdc1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
erik@Eee901:~$ mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sdb1 on /media/disk type ext2 (rw,nosuid,nodev,uhelper=hal)
erik@Eee901:~$

---

