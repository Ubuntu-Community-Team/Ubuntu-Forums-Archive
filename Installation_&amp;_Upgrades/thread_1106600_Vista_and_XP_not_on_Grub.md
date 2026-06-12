---
title: "Vista and XP not on Grub"
date: 2009-03-25
forum: Installation &amp; Upgrades
---

### Post by skykaptain on 2009-03-25
Hello,

I had Vista and XP on my hard drive then installed Ubuntu 8.10. Now neither Vista or XP show up in the Grub menu. How can I add them back?

Here is my fisk -l

Sda is is my mian hard drive with XP (454 GB), Vista (1 TB) and Ubuntu (35 GB) installed. Sdb is my music, videos and pictures. Sdc is my external back up.

```
Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdf38df38

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       55220   443546617+  83  Linux
/dev/sda2           59789      182402   984889344    7  HPFS/NTFS
/dev/sda3           55221       59788    36692460   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2fba0c36

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001   42  SFS

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfe81fe81

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1      121601   976760001    7  HPFS/NTFS

```

---

### Post by shark1997 on 2009-03-25
Can you mount your windows partition?
In your fdisk it only shows one windows partition

---

### Post by Pumalite on 2009-03-25
Edit menu.lst and add an entry for each one at the end
```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by shark1997 on 2009-03-25
the entry would be something like

root (hd0,{partition#})
chainloader +1
boot

---

### Post by Pumalite on 2009-03-25
There are 2 ntfs partitions:sda2 and sdc1

---

### Post by Pumalite on 2009-03-25
More  like:
Title  XP or Vista
boot (hd0,1) or (hd2,0) or UUID's
map   xxx   xxx
map xxx  xxx
chainloader +1

---

### Post by skykaptain on 2009-03-25
> **Pumalite said:**
> More  like:
Title  XP or Vista
boot (hd0,1) or (hd2,0) or UUID's
map   xxx   xxx
map xxx  xxx
chainloader +1

Ok, I have added this:```

title         Windows Vista
boot          (hda0,1)
map           /dev/sda2
chainloader   +1

```

I got a Error 8: Kernal must be loaded before booting. What does that mean?

---

### Post by klo44w on 2009-03-25
Hello

I am also having the same problem. I think my problem stemmed from the time I installed Ubuntu, and there was a problem with its preferred method of partioning. So I chose the next best option (and this was not the manual option).

So now, I have totally lost all access to my other partitions (assuuming they are still there).

When I do fdisk -l, I get this:
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x417d77ce

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18662   149902483+  83  Linux
/dev/sda2           18663       19457     6385837+   5  Extended
/dev/sda5           18663       18664       16033+  82  Linux swap / Solaris
/dev/sda6           18665       19416     6040408+  83  Linux
/dev/sda7           19417       19457      329301   82  Linux swap / Solaris

Kindly help. I've tried using the vista recovery disk, but it is unable to detect any partitions, so I can't do a fixmbr either.

I think I have gotten myself into a silly pickle.

My last ditch options are to keep ubuntu and reinstall vista via virtual box, but will prefer to keep my vista as dual boot.

Thks in advance.
ken

---

