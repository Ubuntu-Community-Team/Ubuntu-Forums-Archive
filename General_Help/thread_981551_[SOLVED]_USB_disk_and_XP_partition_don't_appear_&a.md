---
title: "[SOLVED] USB disk and XP partition don't appear &amp;quot;correctly&amp;quot;  on desktop"
date: 2008-11-13
forum: General Help
---

### Post by bw44 on 2008-11-13
I just upgraded from Gutsy to Hardy.  Under Gutsy my usb data sticks and external usb hard drive, as well as my XP partition (dual boot) all appeared on my Gnome desktop, as follows: FD1, FD2, HD and XP.  FD1 and FD2 are the volume names on the data sticks; HD and XP were specified in /ect/fstab. 

Under Hardy, instead of appearing on the desktop with the names specified in /etc/fstab, the external disk and XP partion appear as "250.1 GB Media" and "24.1GB Media."  However, the devices do appear in /etc/mtab and in /media as /media/HD and /media/XP.

Below are the contents of my /etc/fstab and /etc/mtab files:```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
#
proc            /proc           proc    defaults        0       0
#
# /dev/sda2 -- Linux boot partition
#
UUID=ef823109-c8b7-4cbb-912a-7ddf050e7281 /               ext3    defaults,errors=remount-ro 0       1
#
# /dev/sda1 (/media/XP) -- Windows XP boot partition
#
UUID=220B45742E7AFCAF /media/XP     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
#
# /dev/sda5 -- Linux swap partition
#
UUID=0adbc8ca-557b-4e32-8838-78c2b5740da6 none            swap    sw              0       0
#
# /dev/sdc1 (ususally?) (/media/HD) -- LaCie 250GB USB disk
#
UUID=3f1f4772-79e9-43d4-afb8-f429098eef7e /media/HD       ext3    rw,users,exec,errors=remount-ro 0       1   
#
# /dev/scd0 (/media/cdrom0)
#
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
```
```
/dev/sda2 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.24-21-generic/volatile tmpfs rw 0 0
/dev/sda1 /media/XP fuseblk rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096 0 0
/dev/sdb1 /media/HD ext3 rw,nosuid,nodev,errors=remount-ro 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
/dev/sdd1 /media/FD2 vfat rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush 0 0
/dev/sdc1 /media/FD1 vfat rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush 0 0
```

I'm pretty sure it's just a cosmetic issue, but can anyone tell me how to get the usb disk and XP partition labeled "HD" and "XP" on the desktop?

Thanks.

bw44

---

### Post by cariboo on 2008-11-13
In Hardy and above if the hard drives don't have labels they will show up the way they do on your desktop, to label the drives you can use ntfslabel, which is part of the ntfsprogs package. Or you can use the disk management utility in Windows. Ntfsprogs is available in the repositories, and you can use Add/Remove Programs, Synaptic Package Manager and of course the command line to install it.

Jim

---

### Post by bw44 on 2008-11-13
> **cariboo907 said:**
> In Hardy and above if the hard drives don't have labels they will show up the way they do on your desktop, to label the drives you can use ntfslabel, which is part of the ntfsprogs package. Or you can use the disk management utility in Windows. Ntfsprogs is available in the repositories, and you can use Add/Remove Programs, Synaptic Package Manager and of course the command line to install it.

Jim

Thanks very much!  I couldn't use ntfslabel to assign a label to my usb hard disk, since it's formatted ext3. (Ntfslabel worked fine with the XP partition.)  But once you gave me the info that Hardy is picking up the label, I assigned the usb disk the name "HD" using e2label.  Problem solved!

Cheers,
bw44

---

