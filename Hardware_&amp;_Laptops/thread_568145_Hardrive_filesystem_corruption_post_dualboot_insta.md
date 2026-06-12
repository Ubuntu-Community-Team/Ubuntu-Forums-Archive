---
title: "Hardrive filesystem corruption post dualboot installation"
date: 2007-10-05
forum: Hardware &amp; Laptops
---

### Post by osiris2258 on 2007-10-05
I just added Ubuntu to the 3rd HD on my WIndows XP box, and now there appears to be a problem with the file system on that disk. For the moment, both operating systems are working without incident.

In gparted, the partitions on HD3(contains linux + 2 NTFS partitions) show up, but they can't be resized (the ubuntu install grew one of the windows partitions to twice it's original size, so Linux is in a smaller partition than intended); the message I receive is "check filesystem on /dev/sdc3 for errors and (if possible) fix them". In Windows, Partition magic reports the entire drive with the linux partitions on it as "BAD", with the only option presented being 'format'.

Does anyone know how I can fix this? Preferably without having to reformat the disk? I just added linux, so if I need to reformat the whole drive this would be the time to do it, but it would still be really inconvenient (ironically the other two partitions contain the backups for the data in windows).

---

