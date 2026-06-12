---
title: "e2fsck broke my 'md' partitions!"
date: 2007-07-30
forum: Hardware &amp; Laptops
---

### Post by bsmith1051 on 2007-07-30
I had a working setup of Ubuntu 7.04 with two SATA2 drives setup as /sda and /sdb with matching ext3 root partitions and setup as a RAID-1 mirror called /md0. Long story short, I installed another drive and got an error message about invalid partition, unable to run fsck. But then it would allow me to continue boot-up? Eventually I figured-out that I'd made a typo in adding the new drive to /etc/fstab and then the error message went away. But in the meantime I'd discovered that fdisk reported "Disk /dev/md0 doesn't contain a valid partition table." I actually posted about this on the forums,
[http://ubuntuforums.org/showthread.php?t=512154](http://ubuntuforums.org/showthread.php?t=512154)

Then I was experimenting with the latest Gutsy/Tribe-3 LiveCD and saw the new Partition Editor. It had a seemingly nice easy "Check partition" feature so I naively tried it. It showed the command-line as some long command-line for e2fsck. When I ran it on /sda it found no errors BUT then also said it was resizing the partition. I figured I had to make sure that both partitions were identical so I ran it on /sdb, too.

Now the machine won't boot! I'm getting the same error message re invalid partitions but now I can't skip past it -- it's for real! fsck reports that the partition size (according to the superblock?) is larger than the actual partition. Or something like that; I know, I need to get the exact message but I'm not at the machine right now.

So it appears that e2fsck made an unnecessary change to my md0 partition. Help!

---

### Post by bsmith1051 on 2007-08-01
Here's more detail:

the new Partition Editor appears to have run the following commands:
```
e2fsck -f -y -v /dev/sda1
resize2fs
```
The resize command then output, "size changed to 2441872 blocks"

Now, when I boot, Ubuntu reports:
```
/dev/md0: unexpectedly inconsistency
fsck exit status 4
filesystem according to superblock is 2441872 blocks
physical size of device is 2441856 blocks
```
I now understand that the difference, 64 blocks, is the 'md' superblock which apparently resize2fs doesn't recognize.   So maybe this is a bug in resize2fs?  Obviously it's also a 'bug' in my understanding of how md devices work, but I assumed that something as important as Partition Editor 'Check' wouldn't damage anything.

As an experiment (and because I've done so well --not-- with my experimenting so far) I tried running what seemed like the reverse of I thought had happened:
```
resize2fs /dev/sda1 2441856
```
but then Ubuntu *really* wouldn't boot!  I re-ran it with the larger block count and I seem to be back to original fsck error.

Another bit of info -- when I try to boot the hard drives and get the fsck error, then the recovery console, I can run 'mdadm' and it reports everything is fine, even that the "Superblock is consistent."  So I really don't understand where the error is, after all...

---

### Post by bsmith1051 on 2007-08-02
**SOLUTION**
There's clearly a bug in some of the code _somewhere_.  Either the new Partition Editor (in Gutsy) or e2fsck or resize2fs has the code for 'md' partitions **BACKWARDS**.  Instead of excluding the 16 blocks at the end of the partition (where the md-superblock resides) they 'included' it.

In other words:
- actual size of my 'md' partitions = 2,441,840 blocks
- actual size of my 'md' drive = 2,441,856 blocks
- size that it got resize'd to = 2,441,872 blocks

So the solution, fortunately, was simply to boot the LiveCD again and manually run the _correct_ 'resize2fs' command,
```
resize2fs /dev/sda1 2441840
resize2fs /dev/sdb1 2441840
```
I then rebooted and everything appears to be working perfectly!  So, at the very least, the resize command didn't damage anything ... it just made it mysteriously unbootable!

---

