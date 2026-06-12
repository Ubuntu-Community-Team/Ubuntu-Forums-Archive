---
title: "Gparted question"
date: 2008-12-13
forum: Installation &amp; Upgrades
---

### Post by ukulele_ninja on 2008-12-13
I wanted to resize my storage and system partitions to allow additional space for my system folders and less for storage use. 

So I booted into Gparted via the live CD and attempted to resize the storage partition but it wont allow me to, meaning, it wont let me change any of the default parameters already in the 'resize' box. Would it be best just to delete the storage partition and try and resize the system partition from the unpartitioned space? Or should I scrap it and just reinstall ubuntu?

---

### Post by prshah on 2008-12-13
> **ukulele_ninja said:**
> 
So I booted into Gparted via the live CD and attempted to resize the storage partition but it wont allow me to,

If the storage partition is mounted, you will not be allowed to resize it. Right-click the entry for the partition in gmounted, and choose "Unmount". If your swap partition is also on the same HDD, it may not allow you to make changes to other partitions if it is active; you can disable swap when on live CD by right clicking the swap partition and choose "SwapOff".

Once you have unmounted all relevant partitions, you should be able to resize/move the partitions as you wish. If you still can't post back either a gparted screenshot and/or the following terminal (Applications-Accessories-Terminal) command```
sudo fdisk -l
```

I would never recommend scrapping an existing setup and reinstalling fresh, but that's my personal preference.

---

