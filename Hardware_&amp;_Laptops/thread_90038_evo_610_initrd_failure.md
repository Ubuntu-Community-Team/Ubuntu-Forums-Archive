---
title: "evo 610 initrd failure"
date: 2005-11-14
forum: Hardware &amp; Laptops
---

### Post by MrCheese on 2005-11-14
I have a Comapq Evo N610c on which I've installed Breezy via the Preview cd & updates. This laptop previously ran Hoary fine. I get the following error trying to boot the latest 2.6.12-9 kernel :

Uncompressing Linux...Ok, booting the kernel
[4294669.038000] RAMDISK : ran out of compressed data
[4294669.038000] invalid compressed format (err=1)
[4294669.039000] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown block(0,0)

My /boot is quite small, I'm assuming this doesn't matter as the initrd is uncompressed to RAM - I moved /boot from it's own partition to / with the same result so AFAIK it's not related to disk space. 2.6.12-8 still boots fine (thanks, Grub!).

Any help would be appreciated.

---

