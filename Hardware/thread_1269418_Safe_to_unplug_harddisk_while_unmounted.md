---
title: "Safe to unplug harddisk while unmounted?"
date: 2009-09-18
forum: Hardware
---

### Post by fela on 2009-09-18
I have an external harddrive that is regularly used for backups, but there is no on/off switch. It has an XFS filesystem and I make sure to always cleanly unmount it before turning off power to the hdd, to avoid the 0byte file problem with XFS and power cuts.

The thing is, do you reckon it's safe to unplug the harddisk while it's still spinning, but umounted? Ie, it wouldn't be accessing anything on the drive at this moment in time as there's nothing mounted let alone being accessed.

Just to be clear, I'm talking about the actual physical drive mechanism/circuit board, not the filesystem.

Thanks

---

### Post by bruno9779 on 2009-09-18
I have the same doubt.
My workaround is unplugging the power from the back of the HDD first

---

### Post by fela on 2009-09-18
> **bruno9779 said:**
> I have the same doubt.
My workaround is unplugging the power from the back of the HDD first

Well that's what I do, and that's what I'm having doubts about.

---

