---
title: "Resizing Ubuntu partition"
date: 2005-08-06
forum: Hardware &amp; Laptops
---

### Post by xaque on 2005-08-06
I have a 60 GB hard drive, with Ubuntu installed on the first 10 gigs of it. I want to resize Ubuntu to fill up the entire hard drive (with about 3gb for swap). My current drive layout is like this:

10 gb - Ubuntu (ReiserFS)
47 gb - Free Space
3 gb   - Extended partition
    2 gb - ext2 partition
    1 gb - swap

What is the quickest, easiest, most risk-free way to do this?

---

### Post by wvslkr on 2005-08-06
Personally I like QTParted.  As always back up anything you want to be sure to have if you are going to mess with partitions.

Back Up!!!! :)  :)

---

### Post by xaque on 2005-08-06
I tried using QTParted, but the problem I had was that it wouldn't let me change the partition that Ubuntu was running on (or the swap partition either).

---

### Post by wvslkr on 2005-08-06
You can't change a partition that is in use.  The best way is to use a live cd.  Don't recall if Ubuntu has it, but Mepis or Knoppix both do.

---

### Post by az on 2005-08-06
Or use the install cd.  Boot and make your way to the partitioner.  It can handle that.  Exit when you are done without continuing on...

---

### Post by xaque on 2005-08-07
Okay, I tried using both Knoppix and the Ubuntu install CD. On QTParted in Knoppix, it showed the resize button for the Ubuntu partition, but it was grayed out. The only partition mounted by Knoppix was the swap partition. Do I need to unmount this partition? How would I do that? As for the install CD, I saw options to erase the disk, and create new partitions, but not to resize existing ones. Am I missing something?

---

### Post by az on 2005-08-07
I think knoppix mounts your swap.  That would be the problem.

As for the install cd, pick manually edit partition table....

---

