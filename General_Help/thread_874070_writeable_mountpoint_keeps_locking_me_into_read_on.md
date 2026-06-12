---
title: "writeable mountpoint keeps locking me into read only mode"
date: 2008-07-29
forum: General Help
---

### Post by HangukMiguk on 2008-07-29
My external hard drive was working perfectly normally yesterday.  Then all of a sudden, after a reboot, it now refuses to be written to, sending me to read only mode.

Fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=29497596-f6a1-40d8-a6c4-49986ad43291 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=0a5cf21a-8354-4e62-b982-7b2e55f1397f none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/sdb1	/media/SEA_DISC vfat	user,rw,noauto	0	0
```

mtab:
```
/dev/sda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.24-19-generic/volatile tmpfs rw 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
/dev/sdb1 /media/SEA_DISC vfat rw,noexec,nosuid,nodev,user=corey 0 0
```

fsck of sdb1:

```
fsck 1.40.8 (13-Mar-2008)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
There are differences between boot sector and its backup.
Differences: (offset:original/backup)
  65:01/00
1) Copy original to backup
2) Copy backup to original
3) No action
? 3
File system has 2441533 clusters but only space for 2441470 FAT entries.
```

help?

---

### Post by CrusaderAD on 2008-07-29
I had the same thing happen which was bizarre. I plugged it into a windows machine and double checked the permissions. I also had pendrivelinux setup and took a look in there. It worked after I plugged it back into Ubuntu. I must have fixed something with the permissions.

---

