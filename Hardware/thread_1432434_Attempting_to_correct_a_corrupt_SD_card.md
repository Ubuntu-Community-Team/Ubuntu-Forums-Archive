---
title: "Attempting to correct a corrupt SD card"
date: 2010-03-17
forum: Hardware
---

### Post by Magic Midget on 2010-03-17
The problem is with the SD card on my BlackBerry: it gives me a message saying it's corrupt etc and needs to have a disk error check run on it.

I did a bit of digging, and got to some kind of answer, but I guess I'm only halfway there. I had to do this as part of the solution:

```
sudo fsck -a /media/disk
```And I was greeted with:

```
fsck 1.41.4 (27-Jan-2009)
fsck.ext2: Is a directory while trying to open /media/disk
/media/disk: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device&gt;

```This just has me lost. Anyone care to help? This is not my territory with computers.

---

### Post by quixote on 2010-03-19
Fsck and e2fsck only work on linux / unix type of filesystems (ext2, ext3, ext4, probably reiserfs, etc).  Most SD cards are formatted using a DOS filesystem: vfat, usually vfat16 I believe.  (There's also vfat32.)  So you need to use different tools.

One time when I blew up an SDcard I had good luck with [testdisk]("http://www.howtoforge.com/data_recovery_with_testdisk").  It's a rather ugly, text-based, command line and old school program, but it seems to work better than anything else I've heard of out there. Because it's command line, there's a bit of a learning curve.

Another set of [testdisk instructions]("http://www.debian-administration.org/articles/420") are debian-based.  If the files on the SDcard are not absolutely vital, I'd skip steps 1 and 2 (backing up the bad card).  If you need or want to do steps 1 and 2, remember that when writing from a whole device to another one -- which is what the "dd" family of commands do -- *they will destroy any data or partitions on the second device*, the one you're writing *to*.  Also, the instructions don't prepend "sudo" to the commands, but on an ubuntu system you would need to.

[Wikipedia]("http://en.wikipedia.org/wiki/TestDisk") has a simple overview and a whole bunch of links.

hth.

---

