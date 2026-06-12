---
title: "fsck'd up (corrupt superblock or partition?)"
date: 2007-09-21
forum: Hardware &amp; Laptops
---

### Post by ender42 on 2007-09-21
So I've got some issues with some partitions on my data drive:

[I]root@machine:~ # fsck /dev/hdb2 fsck 1.38 (30-Jun-2005)
e2fsck 1.38 (30-Jun-2005)
Couldn't find ext2 superblock, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/hdb2

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

root@machine: dumpe2fs /dev/hdb2 >> /dev/hdb1/datafile
dumpe2fs 1.38 (30-Jun-2005)
dumpe2fs: Bad magic number in super-block while trying to open /dev/hdb2

root@machine:~ # fsck /dev/hdb3
fsck 1.38 (30-Jun-2005)
e2fsck 1.38 (30-Jun-2005)
The filesystem size (according to the superblock) is 2441494 blocks
The physical size of the device is 2198896 blocks
Either the superblock or the partition table is likely to be corrupt!

root@machine: dumpe2fs /dev/hdb3 >> /dev/hdb1/datafile
dumpe2fs 1.38 (30-Jun-2005)

root@machine:~ # fsck /dev/hdb4
fsck 1.38 (30-Jun-2005)
e2fsck 1.38 (30-Jun-2005)
Couldn't find ext2 superblock, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/hdb4

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

root@machine: e2fsck -b 8193 /dev/hdb4
e2fsck 1.38 (30-Jun-2005)
e2fsck: Bad magic number in super-block while trying to open /dev/hdb4

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

root@machine: dumpe2fs /dev/hdb4 >> /dev/hdb1/datafile
dumpe2fs 1.38 (30-Jun-2005)
dumpe2fs: Bad magic number in super-block while trying to open /dev/hdb4
[/I]


How can I check that I put a filesystem on those partitions?  I'm not sure I did so after partitioning.

What else can I check (or how I can check stuff?), and any ideas on fixing stuff?

/dev/hdb3 is particularly worrying, any thoughts on that?

---

### Post by dcstar on 2007-09-21
> **ender42 said:**
> So I've got some issues with some partitions on my data drive:
..........
How can I check that I put a filesystem on those partitions?  I'm not sure I did so after partitioning.

What else can I check (or how I can check stuff?), and any ideas on fixing stuff?

/dev/hdb3 is particularly worrying, any thoughts on that?

You may not have yet partitioned them (or at least formatted them), that could be why fsck is having so much trouble.

Install gparted and check what is on the disk with that.

---

### Post by ender42 on 2007-09-22
I'm installing gparted (along wtih suggested: hfsutils ntfsprogs ), right now.  Is there a way to check stuff with the command-line?  If I were to be operating on a computer at a distance?

---

### Post by ender42 on 2007-09-22
gparted (Gnome Partition Editor in System) is nice and GUIffied.

It says that 2,3 & 4 are unknown, and thus I'm guessing that I didn't put a filesystem on them after partitioning.

I'm looking thru my notes, and not finding the commands I used to put in the filesystem on hdb1.  I'm sure this is covered somewhere in a help note, but I'm out of time right this instant (I'll come back and keep looking, so no biggie if you don't want to answer this one) - HAH: makefs, d'uh, came to me when I was running errands. Heh, if I could remember correctly: mke2fs



What's up with hdb3?  gparted shows no errors or anything.



How do I put a filesystem on my partitions. (I think I could find this information) --> mke2fs


How can I backup, or make more robust superblocks (in case of corruption?) - I see something called 'sparse superblocks', which is the opposite? of what I need?  I'm assuming that happens during the filesystem creation, since fsck is choking on the ones without filesystems...

I'm thinking of resizing hdb3 to give it more space (it's the backup area where I'd install linux on this drive, if needed - ie: if my hda fails), and I also (now) realize that I need to make a swap partition on hdb as well.  Both of these would be coming out of the spare un-used space on hdb1... I'm also assuming I can do that without losing data on hdb1.  But, I'm worried about the errors shown for hdb3's size...

---

