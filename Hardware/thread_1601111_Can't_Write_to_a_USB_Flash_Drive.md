---
title: "Can't Write to a USB Flash Drive?"
date: 2010-10-19
forum: Hardware
---

### Post by csharpplus on 2010-10-19
Hi,

I have a USB Flash Drive connected in the USB port. Ubuntu recognizes it, and allows me to view the contents of the files that are there, open them etc.

Yet, from whatever reason, I cannot write to (or change) files that are stored in this USB drive, even though I have a lot of free space (800 MB).

How can I solve this?  thanks in advance.

---

### Post by mikewhatever on 2010-10-19
Can you post the output of the following command:

```
mount
```

I suspect the device is mounted as read only, in which case you can't copy files to it.

---

### Post by csharpplus on 2010-10-19
Thank you for your help. Here's what I get:

```

cs@internet:~/scratch$ mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
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
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/cs/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=cs)
/dev/sdb on /media/KINGSTON type vfat (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)

```The USB key was made by Kingston. I guess then that the last line is relevant?

---

### Post by mikewhatever on 2010-10-19
Very odd. It shows the device is mounted and not the partition.
Should have been something like this:

/dev/sdb**X** on /media/KINGSTON type vfat (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)

where **X** designates the partition.

---

### Post by csharpplus on 2010-10-19
All I did was inserting the flash drive into the USB port. nothing else.

Any ideas how to solve this?

---

### Post by mikewhatever on 2010-10-20
I was going to suggest a file system check, but you need a partition to run it on. :confused:

---

### Post by csharpplus on 2010-10-20
Is there anything I can do to mount it differently?

---

