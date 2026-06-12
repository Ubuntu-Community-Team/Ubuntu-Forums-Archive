---
title: "Gutsy can't find my Windows XP HDD anymore"
date: 2007-11-05
forum: Hardware &amp; Laptops
---

### Post by galvao on 2007-11-05
Hi there.

After a "fresh" install of Gutsy my Windows XP HDD doesn't show anymore... Worked fine on Feisty. 

Here's some info:

```

galvao@galvao-desktop ~> mount
/dev/sdb5 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
/dev/sdb6 on /home type ext3 (rw)
/dev/sdb1 on /media/sdb1 type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)

``````

galvao@galvao-desktop ~> sudo fdisk -l

Disk /dev/sda: 60.0 GB, 60040544256 bytes
255 heads, 63 sectors/track, 7299 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1e3e1e3d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7298    58621153+   7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x06930692

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3835    30804606    7  HPFS/NTFS
/dev/sdb2            6376       19214   103129267+   f  W95 Ext'd (LBA)
/dev/sdb3           19215       19452     1911735   82  Linux swap / Solaris
/dev/sdb5            6376        8880    20121381   83  Linux
/dev/sdb6            8881       19214    83007823+  83  Linux

```So, looks like my "missing" HDD is on /dev/sda1 right? So, I try:

galvao@galvao-desktop ~> sudo ntfs-3g /dev/sda1 /mnt/point

and I get:

```

NTFS signature is missing.
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?

```Note that I never touched this HDD when partitioning on Gutsy's installation...

So, What can I do?

TIA,

---

### Post by ROBarber on 2007-11-05
[http://www.psychocats.net/ubuntu/mountwindows]("http://www.psychocats.net/ubuntu/mountwindows")

maybe this will help you. it seems that you skiped some steps in mounting windows partition.

good luck

---

### Post by galvao on 2007-11-05
Thanks a lot for your reply. I'll try that and post the results in here.

regards,

---

### Post by damatta on 2007-11-07
Hi, i'm experiencing a similar problem.
Suddenly I noticed my xp partition was not mounted.
I tried to do it manually but:
"Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda1 /media/sda1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda1 /media/sda1 ntfs-3g defaults,force 0 0
"
What should i do?
this is my fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/mapper/sda3_crypt /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=921c5ea7-5869-426b-b702-1a9dfb2c7de1 /boot           ext3    defaults        0       2
# /dev/sda1
UUID=CEE4E77AE4E76367 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
/dev/mapper/sda4_crypt none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

thanks

---

### Post by Arthur Archnix on 2007-11-08
I received a similar error after Windows failed to shutdown correctly. You have two options:

1. Reboot into windows, and Windows does not automatically do a disk check then schedule on to be performed on the drive, reboot and allow windows to disk-check, then reboot into Ubuntu and it should be fine.

2. Ignore the error and copy paste the mount line into your terminal, hit enter.

The first option is obviously safer, but if your not concerned about possible data loss then simply hit f to mount it anyway. 

No changes are required to your fstab, this is likely a one time error.

---

### Post by galvao on 2007-11-16
Thank you all for your replies.

ROBarber solution didn't worked, I still receive the same error message. 

I'll try the others (must check if grub recognizes the partition so I can boot it, not sure right now) and post a reply ASAP.

Cheers,

---

### Post by restless on 2008-02-20
> **damatta said:**
> 

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda1 /media/sda1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda1 /media/sda1 ntfs-3g defaults,force 0 0
"

I tried this and it worked. 
even afterdisconnecting all removable devices in win and setting it to normal, the previous line in fstab was not enough.
I added 
  /dev/sda1 /media/sda1 ntfs-3g defaults,force 0 0
and now it is mounted without any problem

thank you
lor

---

### Post by ubunt00 on 2008-02-20
> **restless said:**
> I tried this and it worked. 
even afterdisconnecting all removable devices in win and setting it to normal, the previous line in fstab was not enough.
I added 
  /dev/sda1 /media/sda1 ntfs-3g defaults,force 0 0
and now it is mounted without any problem

thank you
lor

I tried to add that to the /etc/fstab file
it keeps on saying that I do not have the permission to edit this file.
when I went to properties-->permission tab, i couldn't change any options. What do I do?:confused:

---

### Post by Yellow Pasque on 2008-02-21
IN terminal:
sudo gedit /etc/fstab

Also, you probably don't want to do a force mount every time and you want non-root access, so:
```
/dev/sda1  /media/sda1  ntfs-3g  rw,auto,exec,user,uid=1000  0  0
```

---

### Post by prak97 on 2008-05-07
remove all packages called "evms".....it's a known bug , and removing the package and rebooting fixes it .

---

