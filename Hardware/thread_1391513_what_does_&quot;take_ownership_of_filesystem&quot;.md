---
title: "what does &quot;take ownership of filesystem&quot; mean in palimpsest"
date: 2010-01-26
forum: Hardware
---

### Post by felipe1982 on 2010-01-26
I have selected the option to "take ownership of filesystem" but I have no idea how to reproduce this WITHOUT using palimpsest (i.e. from gnu bash). Palimpsest _does_not_ edit /etc/fstab (I've checked it several times). The ext(2,3,4) mounting option does not include "...,user=felipe" and adding it gives an error when mounting (manually adding the option, and including it in /etc/fstab both give errors).

I've checked man page for mke2fs(8) but a search for 'own' or 'owner' turns up nothing useful.

How do I take ownership of filesystem without using palimpsest?

(running karmic, gnome + xfce)

---

### Post by Seq on 2010-01-26
```
sudo chown ${USER} /mountpoint/of/disk/i/want/to/own
```
or
```
cd /mountpoint/of/disk/i/want/to/own
sudo chown ${USER} .
```

This is handy in case you suddenly find you can write to arbitrary new files off / (things like `touch /foo` as a user should fail, obviously). I had it happen once by accident after mounting a disk in another machine. I must have chown'd the mount to grab files from it. Oops.

Also, **DON'T** do -R, you probably do not want that. ESPECIALLY on /.

---

### Post by felipe1982 on 2010-01-26
Thanks. Mount partition first, then change ownership? Or 'umount' first, then change ownership of mount point?

edit
1) mount first
2) chown second
3) ..works a treat!

---

### Post by Seq on 2010-01-26
> **felipe1982 said:**
> Thanks. Mount partition first, then change ownership? Or 'umount' first, then change ownership of mount point?

Mounted. The ownership of the directory when not mounted doesn't matter, it's ownership and permissions are replaced with the new filesystem's '.'

---

### Post by Seq on 2010-01-26
Actually, that illustrates a neat little trick, as well. If you umount, then `chown 000 /your/directory` your user won't be able to put files there when the file system is not mounted, and accidentally fill up your disk (or worse, do that then 'lose' the files when you fix your mount).

---

