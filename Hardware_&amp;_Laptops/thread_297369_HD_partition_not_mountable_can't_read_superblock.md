---
title: "HD partition not mountable: can't read superblock"
date: 2006-11-11
forum: Hardware &amp; Laptops
---

### Post by robenroute on 2006-11-11
Hi there,

I'm having troubles with my external USB drive (2.5"-40GB Hitachi). There's only 1 single partition on the disk, which is formatted as FAT32. There are also lots of files and directories on the disk, stuff I can't lose. Now, when I connect my USB drive, the drive is not auto-mounted. It is visible in a Nautilus browser window (Places -> Computer), but double-clicking its icon results in Nautilus issuing the following error:

"**Unable to mount the selected volume**"

Clicking on show more details gives:

"**mount: /dev/sdb1: can't read superblock**"
"**could not execute pmount**"

I've had a look at the partition structure with testdisk. Testdisk reports 1 single partition (which is primary) and I had testdisk analyze the partition, rebuild the FAT and rewrite the partition table. In addition, I had testdisk rewrite the MBR, but all of this with no result (as to resolving the superblock issue).

Anyone out there with an inclination for throwing in a few hints/clues? Much obliged!

Rob

---

### Post by robenroute on 2006-11-11
Hi there,

I've been thinking (happens not too often ;)), but this problem started after I connected to several Windows machines (XP) to transfer some files from my portable HD to those machines....

Could it be that some virus or other corrupted the MBR? If so, how can I check/repair this? Unfortunately, I have no access to a Windows machine anymore.

Thanks a bunch!

---

### Post by robenroute on 2006-11-11
Right, now this is interesting: I've let testdisk have a go at the partition (Analyze, Write FAT, etc.) and according to testdisk everything is hunky-dory now. Then, when I start the following command:

fsck -t vfat /dev/sdb1

fsck says it has to give up because of corrupted FAT. What's going on? I'm somewhat flustered.... Anyone?

Cheers, Rob

---

### Post by robenroute on 2006-11-11
Anyone, Please....

---

