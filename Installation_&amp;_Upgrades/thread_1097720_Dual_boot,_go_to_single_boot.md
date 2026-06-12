---
title: "Dual boot, go to single boot"
date: 2009-03-16
forum: Installation &amp; Upgrades
---

### Post by joborohe on 2009-03-16
Hi guys,

I was wondering, this person I know wants to try ubuntu, but not remove windows, so knowing that windows is partition 1, and ubuntu would be partition 2. now, he eventually will switch entirely to ubuntu, at which point he would like to reclaim his space in partition 1. which is the best option?

1- resize partition 1 to the smallest possible (8mb) and resize partition 2?

or 

2- remove partition 1 and resize partition 2, in which case, how would that affect ubuntu/grub?

---

### Post by yeats on 2009-03-16
I would say Option 1, then do a fresh install when the person is ready to switch completely.  I think a fresh install avoids the issue completely (making sure to back up all data, etc. before the switch - but you know that :-) ).

---

### Post by theozzlives on 2009-03-16
I would say option 2 giving the Ubuntu partition the boot flag.

---

### Post by Mark Phelps on 2009-03-16
If you're going to do a fresh install, option #2.

The complication is that GRUB uses UUIDs in its boot configuration file, and if you change the number of partitions, the UUID will change -- but not be updated in your menu.lst file unless you do that manually.

Thus, without a reinstall, option #1 retains the UUIDs and you won't have to mess with the menu.lst file.

But if you reinstall, you'll be creating a new menu.lst file anyway, so in that case, it doesn't matter.

---

### Post by meierfra. on 2009-03-16
My vote:

option #3:   Reformat partition 1 to ext3 and use it as a Data partition.

Why:

Having a separate Data partition is a good thing by itself.
Since you will not touch the Ubuntu partition, there is virtually no chance of  corrupting your Ubuntu  Partition
Will only take a few minutes.

---

