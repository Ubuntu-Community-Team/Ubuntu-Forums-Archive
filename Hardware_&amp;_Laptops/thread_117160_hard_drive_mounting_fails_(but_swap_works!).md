---
title: "hard drive mounting fails (but swap works!)"
date: 2006-01-14
forum: Hardware &amp; Laptops
---

### Post by jester12345 on 2006-01-14
I'm very sorry if I'm duplicating someone else's post. I've read a lot of posts which all seem to suggest the same set of procedures, but none that seem to solve my problem. If there is a post I missed, please point me to it.

So, here is the issue. I have 2 drives, hda and hdb. Hda has the OS, and is working fine. Both drives have some swap space on them. The Disk and Filesystem applet (under settings:/System/) reports that both swaps are enabled. So, I am reasonably certain that the drive is good. It was certainly recognized during installation, and I was allowed to create a partition and format it.

fstab has an entry for hdb, which appears correct to me:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               reiserfs notail          0       1
/dev/hdb2       /backup         reiserfs defaults        0       2
/dev/hda1       none            swap    sw              0       0
/dev/hdb1       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

However, when I try 'sudo mount -a' I get:
```
mount: /dev/hdb2 already mounted or /backup busy
```

Lsof didn't return anything:
```
jester@caliban:/$ sudo lsof /backup
jester@caliban:/$ sudo lsof /dev/hdb
jester@caliban:/$ sudo lsof /dev/hdb2
```

dmsg might give a clue in that the data for hda and hdb are different:
```
jester@caliban:/$ dmesg | grep hda
[4294681.948000] ReiserFS: hda2: found reiserfs format "3.6" with standard journal
[4294686.156000] ReiserFS: hda2: using ordered data mode
[4294686.182000] ReiserFS: hda2: journal params: device hda2, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[4294686.185000] ReiserFS: hda2: checking transaction log (hda2)
[4294686.224000] ReiserFS: hda2: Using r5 hash to sort names
[4294692.557000] Adding 2096440k swap on /dev/hda1.  Priority:-1 extents:1
jester@caliban:/$ dmesg | grep hdb
[4294681.861000] md: bind<hdb2>
[4294692.577000] Adding 2096440k swap on /dev/hdb1.  Priority:-2 extents:1
```

It only seems to have found the file system on hda, not hdb.

One thing I was surprised about in dmesg was that raid appeared to be configured, but I don't remember doing that! Could it be that hdb2 is being reported as busy because it's in a raid configuration? If so, can I break that without having to reinstall? Raid is good, but I need the storage space. Here's the relevant dmesg parts:
```
[4294681.652000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294681.658000] md: raid1 personality registered as nr 3
[4294681.829000] devfs_mk_dev: could not append to parent for md/0
[4294681.835000] md: md0 stopped.
[4294681.836000] md: bind<hdb>
[4294681.836000] md: md0: raid array is not clean -- starting background reconst
ruction
[4294681.836000] raid1: raid set md0 active with 1 out of 2 mirrors
[4294681.855000] devfs_mk_dev: could not append to parent for md/1
[4294681.860000] md: md1 stopped.
[4294681.861000] md: bind<hdb2>
[4294681.862000] raid1: raid set md1 active with 1 out of 1 mirrors

```


Thanks for the help

---

### Post by lha on 2006-01-19
You can use
```
cat /proc/mdstat
```
to find out if mdadm thinks you have raid configured. If you are willing to post the output of
```
cat /etc/mdadm/mdadm.conf
```
```
sudo fdisk -l
```
```
mount
```
```
df -h
``` I'd take a look and see if I can help you out.

---

