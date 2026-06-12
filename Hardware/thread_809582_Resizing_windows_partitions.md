---
title: "Resizing windows partitions"
date: 2008-05-27
forum: Hardware
---

### Post by Thorzilla on 2008-05-27
Well, as you might imagine, I'm new to Ubuntu...
As it were, I installed Ubuntu Hardy 32-bit so I could dual boot between Vista and Ubuntu. Unfortunately, I need more space in my Vista partition. Does anyone know a way to resize the partitions (if it's even possible) ? I tried using GParted and apparently it can't read the NTFS partition. And please don't say "stop using vista":) 

I'm not sure if you need my laptop specs...

Toshiba A221
AMD Turion 64 (duo core)
1 GB RAM, 160 GB HDD

---

### Post by mikewhatever on 2008-05-27
I've never used Vista, and hopefully never will, but isn't there a built in tool for resizing partitions.

---

### Post by robert_rhode on 2008-05-27
Boot from the live CD and then run the partition editor (e.g., gparted).  Don't worry if your live CD is a little bit dated: I was able to use my 7.04 live CD to simultaneously grow Windows Vista (NTFS) and shrink Ubuntu 8.04 (ext3fs).

---

### Post by Thorzilla on 2008-05-28
I'll try that tonight. Thanks!

---

### Post by Thorzilla on 2008-05-29
Booting the liveCD and running GParted worked. However, when I'm resizing partitions, I am unable to increase the size of the Windows partition (there seems to be a gap between the linux and windows partitions). I *can* shrink the ubuntu partition though. 

When I was thinking it through, I figured that maybe I could shrink the linux partition, then format the unallocated part to ntfs and then somehow merge the windows partition and the new ntfs partition.
Is this possible? If yes, how?

Thanks in advance
Regards
TZ

---

