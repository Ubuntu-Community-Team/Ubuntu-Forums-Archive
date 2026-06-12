---
title: "help w/ possible fatal error w/ usb hard-drive"
date: 2007-05-14
forum: Hardware &amp; Laptops
---

### Post by 13east on 2007-05-14
i have a 60gb external usb hard-drive and have been using it for about a couple of years now w/out any problems.  i have been able to use it on both my windows and ubuntu machines (laptop and desktop).  but just recently it seems like the hard-drive crashed and can't seem to be able to get it to mount at all.  all of a sudden it just stopped working and won't mount on any of my computers (dual-boot laptop with feisty and xp sp2, and desktop with edgy).  the funny thing is that my other usb devices work perfectly:  my usb mouse and a usb numpad work perfectly.  i would really appreciate it if someone could help me out this problem... i really need this drive to easily transfer large files between my computers otherwise its gonna be pain when trying to move couple of gigs of files around.
the output of "sudo fdisk -l" while the drive is plugged is as follows:
```

sanish@mobile-beasty:~$ sudo fdisk -l

Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2613    20988891    7  HPFS/NTFS
/dev/hda2            2614        5893    26346600    7  HPFS/NTFS
/dev/hda3            5894        6089     1574370   82  Linux swap / Solaris
/dev/hda4            6090        7296     9695227+  83  Linux

```

---

### Post by Spartan.II.117 on 2007-05-14
ouch, it's possible that your HDD had a hardware failure..  you can replace the drive within the enclosure but i think the actual drive is dead.

---

### Post by 13east on 2007-05-14
> **Spartan.II.117 said:**
> ouch, it's possible that your HDD had a hardware failure..  you can replace the drive within the enclosure but i think the actual drive is dead.

i was afraid of that...

is there any way i can be sure its hard-drive failure before i go out to buy another drive... i just don't wanna go out and buy another drive and it be for no reason...

thx in advance to all willing to help... and u 2 Spartan

---

### Post by Spartan.II.117 on 2007-05-14
I would recommend opening your enclosure and adding the hard drive directly to your computer, if you still cant access it, then windows has some diagnostics programs you can run (possibly provided by the manufacturer of the actual drive.) to see if the data's recoverable.

---

