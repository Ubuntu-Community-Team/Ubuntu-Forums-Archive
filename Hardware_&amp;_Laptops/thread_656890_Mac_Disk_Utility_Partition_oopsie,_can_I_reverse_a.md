---
title: "Mac Disk Utility Partition oopsie, can I reverse a reformat?"
date: 2008-01-03
forum: Hardware &amp; Laptops
---

### Post by Luminous on 2008-01-03
So I was trying to install OSX86 on my dell laptop, the one I had Ubuntu on as the main OS, and looks like when I tried to get a bootable partition out of disk utility in the install process, I reformatted the Ubuntu/swap partitions! :(

I have a 90 or so gig hard drive that I dedicated to Ubuntu, so about 3 gigs of it is swap, the rest is ext2.
so I boot up the gparted livecd in order to prep a partition for the mac space to use, and resize the ubuntu partition to about 55 gigs, great everything still works fine. I leave the rest as empty space (bad idea). I boot up the OSX86 disc and get to the Disc utility. Now heres where it gets interesting. I try to make a new partition on the empty space... but Mac doesn't like that, so no go on that, and after messing around with some settings, it looks like I have it where I want it, 3 partitions, the Mac journaled partition, and my other 2 ubuntu partitions, not thinking too hard about what I was doing, I failed to notice that disc utility had magically replaced the ext2 options under the two ubuntu partitions... with fat32! OH NO! too late, reformatted. but the reformatting tool seems to have taken little to no time to reformat this drive, so heres my question;

It looks like the disc utility didn't change the size of hte partitions, only the format they were in, is this just a disc header, as in the data is still there and recoverable? and if it is, any way I can do this the linux way? I looked up some live cd's "system restore CD" and "Ultimate boot CD" and tried skimming through those. Problem is, I'm not really sure what I'm looking for. I know I need to repair both the partition table and MBR to fix this. 

Can I just use Gparted again and reset the filesystem types to their originals? or is most hope lost beyond a corporate data recovery business? I have a friend that has some magnetic scanheads so its not like the data's completely gone. But that would take time and effort on both our parts that I hope would not be needed. Any info is appreciated!

---

### Post by karl_kashofer on 2008-01-03
Hi !

This sucks, i hate the feeling when the hair in your neck stand up when you see something like that... I feel with you...

Anyway, here are my 2c

First I would try to make a complete copy of the partitions in question. I would think it should be possible to boot from a live cd and then mount the partitions read-only and copy them to somewhere else with dd. This would give you a working copy to play around with.

Then I think it could be possible to do something like change the filesystem type with cfdisk or fdisk and after that do a repair of the filesystem with ext2 tools. Are you sure it was ext2 and not ext3 ? From my limited knowledge of ext2 i think it keeps a different kind of record of file names than fat32 so you might well be able to recover the file tables from a safety copy in the middle of the disk that was not damaged by the fat32 format. I seem to remember that there is some kind of redundancy in ext2. I also believe there is more hope for ext3, as it has the journal which could also aid in reconstruction.

I hope you can copy the thing with dd so you have a chance to play around. Dont mess with the original partition until you really know what to do. :)

Heads up, not all is lost, 
I hope you get your data back,
Cheers,
Karl

---

