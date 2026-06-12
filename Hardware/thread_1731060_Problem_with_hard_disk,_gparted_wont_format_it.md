---
title: "Problem with hard disk, gparted wont format it"
date: 2011-04-16
forum: Hardware
---

### Post by velja27 on 2011-04-16
Well i have this hard disk of 500GB that all of a sudden had gotten into a read only mode. And each time i tried to put something on it it would get stuck after only 200MB's of transfer. And i got tired of it and i just wanted to format it so it would all be ok, but then i tried to do that and Gparted gave me an error(and its in the code tag below).
By the way, thanks up front for any help it will be much appreciated.
Also, if this is wrong sub-forum I would like to ask moderators to put it in its right place.
```
GParted 0.4.5

Libparted 1.8.8.1.159-1e0e
Delete /dev/sda1 (unknown, 465.76 GiB) from /dev/sda  00:00:01    ( SUCCESS )
     	
calibrate /dev/sda1  00:00:00    ( SUCCESS )
     	
path: /dev/sda1
start: 63
end: 976768064
size: 976768002 (465.76 GiB)
delete partition  00:00:01    ( SUCCESS )

========================================
Create Primary Partition #1 (ext4, 465.76 GiB) on /dev/sda  00:02:53    ( ERROR )
     	
create empty partition  00:00:01    ( SUCCESS )
     	
path: /dev/sda1
start: 63
end: 976768064
size: 976768002 (465.76 GiB)
set partition type on /dev/sda1  00:00:01    ( SUCCESS )
     	
new partition type: ext4
create new ext4 file system  00:02:51    ( ERROR )
     	
mkfs.ext4 -j -O extent -L "" /dev/sda1
     	
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
30531584 inodes, 122096000 blocks
6104800 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=0
3727 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks:
32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208,
4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968,
102400000

Writing inode tables: done
mke2fs 1.41.9 (22-Aug-2009)
ext2fs_mkdir: Attempt to read block from filesystem resulted in short read while creating root dir

========================================
```

---

### Post by velja27 on 2011-04-17
So nobody knows a solution to this problem eh?
Bump.

---

### Post by lisati on 2011-04-17
Is the disk mounted?

---

### Post by Rubi1200 on 2011-04-17
This link might also prove to be useful:
[http://ubuntuforums.org/showpost.php?p=6373612&postcount=5](http://ubuntuforums.org/showpost.php?p=6373612&postcount=5)

> GParted 0.4.5
You should also consider a more recent version of GParted:
[http://distrowatch.com/table.php?distribution=gparted](http://distrowatch.com/table.php?distribution=gparted)

---

### Post by velja27 on 2011-04-18
Disc of course wasn't mounted. And I've tried that post Rubi1200, but thanks.

I've just managed to fix it. I changed the port to which HDD was plugged in to and changed the cable with which it was connected. And then ran an extensive test on Disk Utility, formated it via Disk Utility then got into Live CD and reformated it(with Gparted 0.4.5) again cause the OS(installed one) couldn't register it on boot.
I will boot into my OS and see how it works there, will post the results.

---

### Post by Rubi1200 on 2011-04-19
Okay, I am glad you managed to make some progress.

Let me know if there is anything else you need help with.

---

