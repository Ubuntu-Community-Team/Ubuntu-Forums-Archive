---
title: "mounting 3rd drive, ntfs"
date: 2006-02-14
forum: Hardware &amp; Laptops
---

### Post by wade_d on 2006-02-14
I'm trying to mount a ntfs partition from my 3rd hard drive but I get the error:
```

sudo mount /dev/hdd2 /media/hdd2
mount: /dev/hdd2 already mounted or /media/hdd2 busy

```
I've tried mounting it in various places without success.  The error is also  the same for sudo mount -a

sudo mount produces:
```

/dev/hda2 on / type reiserfs (rw)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
usbfs on /proc/bus/usb type usbfs (rw)
/dev/hda3 on /boot type ext3 (rw)
/dev/hdb5 on /home type reiserfs (rw)
/dev/hda1 on /media/hda1 type ntfs (rw,nls=utf8,umask=0222)
/dev/hda6 on /tmp type reiserfs (rw)
/dev/hda7 on /var type reiserfs (rw)
tmpfs on /dev type tmpfs (rw,size=10M,mode=0755)

```

So I try to umount it and get 
```
sudo umount /dev/hdd2
umount: /dev/hdd2: not mounted
```

I am able to mount /dev/hda1 which is also ntfs, but I don't really want it mounted.  I only did it to see if I could.  
Here is my sudo fdisk -l
```
Disk /dev/hda: 41.1 GB, 41174138880 bytes
255 heads, 63 sectors/track, 5005 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1959    15735636    7  HPFS/NTFS
/dev/hda2            1960        3418    11719417+  83  Linux
/dev/hda3            3419        3424       48195   83  Linux
/dev/hda4            3425        4458     8305605    5  Extended
/dev/hda5            3425        3485      489951   82  Linux swap / 
Solaris
/dev/hda6            3486        4093     4883728+  83  Linux
/dev/hda7            4094        4458     2931831   83  Linux

Disk /dev/hdb: 160.0 GB, 160041885696 bytes
240 heads, 63 sectors/track, 20673 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1         129      975208+   b  W95 FAT32
/dev/hdb2             130         258      975240   82  Linux swap / 
Solaris
/dev/hdb3             259       10592    78125040    5  Extended
/dev/hdb5             259       10592    78125008+  83  Linux

Disk /dev/hdd: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1          65      522081    6  FAT16
/dev/hdd2              66       14593   116696160    7  HPFS/NTFS

```

Here is my /etc/fstab
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               reiserfs defaults        0       1
/dev/hda3       /boot           ext3    defaults        0       2
/dev/hdb5       /home           reiserfs defaults        0       2
/dev/hda1       /media/hda1     ntfs  nls=utf8,umask=0222 0       0
/dev/hdd2       /media/hdd2     ntfs  nls=utf8,umask=0222 0       0
/dev/hda6       /tmp            reiserfs defaults        0       2
/dev/hda7       /var            reiserfs defaults        0       2
/dev/hda5       none            swap    sw              0       0
/dev/hdb2       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```


The partition does work in Windows 2000.  It is set up as slave to a NEC ND-354A DVD burner.  I hope that someone can help me or at least point out any typos I am doing wrong.  Thanks for any help.

---

### Post by taurus on 2006-02-14
What does "df -h" say then???

If you don't see your /dev/hdd2 on that list, try something like

sudo mkdir /media/hdd2
sudo mount -t ntfs /dev/hdd2 /media/hdd2
df -h

---

### Post by wade_d on 2006-02-14
df -h
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/hda2              12G  2.1G  9.1G  19% /
tmpfs                 253M     0  253M   0% /dev/shm
/dev/hda3              45M   27M   15M  65% /boot
/dev/hdb5              75G  1.5G   74G   2% /home
/dev/hda1              16G  5.7G  9.4G  38% /media/hda1
/dev/hda6             4.7G   34M  4.7G   1% /tmp
/dev/hda7             2.8G  315M  2.5G  11% /var
/dev/hdc              2.9G  2.9G     0 100% /media/cdrom0

```

```

sudo mount -t ntfs /dev/hdd2 /media/hdd2
mount: /dev/hdd2 already mounted or /media/hdd2 busy
```

It still does not work. :(

---

### Post by slaging on 2006-02-14
I've been trying to do the same thing.
The only why i'm able to mount a 3rd ntfs drive is through the System -> Administration -> Disk menu, but it's read-only for root user:( 
If you have any luck, please post.

---

### Post by myha on 2006-02-15
You cannot mount it manually because it looks like it has already been automounted...
You can try to comment the /dev/hdd2 in /etc/fstab , so it doesn't automount...
Then reboot.

And try to execute 
sudo mount -t ntfs /dev/hdd2 /media/hdd2

br, M

---

### Post by schdefan on 2006-02-15
what does the output of 
> $cat /proc/partitions 
say?

schdefan

---

### Post by slaging on 2006-02-15
Myha, do you mean somthing like,
> /dev/...  /media/...  ntfs  rw,user,noauto  0  0
 in /etc/fstab?

---

### Post by schdefan on 2006-02-15
E.g.
```
$ cat /proc/partitions
major minor  #blocks  name

   3     0   19535040 hda
   3     1    5116671 hda1
   3     2          1 hda2
   3     3    3791340 hda3
   3     4     377527 hda4
   3     5    8803588 hda5

```
I mean can post the output. To see if hdd2 is recognized

---

### Post by myha on 2006-02-15
[QUOTE=slaging]Myha, do you mean somthing like,

 in /etc/fstab?[/QUOTE]
Yes, try to comment (add # in the beginning) the line with /dev/hdd2 in /etc/fstab.
Then reboot, so the partition won't be automounted and try to mount it manually.

---

