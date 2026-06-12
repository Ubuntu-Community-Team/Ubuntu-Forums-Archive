---
title: "Permission denied to access an external hardrive"
date: 2013-05-09
forum: Hardware
---

### Post by Smajjk on 2013-05-09
I have an external hardrive it is 1TB, ext2 file system. I have some problem accessing it:

```
smajjk@pc[/][16:01]:mount
/dev/mapper/xubuntu-root on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
/dev/sdb1 on /boot type ext2 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfsd-fuse on /run/user/smajjk/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=smajjk)
/dev/sda1 on /media/smajjk/New Volume type ext2 (rw,nosuid,nodev,uhelper=udisks2)

smajjk@pc[/][16:01]:cd /media/smajjk/New\ Volume
cd: permission denied: /media/smajjk/New Volume
```

Any idea how to fix this problem?

Thanks :)

---

### Post by Smajjk on 2013-05-09
Actually got it working by typing:

```
 sudo chown -R smajjk:smajjk /path/to/mounted/drive
```

---

