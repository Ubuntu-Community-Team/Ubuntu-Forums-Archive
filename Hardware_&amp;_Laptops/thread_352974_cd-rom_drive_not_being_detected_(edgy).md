---
title: "cd-rom drive not being detected (edgy)"
date: 2007-02-04
forum: Hardware &amp; Laptops
---

### Post by brettg on 2007-02-04
Hi all

I've just bought one of these; 

[http://www.pioneercomputers.com.au/products/info.asp?c1=3&c2=15&id=1688](http://www.pioneercomputers.com.au/products/info.asp?c1=3&c2=15&id=1688)

and I've installed edgy i386 on it.

Problem: The CD-ROM drive does not work (it is not hardware because it works fine when booting live CD)\

#mount /media/cdrom 
mount: special device /dev/scd0 does not exist

/etc/fstab says;

       /dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

ls -al /media says;

       lrwxrwxrwx  1 root root    6 2007-02-04 13:03 cdrom -> cdrom0
        drwxr-xr-x  2 root root 4096 2007-02-04 13:03 cdrom0

The problem is that /dev/scd0 doesn't exist.

So, why did the edgy installer decide that my cd-rom drive should be /dev/scd0 and what in fact should it be?

According to the specs of the machine, the DVD-ROM drive is SATA

Update: Since this is a new install, I went and re-installed with Dapper, same result as before. Looks like a SATA driver problem maybe?

Update: When I do lspci it tells me about the SATA controller;

0000:00:1f.2 IDE Interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controllers cc=IDE (Rev 02)

---

