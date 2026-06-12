---
title: "Sony DRU-540A CD/DVD-RW unmountable?"
date: 2010-06-25
forum: Hardware
---

### Post by JKirchartz on 2010-06-25
Hey, I'm running 9.04 jaunty and I'm having issues with my cd/dvd drive, it works properly (reading & writing) on windows xp, but when I try to do anything with it in Ubuntu it says there's no media.
With a known-good data CD in the drive "ls -l /dev/sd*" says:
```

brw-rw---- 1 root disk 8,  0 2010-06-25 12:30 /dev/sda
brw-rw---- 1 root disk 8,  1 2010-06-25 12:30 /dev/sda1
brw-rw---- 1 root disk 8,  2 2010-06-25 12:30 /dev/sda2
brw-rw---- 1 root disk 8,  5 2010-06-25 12:30 /dev/sda5
brw-rw---- 1 root disk 8, 16 2010-06-25 12:30 /dev/sdb
brw-rw---- 1 root disk 8, 17 2010-06-25 12:30 /dev/sdb1

```
and "mount" says:
```

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
lrm on /lib/modules/2.6.28-19-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/jkirchartz/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jkirchartz)
/dev/sdb1 on /media/disk type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

```

I can't figure it out, CDs read fine in my old 52xMTRP cd-rom drive, any help or suggestions?

---

### Post by ieee488 on 2010-06-25
on my laptop, the CD/DVD drive is /dev/sr0

do you see the drive in System -> Administration -> Disk Utility  ?

---

