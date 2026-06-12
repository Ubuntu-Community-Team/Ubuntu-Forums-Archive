---
title: "Windows partition needs more room"
date: 2008-06-02
forum: Hardware
---

### Post by ninepillars on 2008-06-02
Hi all,

I'm running a dual boot with Gutsy and Windows XP. I've been trying to watch Netflix online using my XP installation for a few days now, but the problem is that in my infinite wisdom (read: stupidity) I shrank the Windows partition down to about 5GB and used the other 155GB on my hard drive for Gutsy when I installed it. I've freed up about as much disk space as a could, removing OpenOffice and several beloved vintage games, upgrading to SP3 and deleting old updates, but I'm still coming up short.

As a result of all this, I've concluded that adding a good 5-10GB of space on that partition will give my Windows some much-needed elbow room. I read an archived post about this that involves reinstalling either Windows, Ubuntu, or both, but I'd rather not go through all that at this point.

How can I shrink my Ubuntu (ext3) partition/expand my Windows (NTFS) partition without wreaking too much havoc on my system?

Thanks in advance,
Cullen D.

---

### Post by jimbob on 2008-06-02
Post the output of fdisk -l to begin with.

You may be able to shrink Ubuntu, create another partition then move Ubuntu into it.  Then tou can expand XP into some of Ubuntu's previous space, etc.

It depends on how much space Ubuntu is actually using.

---

### Post by ninepillars on 2008-06-02
Here's the fdisk output:

```
Disk /dev/hda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x20112011

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         730     5863693+   7  HPFS/NTFS
/dev/hda2           19051       20023     7815622+  83  Linux
/dev/hda3           18929       19050      979965   82  Linux swap / Solaris
/dev/hda4             731       18928   146175435   83  Linux

Partition table entries are not in disk order

Disk /dev/hdb: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00084cb4

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1          94      755023+  82  Linux swap / Solaris
/dev/hdb2   *          95        2011    15398302+  83  Linux
/dev/hdb3            2012        4866    22932787+  83  Linux
```

My /home partition (/dev/hda4) is the largest one. It's 137.2GB large and is only using about 19GB right now.

---

### Post by acron1 on 2008-06-02
You can do it with the gparted live CD [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by ninepillars on 2008-06-06
Thanks acron1, that did the trick!

---

