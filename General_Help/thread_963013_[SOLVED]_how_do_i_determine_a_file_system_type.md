---
title: "[SOLVED] how do i determine a file system type?"
date: 2008-10-29
forum: General Help
---

### Post by jimi_hendrix on 2008-10-29
so im trying out slackware and i am partitioning my hard  drive

cfdisk and fdisk both say the type of my partitions are "Linux" but when i try to mount them to /mnt it say that Linux is not a file system type...i tried to mount it with ext2 and ext3 as well...any insight

---

### Post by sdennie on 2008-10-29
You could try using the blkid command:

```

sudo blkid

```

---

### Post by jimi_hendrix on 2008-10-29
only showed first two partitions on hardrive, which were my windows dual boot and the one i put my bootloader on...

---

### Post by jimi_hendrix on 2008-10-29
also i am on the live cd so limited commands (no man pages :()

---

### Post by Sam on 2008-10-29
Get the partition Id with```
sudo fdisk -l
```

and check what it correspond to [here](http://www.win.tue.nl/~aeb/partitions/partition_types-1.html).

---

### Post by jimi_hendrix on 2008-10-30
tried that and got > Linux is a Unix-like operating system written by Linus Torvalds and many others on the internet since Fall 1991. It runs on PCs (386 and up) and a variety of other hardware. It is distributed under GPL. Software can be found numerous places, like ftp.funet.fi, metalab.unc.edu and tsx-11.mit.edu. See also comp.os.linux.* and [http://www.linux.org/](http://www.linux.org/). Various filesystem types like xiafs, ext2, ext3, reiserfs, etc. all use ID 83. Some systems mistakenly assume that 83 must mean ext2.i tried all of the file system types

---

### Post by louieb on 2008-10-30
> **vor said:**
> You could try using the blkid command:
> **jimi_hendrix said:**
> only showed first two partitions on hardrive, which were my windows dual boot and the one i put my bootloader on...

Not good. Sounds like theres something weird going on. 
could you post the output of the **fdisk **and** blkid** commands?

---

### Post by sdennie on 2008-10-30
Maybe the disk is partitioned as Linux but but no filesystem was put on the disk.  As said above, it would be useful to see the output of:

```

sudo blkid
sudo fdisk -l

```

---

### Post by jimi_hendrix on 2008-10-30
i got it...slackware does something very weird (i used cfdisk when i tried arch) it lets you set the file system as "Linux" or "Linux Swap" and than during install it reads this and will know which one the swap is and which one to use for the other directories

---

### Post by jimi_hendrix on 2008-10-30
i got it...slackware does something very weird (i used cfdisk when i tried arch) it lets you set the file system as "Linux" or "Linux Swap" and than during install it reads this and will know which one the swap is and which one to use for the other directories...but problem solved thanks all

---

