---
title: "Best HDD configuration for dual boot?"
date: 2011-01-16
forum: Hardware
---

### Post by SPW06 on 2011-01-16
Hi,

Wow, I haven't posted here in a long time. Anyway, I would like to  dual boot a desktop which I plan on building in the near future. I have priced everything so that the box will be as "future resistant" while still residing within my budget.

I have selected the Western Digital Caviar Black WD6402AAEX 640GB 7200 RPM 64MB Cache SATA 6.0Gb/s 3.5" Internal Hard Drive -Bare Drive. The storage is more than enough for both operating systems. And, the 64 MB cash and SATA III interface should provide for great performance.

However, I am concerned that storing the EXT4 partition after the NTFS one may cause unnecessary work on the read/write head whenever I would use Ubuntu. Is this true? Would there be any advantage to storing the operating systems on two separate drives? I should note, this system will have 16GB of RAM, so I expect very little, if any swaping/paging will be needed.

I could add a second drive but that would give me much more storage than I need and put be over-budget.

And advice is appreciated

---

### Post by reedk on 2011-01-16
Don't worry about the partiton order.  After the boot loader knows which OS you chose, it will jump directly to the appropriate sectors. Your setup is a solid one. When it comes to OS configuration, simple always beats clever.

---

