---
title: "Install problem on Latitude E4200 (no partitions visible) 8.10"
date: 2008-12-10
forum: Installation &amp; Upgrades
---

### Post by schaile on 2008-12-10
Hello,
I try to install Ubuntu 8.10 on a DELL Latitude E4200 with a 64 Gbyte
solid state disk. I use the method described here (Live CD on Windows XP):
[https://help.ubuntu.com/community/Installation/FromWindows](https://help.ubuntu.com/community/Installation/FromWindows)
After booting I right away start "Install" (no browsing of disks).
At the point where partitions should be choosen I see an empty table.

fdisk and mount show this:

ubuntu@ubuntu:~$ sudo fdisk -l

[U][B]Disk /dev/sda: 64.0 GB, 64023257088 bytes
255 heads, 63 sectors/track, 7783 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x98deb064
[/B][/U]
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          16      128488+  de  Dell Utility
/dev/sda2   *          17        3760    30073680    7  HPFS/NTFS
/dev/sda3            3761        5715    15703537+  83  Linux
Note: the ext3 on /dev/sda3 I made with gparted, 
       before,  with a 32 Gbyte free space, the result was the same

ubuntu@ubuntu:~$ sudo mount

/proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/sda2 on /cdrom type fuseblk (rw,nosuid,nodev,user_id=0,group_id=0,allow_other,blksize=4096)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)

Any suggestions?
Thanks in advance for help. 
Otto

---

### Post by avilella on 2009-01-25
Hi,

I took the liberty of creating a launchpad team for the people who own or develop for the Dell Latitude E4200/E4300 laptops, so that we can have more visibility upstream when having to ask for patches or support.

[https://launchpad.net/~e4200-e4300](https://launchpad.net/~e4200-e4300)

I'll be sending a couple of messages to ubuntuforums and notebookreview forums to gather the ~15 users I've identified so far.

Cheers,

Albert.


> **schaile said:**
> Hello,
I try to install Ubuntu 8.10 on a DELL Latitude E4200 with a 64 Gbyte
solid state disk. I use the method described here (Live CD on Windows XP):
[https://help.ubuntu.com/community/Installation/FromWindows](https://help.ubuntu.com/community/Installation/FromWindows)
After booting I right away start "Install" (no browsing of disks).
At the point where partitions should be choosen I see an empty table.

fdisk and mount show this:

ubuntu@ubuntu:~$ sudo fdisk -l

[U][B]Disk /dev/sda: 64.0 GB, 64023257088 bytes
255 heads, 63 sectors/track, 7783 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x98deb064
[/B][/U]
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          16      128488+  de  Dell Utility
/dev/sda2   *          17        3760    30073680    7  HPFS/NTFS
/dev/sda3            3761        5715    15703537+  83  Linux
Note: the ext3 on /dev/sda3 I made with gparted, 
       before,  with a 32 Gbyte free space, the result was the same

ubuntu@ubuntu:~$ sudo mount

/proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/sda2 on /cdrom type fuseblk (rw,nosuid,nodev,user_id=0,group_id=0,allow_other,blksize=4096)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)

Any suggestions?
Thanks in advance for help. 
Otto

---

