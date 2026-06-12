---
title: "New internal hard drive - cannot paste to it"
date: 2014-11-16
forum: Hardware
---

### Post by Grant_Williamson on 2014-11-16
I am a non-technical Ubuntu user...
I installed a new internal hard drive into my PC.
I think I have partitioned it correctly by following Ubuntu forums help/ instructions...
I think I have created the mount point correctly...
But now when I cut and past, the Paste is greyed out in the new drive... its sdb1

```

# /etc/fstab: static file system information.#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=ed680e89-a7d9-4e66-9590-1ba81ea44485 none            swap    sw              0       0
/dev/sdb1    /media/WD1TB   ext4    defaults     0        2

```

```
~$ mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
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
none on /sys/fs/pstore type pstore (rw)
/dev/sdb1 on /media/WD1TB type ext4 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=wiley)



```

Please help, many thanks!

---

### Post by Grant_Williamson on 2014-11-16
Right, after a lot of searches, this has solved it:
```
sudo chown -R wiley:wiley /media/WD1TB
```

---

