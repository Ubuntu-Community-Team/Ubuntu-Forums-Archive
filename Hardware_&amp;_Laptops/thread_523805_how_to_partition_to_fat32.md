---
title: "how to partition to fat32"
date: 2007-08-12
forum: Hardware &amp; Laptops
---

### Post by pacsum on 2007-08-12
I recently installed ubuntu on a 60gb hdd and made 2 partitions both ext3 (one for ubuntu and the other for my stuff) but now I want to convert the second one to fat32. I downloaded Gparted but gparted doesn't gives me the partition option. How could I erase and convert the drive to Fat32?
BTW the drive haves a Lost & Found Folder which I find it to be strange.

---

### Post by pmagill on 2007-08-12
use gparted from the live cd.... there you go

---

### Post by dabl on 2007-08-12
> **pacsum said:**
>  but gparted doesn't gives me the partition option.

Yes, it does.  In GParted, highlight the partition of interest, then right-click on it, and select "Format To:".  You will be presented with a list of filesystem choices, so just pick FAT32 if that's the one you want.  :)

---

