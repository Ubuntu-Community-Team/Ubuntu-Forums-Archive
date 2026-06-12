---
title: "Can't copy from CD"
date: 2006-01-08
forum: Installation &amp; Upgrades
---

### Post by ocirneobmoloc on 2006-01-08
I'm trying to install Ubuntu 5.10 x AMD64 on my computer but after boot the installation stops because: "can't copy file JFSUTILS_UDEB".
I downloaded several times the ISO and I checked the MD5 which appear correct; I burned the ISO on a CD-R and even on CD-RW (@4x speed), but I got the same issue.
The same issue appear using even the Ubuntu LIVE version.

The computer is an AMD 64 3500+, 512 Mb RAM, HD 160Gb Sata (no EIDE HD at all), DVD burner on Secondary Master EIDE channel, and chipset NForce 4, NVidia 6600 graphic card.

Any suggestion to overcome the problem is appreciated.

Thanks
Enrico

---

### Post by taurus on 2006-01-08
Do you happen to use jfs as your filesystem???

---

### Post by ocirneobmoloc on 2006-01-08
If I'm not misunderstanding the question, I would say: with WXP everything works smoothly. No issue at all.

---

### Post by ocirneobmoloc on 2006-01-08
Let me add some details about the disk configuration. Currently the disk is partitioned as follows:

1) 70 Gb dedicated to WXP with NTFS
2) 40 GB dedicated to WXP with FAT32
3) 20 Gb unallocated (here is where I would like to place Ubuntu)
4) 20 Gb FAT32 no OS (this partition is seen by all the OS in order to exchage data and backup)

I use BootMagic to chose the OS.

I don't really think the above can create problems, because I got an another computer (AMD 32bit) with the same configuration and everything works perfectly: UBUNTO 5.10x 386 included.

Enrico

---

### Post by deveborn on 2007-10-01
Did someone ever get any solution to this problem? I had the same experience with an old laptop computer, and have no idea what to do. Checksums is ok and I have done an installation on another computer with the same CD so I dont think it has to do with the CD.

/David

---

