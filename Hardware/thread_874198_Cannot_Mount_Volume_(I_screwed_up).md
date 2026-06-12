---
title: "Cannot Mount Volume (I screwed up)"
date: 2008-07-29
forum: Hardware
---

### Post by ZXQ on 2008-07-29
**The Error:**

The Volume 'EVA03' Uses the *NTFS* file system which is not supported by your system.

**The fdisk:**

Disk /dev/sda: 250.0 GB, 250059350016 bytes **(EVA03 IS THIS DRIVE)**
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xacd02140

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30401   244196001    7  HPFS/NTFS

Disk /dev/sdb: 203.9 GB, 203928109056 bytes 
240 heads, 63 sectors/track, 26342 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x17651764

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       26341   199137928+   7  HPFS/NTFS

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000f1ea6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       25497   204800000    7  HPFS/NTFS
/dev/sdc2           25498       38262   102534862+  83  Linux
/dev/sdc3           38263       38913     5229157+  82  Linux swap / Solaris

Disk /dev/sdd: 128 MB, 128974848 bytes
16 heads, 32 sectors/track, 492 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1         492      125936    6  FAT16

**The Reason:**

I changed the value in **'EVA03->Properties->Volume->Settings->File System'** manually to just NTFS thinking that it was just notes or something. I have another drive setup the exact same way, and it works fine. Is there a config file somewhere that i can edit to fix this? 

I really don't want to reinstall ubuntu again. :(


//edit:

Linux buddy asked for this info, so thought I'd post it here (**cat /etc/fstab**)

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc2
UUID=0d4334b8-3a53-4d7b-bb43-4b2bc36559b2 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdc3
UUID=08dbd330-02d2-4f6f-bf95-b69ec7b3860a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

//edit2:

and here is a **df -h**

Filesystem            Size  Used Avail Use% Mounted on
/dev/sdc2              98G  2.9G   90G   4% /
varrun               1013M  104K 1013M   1% /var/run
varlock              1013M     0 1013M   0% /var/lock
udev                 1013M   72K 1013M   1% /dev
devshm               1013M   48K 1013M   1% /dev/shm
lrm                  1013M   39M  975M   4% /lib/modules/2.6.24-19-generic/volatile
gvfs-fuse-daemon       98G  2.9G   90G   4% /home/zq/.gvfs
/dev/sdd1             123M  2.7M  121M   3% /media/ZQ
/dev/sdb1             190G  115G   76G  61% /media/EVA02


//edit3:

And here is **mount**

/dev/sdc2 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/zq/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=zq)
/dev/sdd1 on /media/ZQ type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
/dev/sdb1 on /media/EVA02 type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)

---

### Post by lukjad on 2008-07-29
Usually there is a saved version of your last change to a critical file. Don't change anything until someone more qualified than I can assist you. Can you also give a more detailed explanation of what you changed and where?

---

### Post by ZXQ on 2008-07-29
> **lukjad007 said:**
> Usually there is a saved version of your last change to a critical file. Don't change anything until someone more qualified than I can assist you. Can you also give a more detailed explanation of what you changed and where?

I changed the value in 'EVA03->Properties->Volume->Settings->File System' manually to just NTFS thinking that it was just notes or something.

it doesnt get much more explained than that unfortunately.

---

### Post by lukjad on 2008-07-29
Where is EVA03 located in the file system. I have never heard of it before. Is it in /etc or /usr maybe?

---

### Post by ZXQ on 2008-07-29
> **lukjad007 said:**
> Where is EVA03 located in the file system. I have never heard of it before. Is it in /etc or /usr maybe?

EVA03 is just the name of the drive.

its actually /dev/sdb.

and it is not mounted anywhere... for obvious reasons.

---

### Post by lukjad on 2008-07-29
Try this link. This may be helpful to you.
[http://www.debianadmin.com/mount-your-widows-partitions-and-make-it-readwritable-in-ubuntu.html](http://www.debianadmin.com/mount-your-widows-partitions-and-make-it-readwritable-in-ubuntu.html)

---

### Post by lukjad on 2008-07-29
[http://ubuntuforums.org/showthread.php?t=824671](http://ubuntuforums.org/showthread.php?t=824671)
This may be more what you are looking for.

---

### Post by ZXQ on 2008-07-29
> **lukjad007 said:**
> Try this link. This may be helpful to you.
[http://www.debianadmin.com/mount-your-widows-partitions-and-make-it-readwritable-in-ubuntu.html](http://www.debianadmin.com/mount-your-widows-partitions-and-make-it-readwritable-in-ubuntu.html)

Sir, ntfs3g is installed by default in 8.04.1

and /dev/sdb is another, identical, ntfs drive that is mounted just fine.

---

