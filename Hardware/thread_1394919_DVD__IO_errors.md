---
title: "DVD  I/O errors"
date: 2010-01-31
forum: Hardware
---

### Post by ghannemann on 2010-01-31
Hi

Seem to be having trouble with certain Samsung DVD -RW drives.
I am able to boot and install Ubuntu 9.04, 9.10 Desktop and server versions and Debian 5x in both 32 bit and 64bit systems using these drive.  However, after installation, mounting CD's seem to take a long time - longer than a minute in some cases.  The system log shows the following[INDENT] [FONT=Arial][SIZE=1]Jan 31 19:14:56 abcdef kernel: [   79.965886] Buffer I/O error on device sr0, logical block 2096896
Jan 31 19:14:56 abcdef kernel: [   79.965889] Buffer I/O error on device sr0, logical block 2096897
Jan 31 19:14:56 abcdef kernel: [   79.965892] Buffer I/O error on device sr0, logical block 2096898
Jan 31 19:14:56 abcdef kernel: [   79.965894] Buffer I/O error on device sr0, logical block 2096899
Jan 31 19:14:56 abcdef kernel: [   79.965897] Buffer I/O error on device sr0, logical block 2096900
Jan 31 19:14:56 abcdef kernel: [   79.965899] Buffer I/O error on device sr0, logical block 2096901
[/SIZE][/FONT][/INDENT]This seems to be the worst mounting Data CD's.  Once mounted, they appear to be perfectly functional. 
DVD Movies also generate similar errors but appear to mount successfully after a few seconds.
I have not tried burning any cd's or dvd's yet.
I use these drives on systems with and old AMD XP, Asus  A7S8X-MX (Using an SIS chipset), and more recent Intel Core-Duo, Gigabyte U  system.  In both cases the DVD-RW mode weres a Samsung SH-S222a (PATA) and SH-S223C (Sata).  The Drive that appears to work corectly as a Pioneer  218LBK (Sata).

Debian 5 installation do no seem to have these errors.

What may be problem here? 

Tanks
Gerhard

---

### Post by ghannemann on 2010-01-31
Anyone?

---

