---
title: "Cannot mount NTFS"
date: 2008-09-17
forum: General Help
---

### Post by phoenixankit on 2008-09-17
My Windows XP caught a virus or something, and I'm not able to run it, my last shutdown was not a proper one.
I booted my trusty ;) ubuntu live cd, to take my backup, but my data is in an NTFS drive, and I'm getting this error
[IMG]http://i37.tinypic.com/vzg64m.png[/IMG]
I googled this, and the solution that worked was to start XP, reboot it properly, then start Ubuntu. But since my XP is not running(not even safe mode, my safe mode was fried even before the virus).

---

### Post by trevelyan on 2008-09-17
in a terminal:
```

mount -t ntfs-3g /dev/sda7 /media/GAMES -o force

```

---

### Post by phoenixankit on 2008-09-17
It says only root can do that.

---

### Post by sh_son on 2008-09-17
> **phoenixankit said:**
> It says only root can do that.

> **trevelyan said:**
> in a terminal:
```

mount -t ntfs-3g /dev/sda7 /media/GAMES -o force

```

Open terminal and type the following:

#**sudo** mount -t ntfs-3g /dev/sda7 /media/<name of hdd> -o force

but mounting NTFS might corrupt the MBR table,
use it as the last resort.

Regard.

---

### Post by phoenixankit on 2008-09-17
ubuntu@ubuntu:~$ sudo mount -t ntfs-3g /dev/sda7 /media/GAMES -o force
$LogFile indicates unclean shutdown (0, 0)
WARNING: Forced mount, reset $LogFile.
fuse: failed to access mountpoint /media/GAMES: No such file or directory
FUSE mount point creation failed
Unmounting /dev/sda7 (GAMES)



???

---

### Post by Joeb454 on 2008-09-17
I've force mounted my NTFS partition a couple of times.

As far as I'm aware you don't need to use mount with ntfs-3g. I just simply ran ```
sudo ntfs-3g -o force /dev/sda2 /media/Vista
```

Naturally replace /dev/sda2 with the appripriate drive/partition :)


_EDIT:_ After seeing the post above it seems you don't have a /media/GAMES directory, try running ```
sudo mkdir /media/GAMES
``` before mounting :)

---

### Post by phoenixankit on 2008-09-17
WIN! 
Thanks guys!

---

