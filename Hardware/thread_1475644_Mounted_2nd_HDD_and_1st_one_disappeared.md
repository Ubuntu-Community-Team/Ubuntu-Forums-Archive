---
title: "Mounted 2nd HDD and 1st one disappeared"
date: 2010-05-07
forum: Hardware
---

### Post by AnneM on 2010-05-07
Hi everyone,

I've only been using Ubuntu for a few months now so I am not all that well versed. I am running Ubuntu 10.04.

I have a second HDD in my system which I mounted according to the Ubuntu instructions after formatting it in FAT32. However, after I successfully mounted the second hard drive, the original one has completely disappeared. When I go to check devices I can see the disk and it shows the same space usage as before except now it's in one partition when it used to be two.

I am really not sure what happened and any help would be appreciated. When I run mount I get this:

```
/dev/sda1 on / type ext4 (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/sda1 on /media/268B-53CF type ext4 (rw,noexec,nosuid,nodev)
/dev/sdb1 on /media/1C07-70CF type vfat (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/anne/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=anne)
```

Thanks ever so much.

---

### Post by dino99 on 2010-05-07
install mountmanager and tweak it as you need

fdsk -l

[http://ubuntuforums.org/showthread.php?t=1467891&page=2](http://ubuntuforums.org/showthread.php?t=1467891&page=2) post 14

---

### Post by metallus on 2010-05-07
Please remove the second /dev/sda1 mount from /media/268B-53CF mount point. you have /dev/sda1 mounted twice, once as the root filesistem (/) and once again in /media/268B-53CF
If you don't know how to do that, please ask here.
Or you can use System->Administration->Disk utility.
Good Luck!

---

