---
title: "Sometimes HDD; sometimes not HDD XD"
date: 2009-09-06
forum: Hardware
---

### Post by TrUkvk on 2009-09-06
[FONT=Times New Roman][SIZE=3]Hi guys!!
Maybe this thread is already solved but I haven't found it. 

I've got a Laptop with 2 HDD, 500Gb each. One of them is unformatted, just for DATA, and the other one is 250Gb in Ubuntu and 250Gb in Windows Vista (I'm about to remove this partition)

My problem is: sometimes when I start my laptop I can't see neither the DATA HDD, nor the Windows Vista partition, but when I restart, they appear.

Thanks a lot for your help!![/SIZE][/FONT]

---

### Post by SoftwareExplorer on 2009-09-06
What do you mean by not see the data disk? An unformatted disk usually wouldn't show up in the places menu and the like, but would hopefully show up when you run gparted.

---

### Post by TrUkvk on 2009-09-07
I realy don't know if it's unformated, in fact I use it for my downloads. And the partition for Vista is NTFS, and it neither shows it. 
They are neither shown in the menu, nor in /media. But this happens sometimes, I restart, and the units are back

---

### Post by SoftwareExplorer on 2009-09-07
If you are storing files on it, it was formatted at some point in time. 
What happens if you search for partition editor in Add/Remove, and install it, then go to System->Administration->Gparted(or Partition editor, I think it depends on ubuntu's version)? It should show your hard disks and how the partitions are arranged on them. Screenshots would be nice. 

P.S,I may not be capable of fixing your problem, but even if can't, at least I can help figure out what the problem is exactly, and then others might be able to fix it.

---

