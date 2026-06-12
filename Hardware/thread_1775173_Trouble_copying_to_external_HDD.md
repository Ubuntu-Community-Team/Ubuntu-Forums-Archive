---
title: "Trouble copying to external HDD"
date: 2011-06-04
forum: Hardware
---

### Post by marcusesses on 2011-06-04
I am trying to copy the contents of my home drive to an external HDD (I believe [this]("http://www.wdc.com/en/products/products.aspx?id=440") is the model), and I am receiving an error that says

"There was an error copying the file into /media/My Passport.

- Show more details

Error opening '/media/My Passport/file.pdf': Input/output error"

I am able to remove files from the HDD and copy them to my home drive, but I can't do the reverse. Any suggestions as to what could be happening here?

EDIT: Some more information

The output of the command "df -h" gives

```
/dev/sdd1             466G   94G  373G  20% /media/My Passport
```

so there seems to be adequate space on the drive. If there are any other commands that would be helpful for diagnosing this, just let me know.

---

### Post by marcusesses on 2011-06-05
Here is the output of the "mount" command, in case it is insightful:

```
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw)
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
gvfs-fuse-daemon on /home/mjbaron/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=me)
/dev/sdc1 on /media/KINGSTON_ type vfat (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sr1 on /media/WD SmartWare type udf (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,umask=0077)
/dev/sdd1 on /media/My Passport type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
```

---

