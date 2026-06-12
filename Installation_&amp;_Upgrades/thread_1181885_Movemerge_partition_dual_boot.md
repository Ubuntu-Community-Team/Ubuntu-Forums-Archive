---
title: "Move/merge partition dual boot"
date: 2009-06-08
forum: Installation &amp; Upgrades
---

### Post by kurtosis4 on 2009-06-08
Hi All,
I'm new to Ubuntu but have managed to set up a dual boot laptop (w/ Vista).
I found that my Ubuntu install was reserving too much space and decided to re-allocate some of that space for shared data (music, pics, videos) between the two OS's.

My plan was to merge the exisiting DATA partition with the new unallocated space. The DATA partition is already read/write by both OS's.

I shrank the ubuntu partition (using GPartEd) and all seemed to go well.

Now I find that I cannot merge the unallocated space to the DATA partition in Vista (threads outside of this forum suggested using M$ for that part).

Should I be trying to 'point' /dev/sda4 to the same place as /dev/sda5 before reclaiming the unallocated space in Vista? How would I do this?

Any advice/help/suggestions would be greatly appreciated!.....even if its to do a complete Ubuntu reinstall ;)

fdisk and GPartEd screenshots are attached....

---

### Post by zvacet on 2009-06-08
You can not merge them because your unallocsted space is part of extended partition.Shrink extended partition and unallocated space will be outside of it.Now you can extend your data partition on unallocated spacce.

---

### Post by kurtosis4 on 2009-06-08
Thanks for the quick response zvacet!

I found the issue...I wasn't able to resize the extended partition (/dev/sda4) in GParted because the underlying partitions were locked/mounted.

After unmounting/swapoff-ing, the resize option appeared in the right-click menu.

Then I shrank as you specified (using the Ubuntu Live CD). The results appear below...

---

### Post by zvacet on 2009-06-09
Now you can expand your sda3 to unallocated space.You can use [Gparted live Cd]("http://gparted.sourceforge.net/") for that.

---

