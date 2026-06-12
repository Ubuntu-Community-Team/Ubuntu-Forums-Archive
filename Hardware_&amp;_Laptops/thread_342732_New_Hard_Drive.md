---
title: "New Hard Drive"
date: 2007-01-20
forum: Hardware &amp; Laptops
---

### Post by Zarathu on 2007-01-20
So I bought a new hard drive that I use to keep all of my media on (music, etc).  It's a SATA 3.0 that **does not** have any jumpers in it (which I think might be part of the problem, though SATA doesn't require master/slave jumpers).

Ubuntu does not recognize it at all.  However, Ubuntu did stop recognizing my other SATA drive and recognize the one with my music on it.  Strange.

I'm assuming there's a problem with the number of "slots" for the recognized hard drives.  Any way to fix this?

---

### Post by JamieC on 2007-01-20
Does your BIOS detect it?

Open a new terminal and post the output of the following:
```

sudo fdisk -l

```

---

### Post by Zarathu on 2007-01-20
My BIOS detects it and so does my Windows XP partition.  Do you still want me to output the fdisk -l?

---

### Post by JamieC on 2007-01-20
Yeah, that'd help, please.

---

### Post by Zarathu on 2007-01-20
Oh!  I see the problem.

```
Disk /dev/sda: 81.9 GB, 81964302336 bytes
16 heads, 63 sectors/track, 158816 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      158816    80043232+  42  SFS

Disk /dev/sdb: 400.0 GB, 400088457216 bytes
16 heads, 63 sectors/track, 775221 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1      775220   390710848+   7  HPFS/NTFS

Disk /dev/hda: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2381    19125351    7  HPFS/NTFS
/dev/hda2            2382        3649    10185210   83  Linux
```

Yeah... /dev/sdb1 ....

I just need to mount it.

---

### Post by Zarathu on 2007-01-20
```
~$ sudo mount /dev/sdb1
mount: can't find /dev/sdb1 in /etc/fstab or /etc/mtab
```

---

### Post by JamieC on 2007-01-20
Do you need help with doing that? It's also NTFS, you'll need drivers if you wish to write to it (or otherwise format it appropriately).

---

### Post by Zarathu on 2007-01-20
Never.  I only read from my NTFS drive.

---

Actually, I wouldn't mind getting those drivers if they aren't unstable like I've heard.

---

### Post by JamieC on 2007-01-20
Use the following to mount it (since it isn't set up in fstab you need to provide the options):
```

sudo mkdir /media/windows
sudo mount /dev/sdb1 /media/windows/ -t ntfs -o nls=utf8,umask=0222

```

You can read more about ntfs-3g [here](http://www.ubuntuforums.org/showthread.php?t=217009).

---

### Post by Zarathu on 2007-01-20
I actually just edited fstab manually, but thanks anyway.  I got the mounting part down. ;)

---

