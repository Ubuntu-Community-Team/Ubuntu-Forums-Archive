---
title: "hdd/fsck problems"
date: 2007-04-24
forum: Hardware &amp; Laptops
---

### Post by fethry on 2007-04-24
I had formatted & mounted my new hdd (Seagate Barracuda, 200GB, ATA, 8MB cash) a few days ago. It worked properly until Sunday, when the 100G partition on ext3 started to make problems. I can't access it, neither can recover it. fsck says:

fsck /dev/hdb1
fsck 1.39 (29-May-2006)
e2fsck 1.39 (29-May-2006)
Group descriptors look bad... trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/hdb1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

But I can't understand how to change the superblock. Please help me, if you can.:confused: :confused:

---

### Post by Rob on 2007-04-24
I had a similar problem last night, and hence found your post looking for a solution.

Starting at fsck on wikipedia, then following a link at the bottom to [[COLOR="Blue"]here[/COLOR]]("http://adminschoice.com/docs/fsck.htm") I've read that something like the following command can be used to find the super blocks.  The -N option is rather important, as without it I think the newfs command could erase your disk (hopefully it would ask first?):

```
newfs -N /dev/hdb1
```

It also suggests the first alternate superblock is usually 32, although the command above should provide a list of the alternate superblock locations, if I understand it correctly. If 32 is the first one you would try:

```
fsck -b 32 /dev/hdb1
```

If that doesn't work, try one of the other alternate superblock locations and hope everything gets fixed.

I would guess that messing about with fsck should be relatively safe - it is for repairing filesystems. However, you might want to wait for someone more knowledgeable to provide a more informed reply, particularly if you've got data you don't want to lose.

Rob.

---

### Post by sudo_nym on 2007-04-24
[_Underlines_ by me, to point something out...]

> **fethry said:**
> I had formatted & mounted my new hdd (Seagate Barracuda, 200GB, ATA, 8MB cash) a few days ago. It worked properly until Sunday, when the 100G partition on _ext3_ started to make problems.
[...]
_fsck.ext2_: Bad magic number in super-block while trying to open /dev/hdb1

Well, if you're sure it's an ext3 partition, why does fsck think it's ext2?  Maybe you can try invoking; *fsck.ext3 /dev/hdb1* directly, and see if that works.

On the other hand, if fsck's that confused about your partition, maybe something went wrong when it was formatted.  If you don't have anyhting valuable on that partition yet, what about just formatting it again [but only that partition, not the whole disk], and see if things turn out okay?


Wish you luck,

Patrick.

---

### Post by Rob on 2007-04-24
Remember that ext3 file systems are just ext2 with a few extras. [[COLOR="Blue"]This page explains it better[/COLOR]]("http://en.wikipedia.org/wiki/Ext3").

I wouldn't be surprised if fsck is just calling it ext2 because that's what fsck was originally written for, but it works just as well for ext3.

---

### Post by julv on 2007-04-24
ext3 is indeed ext2 file system with a journaling feature, so the call is ok.

I've had the same problem last night too on the partition mapped to my /home folder. 
I restarted with the live cd and tried to fsck the partition, without success. the other partition of the hard drive is screwed too. 
This is a rather old drive, so i guess this is indeed due to a hardware failure, but i'm puzzled that gparted still sees correctly the drive and the associated partitions...
If anybody has an explanation, i'd be glad not to have to try to reformat the drive (and throw it away if it is really related to it's old age...).
Btw, anybody knows how to recreate a /home partition from scratch without reinstalling (not importing it from somewhere else either...)

---

### Post by fethry on 2007-04-25
> **sudo_nym said:**
> [_Underlines_ by me, to point something out...]
On the other hand, if fsck's that confused about your partition, maybe something went wrong when it was formatted.  If you don't have anyhting valuable on that partition yet, what about just formatting it again [but only that partition, not the whole disk], and see if things turn out okay?


That's what I decided to do.  I reformatted it using the Ubuntu installer partiotioner. I used the default options. Is there a better and more secure way to format it?

---

### Post by fethry on 2007-04-28
I've got problems again!;'-(
After I reformatted the same partition, fsck says:[PHP]
Resize inode not valid.  Recreate<y>? no

Backing up journal inode block information.

/dev/hdb1 contains a file system with errors, check forced.
fsck.ext3: Illegal triply indirect block found while reading bad blocks inode
This doesn't bode well, but we'll try to go on...
Pass 1: Checking inodes, blocks, and sizes
Bad block inode has illegal block(s).  Clear<y>? 
[/PHP]
How can I format it properly?
Please, help!

---

