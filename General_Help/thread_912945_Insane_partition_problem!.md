---
title: "Insane partition problem!"
date: 2008-09-07
forum: General Help
---

### Post by Zalbor on 2008-09-07
Long read, but please try to stay with me... Basic parts in bold.

I have an acer laptop with vista, on which I installed Ubuntu. So my partitions were like this, after installing it:

1)Acer's recovery partition, about 10GB
2)Vista partition, about 110GB
3)Extended partition with:
[INDENT]a)Root ubuntu partition, about 6GB
b)Home ubuntu partition, about 100GB[/INDENT]
4)Acer Arcade partition

I decided to install XP on the computer as well. To do this, I made the Vista partition smaller (from within Vista itself) then used gparted to enlarge the extended partition, and make a new logical partition inside it: NTFS with about 10GB, where I planned to install XP.

The plan was this: Install XP on the new partition, restore grub using the ubuntu live CD, then make an entry for XP in menu.lst.

I started the XP installation and picked the partition to install it in. After it copied the initial files, it rebooted and said it couldn't boot from the hard drive. I booted from the Ubuntu CD and ran gparted.
**First surprise: It showed my entire hard drive as unallocated.**

I tried to restore grub anyway, and surprisingly grub found partitions. After putting it back, I rebooted and got into Ubuntu with no problem (except that **the partition number had changed; (hd0,4) instead of (hd0,3)**).

**Second surprise: Gparted still showed the entire hard drive as unallocated.**
I tried to use "sudo fdisk -l /dev/sda" to see what it said.
**Third surprise:**
```
omitting empty partition (5)

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdd3ec4e5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1274    10233373+  12  Compaq diagnostics
/dev/sda2   *        1275       14580   106876924    6  FAT16
Partition 2 does not end on cylinder boundary.
/dev/sda3           14581       29977   123676402+   5  Extended
/dev/sda4           15856       16584     5855661   83  Linux
/dev/sda5           14581       15855    10241374+   7  HPFS/NTFS
/dev/sda6           16585       29977   107579241   83  Linux
```
**(Linux partitions were supposed to be together, there were supposed to be 2 NTFS partitions plus the two special ones).**

In the past I had erased the partition table of a hard drive and managed to fix it by using gpart, a program that guesses partitions by scanning the hard drive. So I tried to use it again, to see what it would find (sudo gpart /dev/sda).
**Fourth surprise:**
```
** Error: invalid extended ptbl found at sector(234227700).

Begin scan...
Possible partition(Windows NT/W2K FS), size(9993mb), offset(0mb)
Possible partition(Windows NT/W2K FS), size(113992mb), offset(9993mb)
Possible partition(Windows NT/W2K FS), size(113992mb), offset(123986mb)
Possible partition(Windows NT/W2K FS), size(494mb), offset(237978mb)

End scan.

Checking partitions...
Partition(OS/2 HPFS, NTFS, QNX or Advanced UNIX): primary 
Partition(OS/2 HPFS, NTFS, QNX or Advanced UNIX): primary 
Partition(OS/2 HPFS, NTFS, QNX or Advanced UNIX): primary 
Partition(OS/2 HPFS, NTFS, QNX or Advanced UNIX): primary 
Ok.

Guessed primary partition table:
Primary partition(1)
   type: 007(0x07)(OS/2 HPFS, NTFS, QNX or Advanced UNIX)
   size: 9993mb #s(20466744) s(63-20466806)
   chs:  (0/1/1)-(1023/254/63)d (0/1/1)-(1273/254/60)r

Primary partition(2)
   type: 007(0x07)(OS/2 HPFS, NTFS, QNX or Advanced UNIX)
   size: 113992mb #s(233456576) s(20466810-253923385)
   chs:  (1023/254/63)-(1023/254/63)d (1274/0/1)-(15805/254/59)r

Primary partition(3)
   type: 007(0x07)(OS/2 HPFS, NTFS, QNX or Advanced UNIX)
   size: 113992mb #s(233456576) s(253923390-487379965)
   chs:  (1023/254/63)-(1023/254/63)d (15806/0/1)-(30337/254/59)r

Primary partition(4)
   type: 007(0x07)(OS/2 HPFS, NTFS, QNX or Advanced UNIX)
   size: 494mb #s(1012088) s(487379970-488392057)
   chs:  (1023/254/63)-(1023/254/63)d (30338/0/1)-(30400/254/56)r
```

So apparently this only guessed the primary partitions, which look fine...

---

### Post by Zalbor on 2008-09-07
I also ran gpart with the -f option, which makes it scan the hard drive entirely:
```
** Error: invalid extended ptbl found at sector(234227700).

Begin scan...
Possible partition(Windows NT/W2K FS), size(9993mb), offset(0mb)
Possible partition(Windows NT/W2K FS), size(113992mb), offset(9993mb)
Possible partition(Windows NT/W2K FS), size(10001mb), offset(114369mb)
Possible partition(Windows NT/W2K FS), size(113992mb), offset(123986mb)
Possible extended partition at offset(124370mb)
   Possible partition(Linux ext2), size(5718mb), offset(124370mb)
   Possible partition(Linux ext2), size(105057mb), offset(130088mb)
Possible partition(Windows NT/W2K FS), size(494mb), offset(237978mb)
End scan.

Checking partitions...

* Warning: Discarded 3 overlapping partition guesses.
Partition(OS/2 HPFS, NTFS, QNX or Advanced UNIX): primary 
Partition(OS/2 HPFS, NTFS, QNX or Advanced UNIX): primary 
Partition(OS/2 HPFS, NTFS, QNX or Advanced UNIX): primary 
Partition(OS/2 HPFS, NTFS, QNX or Advanced UNIX): primary 
Ok.

Guessed primary partition table:
Primary partition(1)
   type: 007(0x07)(OS/2 HPFS, NTFS, QNX or Advanced UNIX)
   size: 9993mb #s(20466744) s(63-20466806)
   chs:  (0/1/1)-(1023/254/63)d (0/1/1)-(1273/254/60)r

Primary partition(2)
   type: 007(0x07)(OS/2 HPFS, NTFS, QNX or Advanced UNIX)
   size: 113992mb #s(233456576) s(20466810-253923385)
   chs:  (1023/254/63)-(1023/254/63)d (1274/0/1)-(15805/254/59)r

Primary partition(3)
   type: 007(0x07)(OS/2 HPFS, NTFS, QNX or Advanced UNIX)
   size: 113992mb #s(233456576) s(253923390-487379965)
   chs:  (1023/254/63)-(1023/254/63)d (15806/0/1)-(30337/254/59)r

Primary partition(4)
   type: 007(0x07)(OS/2 HPFS, NTFS, QNX or Advanced UNIX)
   size: 494mb #s(1012088) s(487379970-488392057)
   chs:  (1023/254/63)-(1023/254/63)d (30338/0/1)-(30400/254/56)r
```


That says somewhat more...

So, is there anything I can do to save my data (and possibly try me endeavor again)? What strikes me as most strange is that gparted shows no partition while fdisk shows some, and none of them are right. And also that I'm able to work with my system perfectly well, as I'm doing right now.

---

### Post by rbmorse on 2008-09-07
I would use [http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page). Download the .iso and create the CD, and then boot the machine with the damaged drive with that.  Once logged in, use the included "testdisk" utility to identify and restore lost partitions. 

Testdisk and the systemrescueCD has saved me on more than one occasion.

---

