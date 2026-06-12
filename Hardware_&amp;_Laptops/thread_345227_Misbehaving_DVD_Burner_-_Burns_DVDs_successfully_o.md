---
title: "Misbehaving DVD Burner - Burns DVDs successfully only sometimes"
date: 2007-01-24
forum: Hardware &amp; Laptops
---

### Post by Kethinov on 2007-01-24
My DVD burner has been displaying some odd characteristics lately. I'm concerned that it might be failing. What it does is burn DVDs to 100% of completion, then it reports that it mysteriously failed to burn the DVD after it's finished 100%. I put the DVD back in the drive, the computer thinks the DVD is blank. Sometimes it does this behavior, sometimes it does other behavior. I have no idea why.

This is a k3b debug log of one such session:

```

System
-----------------------
K3b Version: 0.12.17

KDE Version: 3.5.5
QT Version:  3.3.6
Kernel:      2.6.17-10-generic
Devices
-----------------------
NU DVDRW DDW-061 BX03 (/dev/hdc, ) at /media/cdrom0 [CD-R; CD-RW; CD-ROM; DVD-ROM; DVD+R; DVD+RW] [DVD-ROM; DVD+RW; DVD+R; CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; SAO/R96R; RAW/R16; RAW/R96R]

K3b
-----------------------
Size of filesystem calculated: 2085773

Used versions
-----------------------
growisofs: 6.1

growisofs
-----------------------
Executing 'builtin_dd if=/dev/fd/0 of=/dev/hdc obs=32k seek=0'
/dev/hdc: "Current Write Speed" is 6.1x1385KBps.
   3080192/4271663104 ( 0.1%) @0.7x, remaining 138:34 RBU 100.0%
  27951104/4271663104 ( 0.7%) @5.3x, remaining 22:46 RBU 100.0%
etc...
4112089088/4271663104 (96.3%) @5.8x, remaining 0:20 RBU 100.0%
4139778048/4271663104 (96.9%) @5.8x, remaining 0:16 RBU 100.0%
:-[ WRITE@LBA=1eefe0h failed with SK=3h/ASC=0Ch/ACQ=00h]: Input/output error
:-( write failed: Input/output error
/dev/hdc: flushing cache
/dev/hdc: closing track
/dev/hdc: closing disc

growisofs command:
-----------------------
/usr/bin/X11/growisofs -Z /dev/hdc=/dev/fd/0 -use-the-force-luke=notray -use-the-force-luke=tty -use-the-force-luke=tracksize:2085773 -dvd-compat -speed=6 -use-the-force-luke=bufsize:32m 

mkisofs
-----------------------
2085773
INFO: UTF-8 character encoding detected by locale settings.
 Assuming UTF-8 encoded filenames on source filesystem,
 use -input-charset to override.
  0.02% done, estimate finish Tue Jan 23 20:45:52 2007
  0.05% done, estimate finish Tue Jan 23 20:45:52 2007
etc...
 97.95% done, estimate finish Tue Jan 23 20:54:49 2007
 97.97% done, estimate finish Tue Jan 23 20:54:48 2007
/usr/bin/X11/mkisofs: Connection reset by peer. cannot fwrite 32768*1

mkisofs command:
-----------------------
/usr/bin/X11/mkisofs -gui -graft-points -volid BSG Season 1 DVDRip eps 4-9 -volset  -appid K3B THE CD KREATOR (C) 1998-2005 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-kethinov/k3bXmEPPa.tmp -rational-rock -hide-list /tmp/kde-kethinov/k3bdhOSja.tmp -joliet -hide-joliet-list /tmp/kde-kethinov/k3b3RmD5a.tmp -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-kethinov/k3bENlNbb.tmp 

```

Is my DVD burner dying?

---

### Post by TomG on 2007-02-07
I have same problem since I upgraded to Edgy. :(
It seems impact "only" DVD-VIDEO for me.
Any clue ?
TomG

---

