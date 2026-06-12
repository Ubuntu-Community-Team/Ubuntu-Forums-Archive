---
title: "Some bad sectors on a hard drive, what to do?"
date: 2010-07-11
forum: Hardware
---

### Post by Rumtscho on 2010-07-11
I noticed that on one of my hard drives, there are some bad sectors. The drive is new (less than a year old, no heavy use). It is external, so the reason may be physical damage. 

I've seen storage devices "lose" bad sectors after a (deep) format, so I thought I'll first format the thing and see what happens from there on. But I cannot even format it. Disk utility gives me some strange errors (device is busy hwatever I try to do). fdisk can create a partition table, but mkfs.ext3 hangs at inode 387. So I now cannot even format the thing. 

I don't want to throw away the whole drive. I'd like to somehow make a partition which doesn't include the damaged sectors. I am currently trying to run mkfs.ext3 with the -c option (only once, so this is the "quick" test), and it looks like it will take more than 12 days (!!!) and I don't know if it will actually leave out the found bad sectors when doing the format. 

I would wait the 12 days if after that I can have a normal non-damaged partition on the drive. But if someone has a better idea, please tell me!

```
rumtscho@bradbury:~$ sudo mkfs.ext3 -c /dev/sdb1
mke2fs 1.41.11 (14-Mar-2010)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
61054976 inodes, 244189752 blocks
12209487 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=4294967296
7453 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks: 
	32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
	4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968, 
	102400000, 214990848

Checking for bad blocks (read-only test):   0.09% done, 13:10 elapsed

```

I am attaching the Disk Utility report for the SMART Data. The first item, Read Error Rate, didn't fit on the screenshot, but the assessment was "Good".

Edit: The forum software scaled my screenshot down, please view the archive instead.

---

