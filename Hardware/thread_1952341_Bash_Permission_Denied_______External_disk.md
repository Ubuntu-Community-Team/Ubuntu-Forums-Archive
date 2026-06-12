---
title: "Bash: Permission Denied       External disk"
date: 2012-04-04
forum: Hardware
---

### Post by bioinfor on 2012-04-04
Hi all

I am trying to read files from an external disk and it just does not work. I get a message Bash: /media...   Permission Denied.
It is a 3TB disk and it seems to be mounted as it shows up in the fdisk:
Anyone who can help?

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1201     9642146+  27  Unknown
/dev/sda2   *        1567        1580      102400    7  HPFS/NTFS
/dev/sda3            1580       54427   424498200    7  HPFS/NTFS
/dev/sda4           54428       60802    51198977    f  W95 Ext'd (LBA)
/dev/sda5           54428       60802    51198976   83  Linux
Note: sector size is 4096 (not 512)

Disk /dev/sdb: 3000.6 GB, 3000592977920 bytes
255 heads, 63 sectors/track, 45600 cylinders
Units = cylinders of 16065 * 4096 = 65802240 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x13f5c655

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       45601  2930256000    7  HPFS/NTFS
Partition 1 does not start on physical sector boundary.

---

### Post by zeljkojagust on 2012-04-04
I don't see /dev/sdb1 mounted anywhere from the output you pasted....

---

### Post by bioinfor on 2012-04-04
I think its monted: (last line)

Aspire-3810T:~$ mount
/dev/sda5 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/robin/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=robin)
/dev/sdb1 on /media/FreeAgent GoFlex Drive type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)

---

### Post by coffeecat on 2012-04-04
It is mounted, on /media/FreeAgent, but did you post the full error message that you see? Post both the command you are using that results in the error and the full error message itself.

---

