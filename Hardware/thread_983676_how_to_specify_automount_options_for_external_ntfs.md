---
title: "how to specify automount options for external ntfs drive?"
date: 2008-11-15
forum: Hardware
---

### Post by ElVirolo on 2008-11-15
Hi everyone,

I have an external LaCie NTFS drive, which I use for backups. I'm trying to copy some files whose names contain accents onto it, so I need it to be mounted with the utf8 option (I think). However, I don't know how to specify the automount options.
I know I can use pysdm or just add a line in /etc/fstab. The thing is when I do that, there's a conflict with the automount : the automount puts it in /media/LaCie anyway, even if there's another mountpoint for the same drive specified in /etc/fstab, so I end up with two different mountpoints.

Many thanks in advance,

ElVirolo

---

### Post by ElVirolo on 2008-11-16
up

---

