---
title: "[SOLVED] Unable to mount external hard drive"
date: 2008-09-25
forum: General Help
---

### Post by I[AM]SMRT on 2008-09-25
I've got a Seagate FreeAgent 500 GB external that I can no longer mount because I changed its properties. Properties -> Volume -> Settings and I changed the mount point from "/media/FreeAgent Drive_" to "/media/FreeAgent500". I then unmounted it and when I tried to remount it, it gave me the following error:

```
Cannot mount volume.

Unable to mount the volume 'Freeagent Drive'

Details:
mount_point cannot contain the following characters: newline, G_DIR_SEPARATOR (usually /)
```

What can I do to fix this?

The reason I changed the mount point was because I'm using the diskusage/diskspace screenlets and it seems they can't display the disk info for drives with spaces in their names.

Thanks,
SMRT

EDIT: After more online searching I found a fix here:

[https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/107668](https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/107668)

---

