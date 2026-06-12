---
title: "cannot mount philips mp3 player"
date: 2010-03-31
forum: Hardware
---

### Post by jon zendatta on 2010-03-31
Until recently I could mount my philips go-gear no problem. Now I get 'you are not privileged to mount volume'

```
j0n@j0n-laptop:~$ lsusb
Bus 001 Device 003: ID 0471:207c Philips 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

```
j0n@j0n-laptop:~$ mount
/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-18-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/j0n/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=j0n)


```

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1ba117c3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3656    29366788+   7  HPFS/NTFS
/dev/sda2            3657        9729    48781372+   5  Extended
/dev/sda5            3657        9545    47303361   83  Linux
/dev/sda6            9546        9729     1477948+  82  Linux swap / Solaris
Note: sector size is 4096 (not 512)

Disk /dev/sdb: 3927 MB, 3927965696 bytes
177 heads, 53 sectors/track, 102 cylinders
Units = cylinders of 9381 * 4096 = 38424576 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         103     3835900    b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(59, 176, 53) logical=(102, 39, 47)
```

Any ideas please.

---

### Post by jon zendatta on 2010-03-31
Interesting, like I said this was 'mounting' until recently. Off to work now so I'll check tonight:KS

---

### Post by jon zendatta on 2010-04-01
So I tested on my partners computer Ubuntu 9.04 & instant mount.
```
green1@green1-laptop:~$ mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-18-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/green1/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=green1)
/dev/sr0 on /media/cdrom0 type udf (ro,nosuid,nodev,utf8,user=green1)
/dev/sdb1 on /media/PHILIPS type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
```
Here is mine, the problem.
```
j0n@j0n-laptop:~$ mount
/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-18-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/j0n/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=j0n)
```

---

### Post by jon zendatta on 2010-04-03
Just noticed I can't mount my camera either.

---

### Post by jon zendatta on 2010-04-03
problem solved.
In /etc/fstab/ i deleted the line referring to /dev/sdb1/:KS

---

