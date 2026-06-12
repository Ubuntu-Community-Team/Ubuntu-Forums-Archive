---
title: "Lacie 1TB External HDD (ext4) not readable"
date: 2014-05-03
forum: Hardware
---

### Post by cruising on 2014-05-03
Hi!

I'm having issues with my Lacie 1TB rugged external hard drive, where I can't read from it. I've tried several options to correct the file system error, but none seem to work so far. 

Here's a result of my last attempt:

```

sudo mkfs.ext4 -S /dev/sdc
mke2fs 1.42.9 (4-Feb-2014)
/dev/sdc is entire device, not just one partition!
Proceed anyway? (y,n) y
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
61054976 inodes, 244189952 blocks
12209497 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=0
7453 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks: 
	32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
	4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968, 
	102400000, 214990848

Allocating group tables: done                            
Skipping journal creation in super-only mode
Writing superblocks and filesystem accounting information: done



```

I have a lot of photos, videos, documents, etc on it. 

How can I recover the files? I feel like creating a new partitioning table should help. But, gparted has a big warning that if you do that it will ERASE ALL DATA on drive. 

Help, please!

Thank you!!

---

### Post by oldfred on 2014-05-03
You are the third or 4th user with formatted drives. I have not seen a solution yet.

You create & format partitions on a drive. When you format a drive, you create a superfloppy type configuration that does not have space for a partition table. You may have data in the space used by a partition table and first partition table in all formatted drives now starts at sector 2048, you may have data in those first 2048 sectors.

Most have just copied data to another drive and created partitions after the fact.

---

