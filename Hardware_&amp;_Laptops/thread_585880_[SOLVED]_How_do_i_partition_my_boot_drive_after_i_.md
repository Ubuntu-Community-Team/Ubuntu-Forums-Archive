---
title: "[SOLVED] How do i partition my boot drive after i have already installed"
date: 2007-10-21
forum: Hardware &amp; Laptops
---

### Post by plr4ever on 2007-10-21
I installed gutsy a few days ago on a new computer, and i didn't think about leaving space for a windows partition. However, now i realized that i cannot fit an ide hard drive in my case, as my only header is taken up by my dvd burner, and the two drives are too far apart to do a master-slave setup.

I've tried running Gparted and partitioning my drive, but i cannot do it since i have one partition that is my boot, and i cannot unmount. QTparted doesnt work either with this, so i was wondering if i could do it from the command line or pre-boot. I really would love to have a windows partition, as i want to test out my new graphics card, and I cannot get wine or cedega working. 

Please help. :confused::confused:

---

### Post by gsiliceo on 2007-10-21
Use your live cd, since nothing will be mounted, gparted should do the trick.

Maybe you need to install it.

---

### Post by plr4ever on 2007-10-21
> **gsiliceo said:**
> Use your live cd, since nothing will be mounted, gparted should do the trick.

Maybe you need to install it.

Thanks, but will this affect the data on the partition?

---

### Post by jrharvey on 2007-10-21
I would repartition and erase everything. The reason for this is Windows doesn't play well with others and if you install it after ubuntu, your ubuntu will be useless anyway. Thats pretty much what happened to me. Im sure you dont have all that much data saved up for a few days. You can install windows after ubuntu but its alot more trouble.

---

### Post by jrharvey on 2007-10-21
if i were you I would create the needed partitions with the live cd and then install windows and then ubuntu.

---

### Post by plr4ever on 2007-10-21
Awesome, sounds like a plan. I'll mark solved once i get it all done. 


Thanks All!!!!!!!!

:)

---

