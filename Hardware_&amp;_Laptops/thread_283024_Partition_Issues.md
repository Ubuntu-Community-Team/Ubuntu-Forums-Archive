---
title: "Partition Issues"
date: 2006-10-23
forum: Hardware &amp; Laptops
---

### Post by shawnzyoo on 2006-10-23
So I have multiple partitions set-up to dual boot with windows
[LIST]
[*]windows
[*]linux
[*]linux swap
[*]fat32
[/LIST]

I shrank the fat32 to a smaller size to add onto the windows partition (bloated windows system) using gparted

I then had rebooted the system, when I used gparted again, it does not show any of my partitions anymore, just one large unallocated space.
But the partitions still exist and I can access them as normal through windows and linux
I would be fine with this except that there is still 10gb unallocated that I was going to add onto windows

I tried using Partition magic 7 to finish the setup, but I get an error that says there is an unlabeled partition (my 10gb) and the fails to run

Does anyone have any suggestions either with gparted or partition magic? 
Thanks

---

### Post by shawnzyoo on 2006-10-23
so I got it all sorted out
I deleted the fat32 partition in windows and then merged it with the unallocated space.

When I then used gparted again all my partitions reappeared as usual and everything was restored to normal...got lucky on this one

---

