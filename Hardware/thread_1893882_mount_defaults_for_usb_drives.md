---
title: "mount defaults for usb drives"
date: 2011-12-11
forum: Hardware
---

### Post by arnowas on 2011-12-11
dear forum,

i have the following question:

i want to change the defaults for mount options, when external usb drives or sticks are mounted.

on my oneiric installation external usb drives are now mounted read-only for normal users, and with 'sync' options for vfat partitions, which gives HORRIBLY slow write speeds.

Thus i want them automatically mounted with umask=000, and with async at least for vfat partitions.

Manual adjustion of /etc/fstab or the like is NOT an option for me, but the only solution i could find after searching around some dozens of forum pages here and elsewhere. I am working in a big group with literally hundreds of drives or sticks going through my usb-plug, so i need something which works automagically both while booting and when mounting via kde device notifier or all those other GUI things like nautilus and those...

Does something like that exist? I would need to install windows otherwise... :-(

Yours, Arno

---

### Post by mtcycler on 2011-12-11
I am in the same boat, I manage a Ubuntu computer lab.  The users in the lab have usb drives which are fat32 and ntfs formatted and need to be able to have executable stuff on the drives.  This means I need a umask of 027 not a 177 which is what the automount appears to be mounting it as.

---

### Post by agestrada on 2012-03-03
Bump

Anyone with a solution that does not involve fstab or going back to Lucid?

Thanks,

---

