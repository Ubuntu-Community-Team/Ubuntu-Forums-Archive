---
title: "Hard Drive Help"
date: 2010-10-13
forum: Hardware
---

### Post by vampist on 2010-10-13
I am having a really bad week... First my windows OS on my laptop goes out (had to reinstall), now my server goes out...

And to top it off.. (here is my problem) My backup harddrive? Is saying it's all unallocated space. I love my life, I love my life, I love my life...

Power went out, server must have been doing something important of some sort... wouldn't even load grub. Grub rescue came up, I attempted to type any command I could think of. Everything gave me "unrecognized command" even help, h, ?, --help anything.


I got my trusty 9.10 usb stick over and reinstalled on my 40GB HDD. clearing the whole harddrive.
I have a backup HDD that is 500GB, I have been backing up with Sbackup.

When looking at it under unbutu, It says "unallocated".

If I run fsck /dev/sdb1, I get

fsck from util-linux-ng 2.16
e2fsck 1.41.9 (22-aug-2009)
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sdb1

The superblock could not be read or does not describe a correct ext2 filesystem. If the device is valid and it really contains an ext2 filesystem (and not swap or ufs or something else), then the super block is corrupt, and you might try running e2fsck whith an alternate superblock: e2fsck -b 8193 <device>

---

### Post by srs5694 on 2010-10-13
The fact that you've got a /dev/sdb1 means that the disk is not "unallocated" (unpartitioned). Before you do anything else with fsck, I recommend you check [this page,](http://www.rodsbooks.com/missing-parts/) which describes the symptoms you're seeing and some possible solutions. If you need more help, please post back with the output of "sudo fdisk -lu". Please post the output between a [noparse]```
[/noparse] string and a [noparse]
```[/noparse] string for legibility.

That said, the fact that fsck is reporting problems with the superblock suggests the filesystem may have very serious problems. (OTOH, maybe you're trying to check a non-filesystem partition or something.) Still, it's best to resolve the problem with the partitions before tacking the filesystem problem -- doing it the other way around could actually make matters worse, depending on what the problems really are.

---

### Post by vampist on 2010-10-13
I did fdisk -lu /dev/sdb1 on the account that I am typing everything from the screen because my startx won't boot... 
(some update problem... I will deal with this later. I got this problem when updating the system, in an attempt that maybe it was a old file or something that was giving me an unallocated disk. so they are totally separate)


fdisk -lu /dev/sdb1 output: 

Disk /dev/sdb1: 500.1GB, 500105217024 bytes
255 heads, 63 sectors/track, 60800 cylinders, total 976768002 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk Identifies: 0x5f2a07fe

Device boot Start End Blocks Id System


EDIT:
That link didn't really help much. sfdisk -d /dev/sdb1 --force > part.txt cat part.txt shows all the info with zeros

EDIT2:
Okay, Fixed the gnome issue.. It was some weird issue with gnome-power-manager
But that is done. Now for the real problem.. The hard drive. Anyone have any ideas?

---

### Post by srs5694 on 2010-10-13
Don't use fdisk on /dev/sdb1; use it on /dev/sdb, or better yet, on nothing at all (it'll scan all partitions), thus:

```

sudo fdisk -lu

```/dev/sda, /dev/sdb, and so on are hard disks. Add a number (/dev/sda1, /dev/sdb1, /dev/sdb2, etc.), and the file refers to a single partition. You use very different utilities on disks than you do on partitions!

Oh, and *please* post your output between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings for legibility! This will preserve the columnar output of fdisk. Without it, everything blurs together and my eyes go cross-eyed!

---

