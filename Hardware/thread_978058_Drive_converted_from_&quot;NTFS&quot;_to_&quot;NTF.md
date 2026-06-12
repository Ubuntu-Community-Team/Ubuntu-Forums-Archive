---
title: "Drive converted from &quot;NTFS&quot; to &quot;NTFS/HPFS&quot;!  Can I fix?"
date: 2008-11-10
forum: Hardware
---

### Post by Ash44455666 on 2008-11-10
Okay, so my external Hard Drive has three partitions.  NTFS, Ext3, and Swap.  I formatted the Ext3 and installed Ubuntu 8.10 to it, but I accidentally installed GRUB to the NTFS partition and now it's corrupted.  The information on the NTFS partition is important to me, and although it wouldn't be the end of the world if I lost it, I would **really** like to recover it.

Old post, before I realized it was corrupted, not changed per se:
> Sorry if this is the wrong category, I wasn't particularly sure which one would fit best =\.

I installed Ubuntu 8.10 to my external hard drive, but I accidentally installed GRUB to the NTFS partition.  I didn't realize that until I loaded up Windows XP, and it couldn't read the drive... said it was still "RAW".  EXT2IFS said that it was a "NTFS/HPFS" file system, and I did a little googling but couldn't find anything that would let me either convert, or read from, that partition.

When I booted from Linux again (on the external hard drive ... at least I did something correctly =|) I couldn't even find the partition, let alone mount and browse it.


Is there ANY way at all I can recover this partition, so that I can use it again like normal?  The partition itself is about 430GB or 440GB.

Thank you for any help you can give me :neutral:

---

### Post by cdtech on 2008-11-10
You can use your XP install disk to "fixmbr" on the window's drive. This will get you back into the XP drive on boot.

My bad...
You said you installed to the partition? not the MBR? am I correct?

---

### Post by Ash44455666 on 2008-11-10
Sorry, yes, I installed it to the partition.  I'm not sure why, but it seems to be "NTFS/HPFS" and not just "NTFS" anymore, and I can't access it from either Windows or Linux.  This partition is what I use as a backup for *all* my stuff, including from past installations (like Vista home premium.  My laptop originally came with it, but a couple months later I replaced it with Ubuntu, making a backup of all my files/documents first)

---

### Post by cdtech on 2008-11-10
You might be able to fix the NTFS partition using "testdisk". This utility is in the "Universe" repositories and is under the System Administration section. If your having partition issues after installing to a partition this will probably be your best bet.

```
sudo apt-get install testdisk
```
Then run as root:
```
sudo testdisk
```

---

### Post by Ash44455666 on 2008-11-10
Ok, so I installed TestDisk and ran it as root (via sudo).  I chose the correct drive (the Seagate 500GB external hard drive), chose the "HPFS - NTFS" partition, and chose 'change partition' or something like that.  It gave me a whole bunch of choices, and I'm not sure exactly which would be the best choice.  I want it to be NTFS, but the closest one is "Syrinx Boot-bad NTFS".  Here's a screenshot with all the choices:

[IMG]http://img293.imageshack.us/img293/503/screenshotpr6.png[/IMG]

---

### Post by cdtech on 2008-11-10
Here is a step by step procedure for "testdisk". This may help you better than I can type. :)
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

Let me know if you get it fixed.

---

### Post by cariboo on 2008-11-10
Choose 07 as in on your list HPFS/NTFS is what Linux calls an NTFS partion. This is a partial listing of :

```
sudo fdisk -l
```

the result is this:

```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x51b6cc16

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10199    81920000    7  HPFS/NTFS
/dev/sda3           10200       30401   162272565    5  Extended
/dev/sda5           29697       30401     5662881   82  Linux swap / Solaris
/dev/sda6           12112       29696   141251481   83  Linux
/dev/sda7   *       10200       12111    15358077   83  Linux
```

note my Vista partition is /dev/sda1 and is listed as HPFS/NTFS.

You have some other problem that has nothing to do with the partition type.

JIm

---

### Post by Ash44455666 on 2008-11-10
I think you're right cariboo, when I had TestDisk try and read the files in the NTFS partition, it said it was corrupted or unreadable or something like that.

I'll try to use chkdsk to repair the partition (even though Windows can't recognize it at all), but is this also possible with TestDisk?  I'm not sure whether or not the provided tutorial pertains to my problem or not, because I don't have any deleted partitions.. just a, what seems to be, damaged one.

---

### Post by mrsteveman1 on 2008-11-10
Either HPFS was the original name of what is now NTFS or it evolved into NTFS over the years (when MS stopped playing nice with OS/2 and IBM i think...)

Either way its the same thing now.

---

### Post by Ash44455666 on 2008-11-10
> **mrsteveman1 said:**
> Either HPFS was the original name of what is now NTFS or it evolved into NTFS over the years (when MS stopped playing nice with OS/2 and IBM i think...)

Either way its the same thing now.

Thanks for the information!  Unfortunately, I just found out from both cariboo's last post, and TestDisk telling me it was unable to read from the partition, or something like that..

Edit: Also, just updated the thread with what appears to be my *real* problem

---

### Post by cdtech on 2008-11-10
Could you post the output of:
```
dd if=/dev/**sda1** bs=512 count=1 | hd
```
be sure to edit the drive allocation above with yours (sda1,sdb1 whichever)

---

### Post by Ash44455666 on 2008-11-10
drive allocation?  If you mean the NTFS drive I'm having trouble with, here was the output:
```
1+0 records in
1+0 records out
512 bytes (512 B) copied, 0.016291 s, 31.4 kB/s
00000000  eb 48 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.H.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  00 00 00 00 80 00 80 00  80 3a c6 37 00 00 00 00  |.........:.7....|
00000030  00 00 0c 00 00 00 00 00  c0 84 a3 03 00 00 03 02  |................|
00000040  ff 00 00 80 06 bb 94 39  00 08 fa 90 90 f6 c2 80  |.......9........|
00000050  75 02 b2 80 ea 59 7c 00  00 31 c0 8e d8 8e d0 bc  |u....Y|..1......|
00000060  00 20 fb a0 40 7c 3c ff  74 02 88 c2 52 be 7f 7d  |. ..@|<.t...R..}|
00000070  e8 34 01 f6 c2 80 74 54  b4 41 bb aa 55 cd 13 5a  |.4....tT.A..U..Z|
00000080  52 72 49 81 fb 55 aa 75  43 a0 41 7c 84 c0 75 05  |RrI..U.uC.A|..u.|
00000090  83 e1 01 74 37 66 8b 4c  10 be 05 7c c6 44 ff 01  |...t7f.L...|.D..|
000000a0  66 8b 1e 44 7c c7 04 10  00 c7 44 02 01 00 66 89  |f..D|.....D...f.|
000000b0  5c 08 c7 44 06 00 70 66  31 c0 89 44 04 66 89 44  |\..D..pf1..D.f.D|
000000c0  0c b4 42 cd 13 72 05 bb  00 70 eb 7d b4 08 cd 13  |..B..r...p.}....|
000000d0  73 0a f6 c2 80 0f 84 ea  00 e9 8d 00 be 05 7c c6  |s.............|.|
000000e0  44 ff 00 66 31 c0 88 f0  40 66 89 44 04 31 d2 88  |D..f1...@f.D.1..|
000000f0  ca c1 e2 02 88 e8 88 f4  40 89 44 08 31 c0 88 d0  |........@.D.1...|
00000100  c0 e8 02 66 89 04 66 a1  44 7c 66 31 d2 66 f7 34  |...f..f.D|f1.f.4|
00000110  88 54 0a 66 31 d2 66 f7  74 04 88 54 0b 89 44 0c  |.T.f1.f.t..T..D.|
00000120  3b 44 08 7d 3c 8a 54 0d  c0 e2 06 8a 4c 0a fe c1  |;D.}<.T.....L...|
00000130  08 d1 8a 6c 0c 5a 8a 74  0b bb 00 70 8e c3 31 db  |...l.Z.t...p..1.|
00000140  b8 01 02 cd 13 72 2a 8c  c3 8e 06 48 7c 60 1e b9  |.....r*....H|`..|
00000150  00 01 8e db 31 f6 31 ff  fc f3 a5 1f 61 ff 26 42  |....1.1.....a.&B|
00000160  7c be 85 7d e8 40 00 eb  0e be 8a 7d e8 38 00 eb  ||..}.@.....}.8..|
00000170  06 be 94 7d e8 30 00 be  99 7d e8 2a 00 eb fe 47  |...}.0...}.*...G|
00000180  52 55 42 20 00 47 65 6f  6d 00 48 61 72 64 20 44  |RUB .Geom.Hard D|
00000190  69 73 6b 00 52 65 61 64  00 20 45 72 72 6f 72 00  |isk.Read. Error.|
000001a0  bb 01 00 b4 0e cd 10 ac  3c 00 75 f4 c3 00 00 00  |........<.u.....|
000001b0  00 00 00 00 00 00 00 00  44 52 20 69 73 20 63 6f  |........DR is co|
000001c0  6d 70 72 65 73 73 65 64  00 0d 0a 50 72 65 73 73  |mpressed...Press|
000001d0  20 43 74 72 6c 2b 41 6c  74 2b 44 65 6c 20 74 6f  | Ctrl+Alt+Del to|
000001e0  20 72 65 73 74 61 72 74  0d 0a 00 00 00 00 00 00  | restart........|
000001f0  00 00 00 00 00 00 00 00  83 a0 b3 c9 00 00 55 aa  |..............U.|
00000200

```

---

### Post by cdtech on 2008-11-10
And also the output of:
```
sudo fdisk -l
```

---

### Post by Ash44455666 on 2008-11-10
okey dokey

```
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe28843d3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2             193        5467    42371437+   5  Extended
/dev/sda3   *        5468       16195    86172660    7  HPFS/NTFS
/dev/sda4           16196       24322    65271808    7  HPFS/NTFS
Partition 4 does not end on cylinder boundary.
/dev/sda5             193        5206    40274923+  83  Linux
/dev/sda6            5207        5467     2096451   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00070bf4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       58247   467868996    7  HPFS/NTFS
/dev/sdb2           58248       60801    20515005    5  Extended
/dev/sdb5           58248       60541    18426523+  83  Linux
/dev/sdb6           60542       60801     2088418+  82  Linux swap / Solaris

```

---

### Post by cdtech on 2008-11-10
That "dd" command was from the "sda1" partition?. The reason I ask is that the "sda1" parition should be corrupt and the "dd" command shows a good sector.

---

### Post by caljohnsmith on 2008-11-10
You can usually fix the boot sector of a NTFS partition with testdisk by doing the following:
```

sudo testdisk
```
After starting testdisk, choose "no log", choose the correct HDD and "proceed", choose "intel", choose "advanced", select the NTFS partition you want to fix, choose "boot", then choose "Backup BS"; if testdisk gives you an error about boot sectors not matching, then choose "write". That should fix the boot sector of that NTFS partition.

So which partition is it? If it is sda1 you'll also need to change its file system type.

---

### Post by Ash44455666 on 2008-11-10
> **caljohnsmith said:**
> You can usually fix the boot sector of a NTFS partition with testdisk by doing the following:
```

sudo testdisk
```
After starting testdisk, choose "no log", choose the correct HDD and "proceed", choose "intel", choose "advanced", select the NTFS partition you want to fix, choose "boot", then choose "Backup BS"; if testdisk gives you an error about boot sectors not matching, then choose "write". That should fix the boot sector of that NTFS partition.

So which partition is it? If it is sda1 you'll also need to change its file system type.

Thanks!  This fixed my problem, perfectly!  I rebooted the computer and loaded up Windows XP, and was able to open (and of course, browse) the drive just fine.  Also, I can still boot into the Ubuntu install on the external hard drive without a problem.


Thank you very much everyone for the help!

P.S. cdtech, it was the dd command for the "sdb1" partition, I believe, and it's on the 500GB hard drive (AKA, the external hard drive).  The one above is the internal hard drive, where the only problem is it has Windows installed :P

---

### Post by caljohnsmith on 2008-11-10
Glad to hear it worked; that testdisk program can really work wonders sometimes, even with proprietary file systems like NTFS (*cough* *cough*). Anyway, cheers and have fun with Ubuntu. :)

---

