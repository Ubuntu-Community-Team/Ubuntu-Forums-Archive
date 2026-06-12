---
title: "[SOLVED] Fsck interrupts bootup though nothing is wrong"
date: 2008-03-17
forum: Hardware &amp; Laptops
---

### Post by purplecow on 2008-03-17
It started when I formatted and repartitioned one of my hard disks from two ext3 ones to one large FAT32 drive.
Now every time I boot up, fsck comes up and starts to check things, then fails doing something, it doesn't really tell me what's going on.
It brings up a maintenance console where I can just press Ctrl+D and the system boots up nicely after that. As far as I can tell, there is nothing wrong with any of my partitions. 
No data gets lost or corrupted, but apparently there is some problem and I have no idea how to fix it.

Here's the log file from /var/log/fsck:
```

Log of fsck -C -R -A -a 
Mon Mar 17 08:03:15 2008

fsck 1.40.2 (12-Jul-2007)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
There are differences between boot sector and its backup.
Differences: (offset:original/backup)
  71:4d/00, 72:41/00, 73:54/00, 74:4b/00, 75:41/00, 76:20/00, 77:20/00
  , 78:20/00, 79:20/00, 80:20/00, 81:20/00
  Not automatically fixing this.
/dev/hdb1: 16730 files, 667530/1318691 clusters
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/hdb5: 73199 files, 1986152/2990627 clusters
/dev/hdb6: clean, 46/6033888 files, 1626953/12064807 blocks
/dev/hda2: clean, 43/22176 files, 52450/88356 blocks
Replaying journal..
Reiserfs journal '/dev/hda6' in blocks [18..8211]: 0 transactions replayed
Checking internal tree..finished
Reiserfs super block in block 16 on 0x306 of format 3.6 with standard journal
Blocks (total/free): 24019168/1399338 by 4096 bytes
Filesystem is clean
fsck.ext3: Unable to resolve 'UUID=2915d85e-69a3-484d-b39f-dc75e8a45765'

fsck.ext3: Unable to resolve 'UUID=84716069-b02e-4d2d-b16a-f82f84454757'

Reiserfs super block in block 16 on 0x306 of format 3.6 with standard journal
Blocks (total/free): 24019168/1399338 by 4096 bytes
Filesystem is clean
fsck died with exit status 8

Mon Mar 17 08:04:13 2008
----------------

```

---

### Post by erginemr on 2008-03-17
Regarding at the message:
```
fsck.ext3: Unable to resolve 'UUID=2915d85e-69a3-484d-b39f-dc75e8a45765'
fsck.ext3: Unable to resolve 'UUID=84716069-b02e-4d2d-b16a-f82f84454757'
```

I am suspecting that there might be a wrong UUID setting in your /etc/fstab file. Can you please post the result of the following commands from the terminal:

```
cat /etc/fstab
```
```
blkid
```
```
sudo fdisk -l
```

---

### Post by justsomedude on 2008-03-17
Your sytem doesn't know the filesystem has changed, it thinks your fat partition are two totally corrupted ext3 partitions. Thus it gives you a root prompt in read only mode to backup your data.

Boot from a live CD and mount your root partition. Find your /etc/fstab on this partition, open it with admin rights  and uncomment the two ext3 partitions (the ones that are now your fat partition).

Then you will be able to boot normally and can create a new mount point and fstab entry for your newly created partition.

Do you need a more detailed description?

---

### Post by purplecow on 2008-03-17
Thanks both of you.
I looked at my fstab and there were two lines about the ext3-partitions that were now gone. 
I commented them out and now it's not confused anymore.

---

### Post by erginemr on 2008-03-17
You are welcome. Take care. :D

On a final note:
**To close a thread **-> Select **"mark this thread as solved"** from the thread tools menu. 
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

