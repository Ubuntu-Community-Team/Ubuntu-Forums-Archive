---
title: "Will #mdadm --create delete data on my partition?"
date: 2009-09-16
forum: Hardware
---

### Post by sunpyo on 2009-09-16
I've been through all I can with trying to --assemble my Raid 5 data. However I've heard that #mdadm --create will recreate my RAID intuitively because it recognizes the previously created array parameters and such. So just to get some clarification,
 
Will mdadm #create delete any of the data on my partitions or will it just recreate the array? Thanks!

---

### Post by laluz on 2009-09-16
how about "man mdadm" ? 
"mdadm --assemble --scan" is probably what you are looking for.

---

### Post by freackout on 2009-09-16
> **sunpyo said:**
> I've been through all I can with trying to --assemble my Raid 5 data. However I've heard that #mdadm --create will recreate my RAID intuitively because it recognizes the previously created array parameters and such. So just to get some clarification,
 
Will mdadm #create delete any of the data on my partitions or will it just recreate the array? Thanks!

i once thought i'd lost data wilst messing around with raid disks and ext3/4 ect anyway simply installed a small hard drive and put 9.04 alternate on it and it found all my raid stuff strait away.

---

### Post by sunpyo on 2009-09-16
i already tried:
 
#mdadm --assemble --scan
 
I am able to assemble the raid by doing that, however I am unable to browse to look for the data. I also cannot mount or anything like that. I do however know that the partition is ext3. However I cannot mount by doing:
 
#mount -t ext3 /dev/md2 /media/disk/shares <--- this is the directory it should be mounted to.
 
Anyhow like I said. I can assemble the raid, but it does not open to view the files or anything.

---

### Post by tgrimley on 2009-09-16
Looks like I was wrong, --create doesn't necessarily destroy your data.  I tried it on my virtual machine and it was okay, but ymmv:

```
tgrimley@tgrimley-virtual:~$ cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid6 sdd1[3] sdb1[1] sda1[0] sdc1[2]
      41929344 blocks level 6, 64k chunk, algorithm 2 [4/4] [UUUU]
      
md1 : active raid1 sdf1[1] sde1[0]
      2096384 blocks [2/2] [UU]
      
unused devices: <none>
tgrimley@tgrimley-virtual:~$ mkdir md0mount
tgrimley@tgrimley-virtual:~$ sudo mount /dev/md0 md0mount/
[sudo] password for tgrimley: 
tgrimley@tgrimley-virtual:~$ cd md0mount/
tgrimley@tgrimley-virtual:~/md0mount$ ls
lost+found
tgrimley@tgrimley-virtual:~/md0mount$ sudo chown tgrimley /home/tgrimley/md0mount/
tgrimley@tgrimley-virtual:~/md0mount$ sudo echo "tesssssssssst" >> testfile
tgrimley@tgrimley-virtual:~/md0mount$ cat testfile 
tesssssssssst
tgrimley@tgrimley-virtual:~/md0mount$ cd ..
tgrimley@tgrimley-virtual:~$ sudo umount md0mount/
tgrimley@tgrimley-virtual:~$ ls md0mount/
tgrimley@tgrimley-virtual:~$ cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid6 sdd1[3] sdb1[1] sda1[0] sdc1[2]
      41929344 blocks level 6, 64k chunk, algorithm 2 [4/4] [UUUU]
      
md1 : active raid1 sdf1[1] sde1[0]
      2096384 blocks [2/2] [UU]
      
unused devices: <none>
tgrimley@tgrimley-virtual:~$ sudo mdadm --stop /dev/md0
mdadm: stopped /dev/md0
tgrimley@tgrimley-virtual:~$ sudo mdadm --create /dev/md0 --level=raid6 --raid-disks=4 /dev/sd[a-d]1
mdadm: /dev/sda1 appears to contain an ext2fs file system
    size=41929344K  mtime=Wed Sep 16 16:38:45 2009
mdadm: /dev/sda1 appears to be part of a raid array:
    level=raid6 devices=4 ctime=Wed Sep  2 18:08:49 2009
mdadm: /dev/sdb1 appears to contain an ext2fs file system
    size=41929344K  mtime=Wed Sep 16 16:38:45 2009
mdadm: /dev/sdb1 appears to be part of a raid array:
    level=raid6 devices=4 ctime=Wed Sep  2 18:08:49 2009
mdadm: /dev/sdc1 appears to be part of a raid array:
    level=raid6 devices=4 ctime=Wed Sep  2 18:08:49 2009
mdadm: /dev/sdd1 appears to contain an ext2fs file system
    size=41929344K  mtime=Wed Sep 16 16:38:45 2009
mdadm: /dev/sdd1 appears to be part of a raid array:
    level=raid6 devices=4 ctime=Wed Sep  2 18:08:49 2009
Continue creating array? y
mdadm: array /dev/md0 started.
tgrimley@tgrimley-virtual:~$ sudo mount /dev/md0 md0mount/
tgrimley@tgrimley-virtual:~$ ls md0mount/
lost+found  testfile
tgrimley@tgrimley-virtual:~$ cd md0mount/
tgrimley@tgrimley-virtual:~/md0mount$ cat testfile 
tesssssssssst
```

---

