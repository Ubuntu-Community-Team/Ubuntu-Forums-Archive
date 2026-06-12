---
title: "Mounting HFS+ disk image"
date: 2010-08-24
forum: Hardware
---

### Post by franksmyth on 2010-08-24
Hello,

I used ddrescue to image a dying disk that has many bad sectors. The first pass of ddrescue left about 15GB unrecovered. Subsequent passes were recovering bits of this at a rate of a few MB per day so I had to abandon that.

The issue that I am having is that while the original disk will mount in Ubuntu, the image will not. I get a bad superblock error. 

However using testdisk I can see that the superblock and backup superblock on both disks are identical.

The original disk is 250GB while the disk I am imaging onto is larger at 320GB. So there is 70GB left unused at the end of the image disk. Could the different disk sizes be causing the image to be unmountable?

fsck.hfsplus will not run either reporting invalid node structure and invalid record count.

Any advice on how I could get the image to mount would be much appreciated.

Thanks,
-Frank

---

