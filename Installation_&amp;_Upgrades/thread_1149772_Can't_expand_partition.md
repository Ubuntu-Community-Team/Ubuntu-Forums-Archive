---
title: "Can't expand partition?"
date: 2009-05-05
forum: Installation &amp; Upgrades
---

### Post by Roasted on 2009-05-05
I have a FOG imaging server set up. I had it set up on an 80gb drive but I quickly filled it with a series of 2-5gb images that I use for all of the computers at work. I got a hold of a 160gb drive and copied it to the 80. The problem is now, I have 80gb of space left over. I want to grow my main ext3 partition to utilize the 80gb of left over space yet - I can't.

I'm booted up to an Ubuntu 9.04 LiveCD right now and I'm looking at GParted from within that LiveCD. I cannot grow the partition whatsoever to suck up the remaining 80gb...

How on earth am I doing anything wrong?

---

### Post by dstew on 2009-05-05
Is the 80 gb partition unmounted? Is the remaining space unallocated?

---

### Post by Roasted on 2009-05-05
Yes, everything is unmounted. I've tried using GParted LiveCD along with the Ubuntu LiveCD.

The additional space is unallocated. I've also tried to format it as ext2, ext3, and I also created a blank partition with no file system on it. Every option didn't work.

I have a feeling it's because of the fact it's an extended partition.

I have a 2nd drive in the computer with the images backed up on, so I'm just going to format it since all I use this computer for is to image computers. It's simple enough to re-format it in this particular instance.

Still peeves me though...

---

### Post by dstew on 2009-05-05
One thought. As I understand, an *_extended_* partition is only a container for one or more *_logical_* partitions. Are trying to expand a logical partition? If so, maybe you need to expand the container (extended) partition first.

---

