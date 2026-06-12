---
title: "replacing failing system disk"
date: 2005-08-19
forum: Hardware &amp; Laptops
---

### Post by snowsquirrel on 2005-08-19
My hda is going south. I have a good (crosses fingers) disk as /dev/hdb right now.  My plan for migration is this:

1. fdisk /dev/hdb, and create similar partion scheme on hdb.
2. newfs all new partititions, mkswap on swap partition.
2. from knoppix, "cp -a" the contents of /dev/hda to /dev/hdb.
3. chroot to the / of hdb, and run grub.
4. poweroff, pull hda, make hdb the new primary-master (aka hda).
5. boot and pray.

Anyone see any wholes in this theory?

Thanks.

---

### Post by glug101 on 2005-08-19
No 'wholes' and no obvious holes either :)

Looks like it might work. (assuming none of the important files are pooched allready, and in my experience that's a pretty BIG if)  Good luck!

---

