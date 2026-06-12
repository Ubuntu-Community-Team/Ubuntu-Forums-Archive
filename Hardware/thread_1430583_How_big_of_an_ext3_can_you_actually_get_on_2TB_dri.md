---
title: "How big of an ext3 can you actually get on 2TB drive"
date: 2010-03-15
forum: Hardware
---

### Post by urobb on 2010-03-15
Hi all,

I'm setting up a file server and putting /home on a RAID 10.  I would like the entire file system to be able to fit onto a 2TB drive for easy off-site backup'ing.

Could anyone kindly suggest a good total size to use for my /home volume that will safely fit onto a 2TB drive formated with one volume and ext3 file system?

---

### Post by ubunterooster on 2010-03-15
why not ext4?

---

### Post by srs5694 on 2010-03-15
See [this Wikipedia page](http://en.wikipedia.org/wiki/Ext2) (among other places) for ext2 limits, or [this other Wikipedia page](http://en.wikipedia.org/wiki/Comparison_of_file_systems) for a comparison of filesystems. Ext2fs is limited to between 2TiB and 32TiB in total size.

---

### Post by urobb on 2010-03-15
Ok, you talked me into ext4!

The reason I was thinking ext3 would be a safe choice is that when I first googled ext4 I found the following link: Is this anything to worry about?
[http://en.wikipedia.org/wiki/Ext4#Disadvantages](http://en.wikipedia.org/wiki/Ext4#Disadvantages)

I just recently noticed people talking about the limitations of creating a ext3 larger than 2TB on certain version of the Linux kernel, but some folks reported that it wasn't a problem for them with more current version of Ubuntu.  I'm not planning to go over 2TB in the foreseeable future, but it'd be nice to know that I will be able to grow if there is a need.

For the meantime, I would like to create a file system on a RAID 10 volume that can hold as much data as can safely fit onto a single 2TB disk for occasional backups.  With that in mind, do you have any advice about how big I should make the ext4 file system to-be-backed-up so that it will fit on any 2TB disk with a single ext4 volume?

I understand that what I'm getting at is not an "enterprise" solution, but trust me, we are not an enterprise :)

---

### Post by CharlesA on 2010-03-15
I've got a 4TB partition on a RAID 5 array that is running EXT3.

You could probably make the /home partition around 1.75TB safely. I've got around 1.8TB of usable space on a 2TB drive.

---

### Post by ubunterooster on 2010-03-15
....too many threads, so little time.

  Okay, the only problem I've found w/ ext4 is if you begin writing a file and, say, the power goes out or the plug gets pulled you will lose that file. But then, you DO keep backups in case you lose something so you can pull up the backup. Speed, disk size possibilities, and safe practices [ahem, BACKING UP] make up easily for that. Any more questions?

I really got to stop subscribing to so many threads. But first!, I'm gonna go ban somebody....

---

