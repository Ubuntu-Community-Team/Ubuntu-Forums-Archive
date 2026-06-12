---
title: "&quot;clone&quot; hardrive"
date: 2007-01-04
forum: Hardware &amp; Laptops
---

### Post by ninocass on 2007-01-04
Hi all

I recently purchased a 120GB harddrive for my laptop to replace my 40GB.

The 40GB is set up with the following partitions:

EXT3 - Ubuntu
FAT32 - Windows
FAT32 - Storage
SWAP

Is it possible to "move" the content/settings/OS/MBR/Partitions to the new hardrive so that i can plug in the 120GB and the drive will boot allowing me linux/windows?

Cheers

Nino

---

### Post by kidders on 2007-01-04
Hi there,

It is. :-) You can use "dd" to dump the contents of one device onto another.

Since the two disks have different geometries, I'd be inclined to take a more manual approach, if it were me though. That would also make it easier for you to resize any partitions you wanted to make bigger, now that you have more wiggle room.

So, if I were doing it (and quite possibly for no particular reason! :-? ), I would manually recreate partitions, **cp -dpR** the filesystems, re-run **mkswap** and **grub** to create swap space and a shiny new MBR, tweak my /etc/fstab, and reboot.

---

