---
title: "How to enable new sata hard drive?"
date: 2008-03-07
forum: Hardware &amp; Laptops
---

### Post by shankariyer on 2008-03-07
My mother boad ( ASUS M2N SLI ) supports SATA drive and so I've a combo
of IDE and SATA drives.

SATA came last, so grub and windoze/linux installation in on IDE. I don't have any booting problems detailed in other posts.

After I connected my SATA drive, I logged on to windows and using disk-managment, I formatted the drive to NTFS. That's ok to start with.

PATA #1( 320gb ) + #2( 120gb ) + SATA #3( 750gb ) is what I'm trying to achieve. Now, when I log on to Ubuntu, I see that it not mounted.

> 
~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda10             19G   12G  6.1G  66% /
varrun                2.0G  128K  2.0G   1% /var/run
varlock               2.0G     0  2.0G   0% /var/lock
udev                  2.0G  132K  2.0G   1% /dev
devshm                2.0G   16K  2.0G   1% /dev/shm
lrm                   2.0G   38M  1.9G   2% /lib/modules/2.6.22-14-generic/volatile
/dev/hda11             19G  5.6G   13G  32% /app
/dev/hda12             19G  9.3G  8.7G  52% /db
/dev/hda1              41G   24G   17G  58% /media/hda1
/dev/hda5              41G  4.8G   36G  12% /media/hda5
/dev/hda6              41G   20G   21G  48% /media/hda6
/dev/hda7              41G  1.8G   39G   5% /media/hda7
/dev/hda8              21G   20G  455M  98% /media/hda8
/dev/hda9              21G   17G  3.2G  85% /media/hda9
/dev/hdb5             112G   81G   32G  73% /media/hdb5
/dev/hda14             21G   14G  6.1G  70% /utl
/dev/hda13             19G   15G  3.7G  80% /web
Is this just a case of mounting the drive or should I do some magic here, all not affecting Ubuntu/Grub and Windoze ?

> 
~$ sudo fdisk -l

Disk /dev/sda: 750.1 GB, 750156374016 bytes
16 heads, 63 sectors/track, 1453521 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x7fef2bee

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1     1453521   732574552+  42  SFS

Disk /dev/hda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x208c208b

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        5222    41945683+   7  HPFS/NTFS
/dev/hda2            5223       38913   270622957+   f  W95 Ext'd (LBA)
/dev/hda5            5223       10444    41945683+   7  HPFS/NTFS
/dev/hda6           10445       15666    41945683+   7  HPFS/NTFS
/dev/hda7           15667       20888    41945683+   7  HPFS/NTFS
/dev/hda8           20889       23499    20972826    7  HPFS/NTFS
/dev/hda9           23500       26110    20972826    7  HPFS/NTFS
/dev/hda10          26111       28600    20000893+  83  Linux
/dev/hda11          28601       31090    20000893+  83  Linux
/dev/hda12          31091       33580    20000893+  83  Linux
/dev/hda13          33581       36070    20000893+  83  Linux
/dev/hda14          36071       38822    22105408+  83  Linux
/dev/hda15          38823       38913      730926   82  Linux swap / Solaris

Disk /dev/hdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x68a06a33

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           2       14593   117210240    f  W95 Ext'd (LBA)
/dev/hdb5               2       14593   117210208+   7  HPFS/NTFS
Thanks.

---

### Post by Rocket2DMn on 2008-03-08
You should be able to mount it normally, and would probably want to add it to /etc/fstab
The only problem is that it shows the file system as SFS.  I don't even know what that is, but it certainly doesn't look like NTFS.
If you haven't loaded any data onto the disk, I would try formatting again, either from windows or using GParted.  You can use GParted from the LiveCD, the GParted LiveCD, or you can download it from the repos and use it on the disk.  You can't fiddle with drives that are mounted (so if you ever had to screw with your root partition, you'd have to use one of the LiveCDs), but for this case you should be able to use GParted without a LiveCD.
```
sudo apt-get install gparted
```
System->Administration->Partition Editor

---

### Post by shankariyer on 2008-03-08
I have gparted installed already and I checked the layout. While it reads it as 'ntfs', it says "unable to read the contents of the file-system. Because of this, some operations may be unavailablel".

Previously, I had formatted using 'disk management' from windows. While I can format using gParted, would there be any issues, if I try to access that partition from windoze, as the option to format this as 'ntfs' ( from gparted ) is disabled?

Thanks.

---

### Post by Rocket2DMn on 2008-03-08
Hrmm, you should be able to format from GParted with ntfs if you have ntfs-3g installed with write enabled (see ntfs-config).  If that doesn't work, I would try again from windows, maybe doing it from a DOS cmd prompt, something like:
```
format g: /FS:NTFS
```

edit: where "g:" is the appropriate drive letter, of course.

---

### Post by shankariyer on 2008-03-08
I've progressed a bit. Windows had loaded this SATA drive as 'Dynamic Disk'. Upon research, I found that this is a dirty trick of Microshaft. Suspecting Partition Magic, I had a chat conversation with Symantec. That proved to be a disaster, as Symantec's tech support was clueless, even when they had a remote-desktop trouble-shooting session.

Anyways... then found this [link]("http://support.microsoft.com/kb/309044"), which helped me to use Disk Management to convert the disk as a 'Basic Disk'. Now am planning to format it further using Partition Magic or GParted and hope Ubuntu is able to mount them auto.

---

### Post by Rocket2DMn on 2008-03-08
Cool.  Once you get it formatted correctly, post back and we'll get it to mount automatically by putting an fstab entry for it.  Just include the output of the commands
```
sudo fdisk -l
cat /etc/fstab
```

If you want to try it yourself first, have a look here - [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131) - otherwise, I'll walk you through it.

---

