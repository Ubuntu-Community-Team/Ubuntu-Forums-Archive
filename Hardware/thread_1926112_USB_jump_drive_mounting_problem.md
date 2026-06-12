---
title: "USB jump drive mounting problem"
date: 2012-02-15
forum: Hardware
---

### Post by vduck on 2012-02-15
I can't get my laptop to recognize my Toshiba usb flash drive. I think it can't figure out the fs type. The key does work in my other machine (also ubuntu).
Could the be a problem with devtmpfs?

my machine:
uname -a
```

Linux wing 3.0.0-16-generic #28-Ubuntu SMP Fri Jan 27 17:44:39 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
```


 mount
```

/dev/sda1 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sda3 on /home type ext4 (rw,commit=0)
/dev/sda2 on /usr type ext4 (rw,commit=0)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/vduck/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=vduck)

```

sudo fdisk -l /dev/sdb
```

Disk /dev/sdb: 8015 MB, 8015282176 bytes
10 heads, 41 sectors/track, 38182 cylinders, total 15654848 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x387101a2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048    15654847     7826400   83  Linux

```

df -T /dev/sdb
```

Filesystem    Type   1K-blocks      Used Available Use% Mounted on
udev      devtmpfs      950420         4    950416   1% /dev

```

---

### Post by vduck on 2012-02-15
You know, I decided this is more trouble than it's worth. I'm reformatting the key and I'll copy the data onto it again. I'll post if this doesn't work.

---

