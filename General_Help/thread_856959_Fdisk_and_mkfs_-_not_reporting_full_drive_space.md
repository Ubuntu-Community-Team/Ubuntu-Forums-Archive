---
title: "Fdisk and mkfs - not reporting full drive space"
date: 2008-07-12
forum: General Help
---

### Post by drhiii on 2008-07-12
Hello,

I installed Ubuntu server edition several months ago on a dual drive system.  A few days ago decided I wanted to flatten and rebuilt the second drive, /dev/sdb  

I fdisk'd then mkfs.ext3'd the drive. Fdisk reported the correct size.  Everything went swimmingly.  However, when I mounted the dirve, it showed approx 1/3rd of the drive was used.  Has me totally stumped because nothing in the fdisk to remove the partitions, then mkfs which formatted all the way... nothing appeared unusual.

Thoughts on why a freshly fdisk'd and mkfs'd drive would report used space?  I've added slices of output from the exercise which I have done several times now, to no avail as it is reporting used drives space right after a full fdisk and format.

tx


Info:

fdisk - 

Command (m for help): p

Disk /dev/sdb: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c88f6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       48640   390700768+  83  Linux

Command (m for help): d
Selected partition 1

Command (m for help): p

Disk /dev/sdb: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c88f6

   Device Boot      Start         End      Blocks   Id  System

Command (m for help): n
Command action
   e   extended
   p   primary partition (1-4)
p
Partition number (1-4): 1
First cylinder (1-48641, default 1): 1
Last cylinder or +size or +sizeM or +sizeK (1-48641, default 48641): 
Using default value 48641

Command (m for help): p

Disk /dev/sdb: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c88f6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       48641   390708801   83  Linux

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.
Syncing disks.



Now mkfs - 

root@tpl:/etc# mkfs.ext3 -b 4096 /dev/sdb1
mke2fs 1.40.2 (12-Jul-2007)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
48840704 inodes, 97677200 blocks
4883860 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=0
2981 block groups
32768 blocks per group, 32768 fragments per group
16384 inodes per group
Superblock backups stored on blocks: 
	32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
	4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968

Writing inode tables: done                            
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 23 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to override.


Now what it reports on /dev/sdb1 which is used space, this after a fresh fdisk and mkfs!!!

root@tpl:/etc# mount -t ext3 /dev/sdb1 /media/sdb
root@tpl:/etc# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             357G  274G   65G  81% /
varrun                2.0G   92K  2.0G   1% /var/run
varlock               2.0G     0  2.0G   0% /var/lock
udev                  2.0G  140K  2.0G   1% /dev
devshm                2.0G     0  2.0G   0% /dev/shm

/dev/sdb1             367G  195M  348G   1% /media/sdb

---

### Post by dcstar on 2008-07-12
> **drhiii said:**
> Hello,

I installed Ubuntu server edition several months ago on a dual drive system.  A few days ago decided I wanted to flatten and rebuilt the second drive, /dev/sdb  
........
Now what it reports on /dev/sdb1 which is used space, this after a fresh fdisk and mkfs!!!

root@tpl:/etc# mount -t ext3 /dev/sdb1 /media/sdb
root@tpl:/etc# df -h
```
Filesystem            Size  Used **Avail Use%** Mounted on
/dev/sda1             357G  274G   65G  81% /
varrun                2.0G   92K  2.0G   1% /var/run
varlock               2.0G     0  2.0G   0% /var/lock
udev                  2.0G  140K  2.0G   1% /dev
devshm                2.0G     0  2.0G   0% /dev/shm

**/dev/sdb1**             367G  195M  **348G   1%** /media/sdb
```

So /dev/sdb1 has 1% used - which is the EXT3 journal - and 384G available, what is the problem again?

---

### Post by drhiii on 2008-07-13
Oh boy.  I cannot believe I cannot read, and interpret.  Bonehead post of the month here.  I have as you say, NO problem.  Other than not reading what's on the screen.  

I will retreat to my rsync commands with my tail between my legs.  Honestly, I do not know what I was thinkng....   point being, I wasn't.  

tx


> **dcstar said:**
> So /dev/sdb1 has 1% used - which is the EXT3 journal - and 384G available, what is the problem again?

---

### Post by dcstar on 2008-07-13
> **drhiii said:**
> 
......
I will retreat to my rsync commands with my tail between my legs.  

After you mark this thread as solved, of course.....

---

