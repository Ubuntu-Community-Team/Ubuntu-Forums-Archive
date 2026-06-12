---
title: "Multiple hard drives to /"
date: 2016-01-10
forum: Hardware
---

### Post by Bruno_Hazer on 2016-01-10
Hi guys,
I have problem with mouting hard drives on my server. I have HP Proliant DL380 G4 with 6 hard drives. A long time ago I do something with drives and now I don't like ist. I mount hard drives on directory */data *and system space on /.

Here ist my **df -h**
```
root@bravo:/data/shared/Brunes# df -h
Filesystem                  Size  Used Avail Use% Mounted on
udev                        2.4G  4.0K  2.4G   1% /dev
tmpfs                       490M  772K  489M   1% /run
/dev/mapper/bravo--vg-root   29G  3.6G   25G  13% /
none                        4.0K     0  4.0K   0% /sys/fs/cgroup
none                        5.0M     0  5.0M   0% /run/lock
none                        2.4G     0  2.4G   0% /run/shm
none                        100M     0  100M   0% /run/user
/dev/cciss/c0d0p1           236M   85M  139M  39% /boot
/dev/cciss/c1d0             404G  133G  251G  35% /data

```

Now, I want set all space with space for system to **/** directory. This can be set up somehow? I've clueless and it's very important for me.
Thanks for help and sorry for my Slovak-English.

---

### Post by SeijiSensei on 2016-01-10
Why bother?  You're not running out of space in /.  Trying to reconfigure storage is a complicated task even for experienced users.  Unless you have a compelling need to do this, I'd just leave things alone.

---

### Post by weatherman2 on 2016-01-10
Your / partition is already an LVM logical volume.  To add additional disk space to it from other devices, create new LVM partitions on other disks, add them to the same volume group, then extend your original logical volume.

---

