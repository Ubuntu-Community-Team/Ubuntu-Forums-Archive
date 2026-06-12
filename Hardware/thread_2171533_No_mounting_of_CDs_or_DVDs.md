---
title: "No mounting of CDs or DVDs"
date: 2013-08-31
forum: Hardware
---

### Post by Kevin_Crow on 2013-08-31
I've read a number of threads of past users who've had this problem, but have had no success thus far imitating their solutions.  Currently I am trying with a CD-rom, but the issue seems to be the same with a DVD.  I am fairly new to Linux beyond basic file system navigation.

root@ckc-Dimension-4600C:/media# eject -n
eject: device is `/dev/sr0'


root@ckc-Dimension-4600C:/media# ls -al /dev/cd*
lrwxrwxrwx 1 root root 3 Aug 31 07:23 /dev/cdrom -> sr0
lrwxrwxrwx 1 root root 3 Aug 31 07:23 /dev/cdrw -> sr0


root@ckc-Dimension-4600C:/media# cat /var/log/dmesg | egrep '(CD|DVD)'
[    0.700483] ata2.00: ATAPI: HL-DT-STCD-RW/DVD-ROM GCC-4241N, A100, max UDMA/33
[    1.054221] scsi 1:0:0:0: CD-ROM            HL-DT-ST RW/DVD GCC-4241N A100 PQ: 0 ANSI: 5
[    1.057845] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.058058] sr 1:0:0:0: Attached scsi CD-ROM sr0
root@ckc-Dimension-4600C:/media# 

root@ckc-Dimension-4600C:/media# sudo mount /media/cdrom0/ -o unhide
mount: can't find /media/cdrom0/ in /etc/fstab or /etc/mtab

root@ckc-Dimension-4600C:/media# sudo mount /dev/cdrom/sr0 
mount: can't find /dev/cdrom/sr0 in /etc/fstab or /etc/mtab

ckc@ckc-Dimension-4600C:/media$ udisks --mount /dev/sr0
Mount failed: Error mounting: mount: no medium found on /dev/sr0


ckc@ckc-Dimension-4600C:/media$ sudo mount -t iso9660 /dev/sr0 /cdrom
mount: no medium found on /dev/sr0
ckc@ckc-Dimension-4600C:/media$ sudo mount /dev/sr0 /cdrom
mount: no medium found on /dev/sr0

I very much like Linux - just wish I could get it fully functioning!
-Kevin Crow, TEMPO Networks, Newark NJ

---

