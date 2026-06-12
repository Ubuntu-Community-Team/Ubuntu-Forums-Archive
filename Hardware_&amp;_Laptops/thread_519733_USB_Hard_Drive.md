---
title: "USB Hard Drive"
date: 2007-08-07
forum: Hardware &amp; Laptops
---

### Post by trueegor on 2007-08-07
I have a FreeAgent USB drive that used to mount automatically when connected but now it won't.  It's formatted ntfs.  The drive works fine with my Windows machine.

Just did a new install of the OS Ubuntu 7.04.  

there is no entry for it in fstab

partial output from fdisk -l
```
Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    7  HPFS/NTFS

```

Any ideas.

---

### Post by merlinus on 2007-08-07
What mount point have you created for this drive?  Have you installed and configured ntfs-3g and ntfs-config?

Mount the drive and post results of:

```

mount
cat /etc/fstab

```

-merlin

---

### Post by trueegor on 2007-08-07
The thing is that it used to work in Feisty without doing anything.  Plug it in and I would get an icon on the desktop.  

ntfs-3g and ntfs-config are installed

Forgive me, I'm a relative newbie.

I attemted to add a line for the freeagent to the fstab.  It wasn't there before.

Output of mount
```
/dev/hda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-15-generic/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sdb1 on /media/FreeAgent Drive type ntfs (rw)

```

Output of cat /etc/fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=3907a080-cc19-43b9-b4fc-d194ee08f2a9 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=8961622a-2fb9-49a2-8025-409190b50799 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sdb1       /media/FreeAgent\ Drive auto    rw,user,noauto  0       0

```

---

### Post by merlinus on 2007-08-07
> 
/dev/sdb1       /media/FreeAgent\ Drive auto    rw,user,noauto  0       0
You need to specify the filsystem, and backslashes are not used in linux.

So you might try this:

/dev/sdb1 /media/FreeAgent ntfs-3g defaults,locale=en_US.utf8 0 0

-merlin

---

