---
title: "New hard drive with 7.53GB used? (already used tune2fs)"
date: 2008-09-28
forum: General Help
---

### Post by rkudeshi on 2008-09-28
Hi,

I've installed 4 new 1TB hard drives in my computer and formatted them with ext3.  GParted reports total capacity as 931.51 GB, but shows 7.53 of that already being used!

Note that this is after I used tune2fs to remove the space reserved for root as these drives will be used for storage only (in a software RAID5).

I've never used Linux/Ubuntu before, but I have to say this is a first for me -- a freshly formatted hard drive already having space used?

I understand ext3 is a "journaling" file system (which I don't quite understand), but formatting with ext2 showed almost the same amount of space being used.

Any ideas? Thanks!

(Sorry if it seems like only a relatively small amount of space, but over all 4 drives, it adds up to more than 30GB of otherwise-useable space)

---

### Post by Excalibre on 2008-09-29
> **rkudeshi said:**
> Hi,

I've installed 4 new 1TB hard drives in my computer and formatted them with ext3.  GParted reports total capacity as 931.51 GB, but shows 7.53 of that already being used!

Note that this is after I used tune2fs to remove the space reserved for root as these drives will be used for storage only (in a software RAID5).

I've never used Linux/Ubuntu before, but I have to say this is a first for me -- a freshly formatted hard drive already having space used?

I understand ext3 is a "journaling" file system (which I don't quite understand), but formatting with ext2 showed almost the same amount of space being used.

Any ideas? Thanks!

(Sorry if it seems like only a relatively small amount of space, but over all 4 drives, it adds up to more than 30GB of otherwise-useable space)
I just got a new 1 TB external hard drive and had exactly the same figure show up as used. I suspect it's because there's a certain amount of overhead for the file system that's allocated in advance. There has to be other stuff on the disk besides your data itself -- in essence, a table of contents that allows the computer to know where to look for particular files. I think that's where those 7.53 gigs went.

---

### Post by Bakon Jarser on 2008-09-29
[http://en.wikipedia.org/wiki/Gigabyte#Consumer_confusion](http://en.wikipedia.org/wiki/Gigabyte#Consumer_confusion)

---

### Post by rkudeshi on 2008-09-29
> **Bakon Jarser said:**
> [http://en.wikipedia.org/wiki/Gigabyte#Consumer_confusion](http://en.wikipedia.org/wiki/Gigabyte#Consumer_confusion)

Thanks for the reply, but I already took this into consideration: the drive reports as having a capacity of 931.51 GB, which is fine -- I just want to know why it says 7.53 GB of that has already been used.

As for file system overhead -- formatting with NTFS reports very little space used.  I thought it was the journaling feature of ext3, but ext2 (which I don't think supports journaling) reports almost as much space as ext3 used.

Any other ideas?

---

### Post by Excalibre on 2008-09-30
> **Bakon Jarser said:**
> [http://en.wikipedia.org/wiki/Gigabyte#Consumer_confusion](http://en.wikipedia.org/wiki/Gigabyte#Consumer_confusion)
Right, this has nothing to do with the issue in question. Work out the math, first of all -- a 1 terabyte hard drive, 1*10^14 bytes, works out to 931 gibibytes (that's the technical term) or 0.909 tebibytes. That's a lot bigger difference than the 7.5ish gibibytes in question, and besides, that missing space doesn't show up as "used" when you plug the hard drive in. It's just not there. When I plugged in this 1 terabyte drive, Ubuntu told me it had 931 gibibytes of storage, which is exactly what should be expected.

---

### Post by Excalibre on 2008-09-30
> **rkudeshi said:**
> As for file system overhead -- formatting with NTFS reports very little space used.  I thought it was the journaling feature of ext3, but ext2 (which I don't think supports journaling) reports almost as much space as ext3 used.

Any other ideas?
It's well possible that one file system has more overhead than another. NTFS is a generally less sophisticated file system than ext3, it might well store less metadata describing the file system. The journals shouldn't be significant when you first plug it in, because there shouldn't be much journaled (and my very vague understanding is that they don't get very big anyway.) I think it's just the sort of meta-information that has to be stored alongside the data. Keep in mind, it's only 0.7% of the total (much less than would be accounted for by the terabyte/tebibyte confusion, and much less than the 5% allocated for root) -- I think it's just the part that describes the file system.

---

### Post by scouser73 on 2008-09-30
I have found this strange also, when I have reformatted my hard drives into various filesystems I see that it takes up quite a bit of space, the most being EXT3 taking up a whopping 22GB of space.  I have found that ReiserFs doesn't seem to take up any space. ReiserFs might not be for you, but it's worth checking it out, and regaining valuable hard drive space.

[http://en.wikipedia.org/wiki/ReiserFS]("http://en.wikipedia.org/wiki/ReiserFS")

Ps. ReiserFs is also a Journaled File System.

---

### Post by hyper_ch on 2008-09-30
ext3 allocates a table of contents first into which the inodes go - basically saving some space so that it can write to where file x actually resides on the harddisk.

---

### Post by jespdj on 2008-09-30
For normal users, on an ext2/ext3 filesystem, 5% of the space is reserved - only the system administrator can use it. This is to guard against problems when the filesystem is almost full.

---

### Post by Excalibre on 2008-09-30
> **jespdj said:**
> For normal users, on an ext2/ext3 filesystem, 5% of the space is reserved - only the system administrator can use it. This is to guard against problems when the filesystem is almost full.
Please read the thread before posting to it.

---

