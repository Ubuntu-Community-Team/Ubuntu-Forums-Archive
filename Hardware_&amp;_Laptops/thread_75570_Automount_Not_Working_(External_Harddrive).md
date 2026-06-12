---
title: "Automount Not Working (External Harddrive)"
date: 2005-10-13
forum: Hardware &amp; Laptops
---

### Post by quazi on 2005-10-13
My external harddrive only automatically mounts in Gnome.  In either XFCE or KDE, the drive won't mount automatically, and I need to manually enter the following to mount it:
```
sudo mount -t ntfs -o ro,umask=0222 /dev/sda1 /media/Stuff
```

This isn't really a huge expendature of effort, but I feel that I shouldn't have to do that.

---

### Post by born_confused on 2005-10-13
[QUOTE=quazi]My external harddrive only automatically mounts in Gnome.  In either XFCE or KDE, the drive won't mount automatically, and I need to manually enter the following to mount it:
```
sudo mount -t ntfs -o ro,umask=0222 /dev/sda1 /media/Stuff
```

This isn't really a huge expendature of effort, but I feel that I shouldn't have to do that.[/QUOTE]

Im not sure that xfce does it, however you are lucky it mounts in Gnome, I posted this earlier

[http://ubuntuforums.org/showthread.php?t=75268](http://ubuntuforums.org/showthread.php?t=75268)

mine doesnt even automount in gnome.

---

