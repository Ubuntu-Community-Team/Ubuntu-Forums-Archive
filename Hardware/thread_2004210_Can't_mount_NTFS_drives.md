---
title: "Can't mount NTFS drives"
date: 2012-06-15
forum: Hardware
---

### Post by Zoarob on 2012-06-15
Hello

I've been running Ubuntu by booting it from a flash disk for a while and everything was going ok. I've been able to access my Windows files without any problems. However recently I haven't been able to mount the NTFS drives that notmally run Windows on my machine.

Here is what I get when I try to open them:

```
Unable to mount 

Error mounting: mount exited with exit code 16: Mount is denied because the NTFS volume is already exclusively opened. The volume may be already mounted, or another software may use it which could be identified for example by the help of the 'fuser' command
```I'm new to using the terminal and therefore not very familiar with the commands required to solve this. But I do know how to see the list of mounted drives. When I type mount I get this:

```
rootfs on / type rootfs (rw)
none on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
none on /proc type proc (rw,nosuid,nodev,noexec,relatime)
none on /dev type devtmpfs (rw,relatime,size=1800756k,nr_inodes=210289,mode=755)
none on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
/dev/sdb1 on /cdrom type vfat (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
/dev/sdb1 on /casper-rw-backing type vfat (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop1 on /cow type ext2 (rw,noatime,errors=continue)
aufs on / type aufs (rw,noatime,si=bca8e2c6)
none on /sys/kernel/debug type debugfs (rw,relatime)
none on /sys/kernel/security type securityfs (rw,relatime)
none on /dev/shm type tmpfs (rw,nosuid,nodev,relatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev,relatime)
none on /var/run type tmpfs (rw,nosuid,relatime,mode=755)
none on /var/lock type tmpfs (rw,nosuid,nodev,noexec,relatime)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,nosuid,nodev,noexec,relatime)
```When I type sudo fdisk -l (Although I don't know entirely what it does), I get this:

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x76692ca8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1912    15357116   1c  Hidden W95 FAT32 (LBA)
/dev/sda2   *        1913       17112   122094000    7  HPFS/NTFS
/dev/sda3           17113       60801   350931892+   f  W95 Ext'd (LBA)
/dev/sda5           17113       60801   350931861    7  HPFS/NTFS

Disk /dev/sdb: 16.2 GB, 16173236224 bytes
255 heads, 63 sectors/track, 1966 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000250b6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1967    15794144+   c  W95 FAT32 (LBA)
```Any help or info regarding this would be much appreciated. Keep in mind I'm a noob so be please be patient  and explain what any command you suggest actually does. Thanks.

---

### Post by Zoarob on 2012-06-18
No one has any idea?

---

### Post by sudodus on 2012-06-18
> **Zoarob said:**
> 
Here is what I get when I try to open them:

```
Unable to mount 

Error mounting: mount exited with exit code 16: Mount is denied because the NTFS volume is already exclusively opened. The volume may be already mounted, or another software may use it which could be identified for example by the help of the 'fuser' command
```

Try fuser as suggested, for example the following command line
```
fuser -vm /dev/sda5
``` and post the result.

Read ```
man fuser
``` or simply type ```
fuser
``` to get information about the command.

---

### Post by Zoarob on 2012-06-18
Thanks for the reply.

When I give the command you suggested, nothing happens. When I type it without -vm, I get the following:

> Cannot stat file /proc/4212/fd/22: Stale NFS file handle
Cannot stat file /proc/4340/fd/22: Stale NFS file handle
Cannot stat file /proc/4342/fd/22: Stale NFS file handle


---

### Post by sudodus on 2012-06-18
I suggest that you run that command also for sda2:
```
fuser -vm /dev/sda2
```
and see if you get more info from that.

Anyway, something seems wrong. I searched the internet for ***Stale NFS file handle*** and found several descriptive links, for example this one
[[COLOR="Red"]_http://www.cyberciti.biz/tips/nfs-stale-file-handle-error-and-solution.html_[/COLOR]]("http://www.cyberciti.biz/tips/nfs-stale-file-handle-error-and-solution.html")

Do you [try to] connect to the NTFS drive(s) via NFS, which is a network protocol?

Wikipedia:  Network File System (NFS) is a distributed file system protocol originally developed by Sun Microsystems in 1984,[1] allowing a user on a client computer to access files over a network in a manner similar to how local storage is accessed.

---

