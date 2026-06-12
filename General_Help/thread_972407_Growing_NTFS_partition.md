---
title: "Growing NTFS partition"
date: 2008-11-05
forum: General Help
---

### Post by Gamboge on 2008-11-05
I recently deleted my windows partition and I am trying to add it's unallocated space to another ntfs partition. GParted doesn't seem to let me increase the partition size despite the unallocated space that is available to be used, however.

Ideas?

---

### Post by taurus on 2008-11-05
Is the unallocated space right next to your ntfs partition?  If you have another partition between your ntfs partition and the unallocated space, I don't think you can just add that unallocated space to the ntfs partition, skipping over the middle partition.

Post a screenshot, Applications -> Accessories -> Take Screenshot, of the gparted window here if you wish.

---

### Post by josephellengar on 2008-11-05
> **Gamboge said:**
> I recently deleted my windows partition and I am trying to add it's unallocated space to another ntfs partition. GParted doesn't seem to let me increase the partition size despite the unallocated space that is available to be used, however.

Ideas?

I had this problem when I first started using gparted.  I was making a mistake and forgetting to unmount the partition before I tried to resize it.  To unmount it you can do a: sudo umount -a or you can also right click on it in gparted and click the unmount button.  I don't think you need to do this if you use a gparted live cd.

---

### Post by pansz on 2008-11-05
do you have ntfsprogs installed? gparted will not have ntfs resize support if ntfsprogs is not installed.

---

### Post by Gamboge on 2008-11-05
Hey guys, thanks for the advice so far. The partitions aren't next to each other so that has something to do with it I imagine. Also, when I try to unmount /dev/sda5 (the partition I'm trying to grow) it says it's busy. 

Oh, and I do have ntfsprogs pansz.

---

