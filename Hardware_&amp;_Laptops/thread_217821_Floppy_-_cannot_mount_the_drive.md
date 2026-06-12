---
title: "Floppy - cannot mount the drive"
date: 2006-07-17
forum: Hardware &amp; Laptops
---

### Post by Turin Turambar on 2006-07-17
Ubuntu won't read my diskettes.

Fstab line is there:

/dev/fd0        /media/floppy	vfat	rw,user,noauto	0       0

When I try to mount, it starts the drive, but doesn't show anything. After about 2 mins of waiting, it reports an error:

mount: /dev/fd0 is not a valid block device

... or similar.
I tried changing "vfat" to "auto", but without success.

Any clues? Thanks!

---

### Post by mltom on 2008-03-29
This is the exact same error I receive after my Xubuntu 7.10 install.

I hope someone answer's your question.

tom

---

