---
title: "HD broken? fsck and e2fsck have given up"
date: 2007-01-21
forum: Hardware &amp; Laptops
---

### Post by Bumfun MC on 2007-01-21
Hello,

when i was working with my computer the screen froze suddenly. At the next reboot fsck checked the partition / and found some errors in /usr and /etc. After resolving this by deleting so many files that Ubuntu couldnt start anymore I decided to boot the already installed Breezy Badger from another HD to test if /home (aka hdc1) is okay. Fsck terminated with «signal 8». Why is this? How do I get access to the ext3 formatted HD «hdc1»? Is the superblock possibly broken? (see below)
Here are some cuts from the terminal:


```
root@pc2:~# fsck /dev/hdc1 
fsck 1.38 (30-Jun-2005)
e2fsck 1.38 (30-Jun-2005)
Warnung... fsck.ext3 für Gerät /dev/hdc1 wurde mit Signal 8 beendet.

```(Warning... fsck.ext3 for /dev/hdc1 was terminated with signal 8 )

```
root@pc2:~# tune2fs -l /dev/hdc1
tune2fs 1.38 (30-Jun-2005)
Gleitkomma-Ausnahme
```(means: floating-point exception)

```
root@pc2:~# fdisk -l

Platte /dev/hdc: 120.0 GByte, 120060444672 Byte
255 Köpfe, 63 Sektoren/Spuren, 14596 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/hdc1   *           1       10334    83007823+  83  Linux
/dev/hdc2           10335       14455    33101932+  83  Linux
/dev/hdc3           14456       14596     1132582+   5  Erweiterte
/dev/hdc5           14456       14596     1132551   82  Linux Swap / Solaris

```

```
root@pc2:~# mount /dev/hdc1 /media/hdc
mount: wrong fs type, bad option, bad superblock on /dev/hdc1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


```

```
root@pc2:~# dmesg | tail
[4298244.036000] EXT3-fs: unsupported inode size: 0

```

---

### Post by Bumfun MC on 2007-01-21
[http://forum.ubuntuusers.de/topic/69747/](http://forum.ubuntuusers.de/topic/69747/)

---

