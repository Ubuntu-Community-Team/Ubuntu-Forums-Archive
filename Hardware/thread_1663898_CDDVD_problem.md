---
title: "CD/DVD problem"
date: 2011-01-10
forum: Hardware
---

### Post by EricJonsson on 2011-01-10
So I'm running a HTPC box with Ubuntu Server 10.04, Lucid.

```
eric@Gimli:~$ uname -a
Linux Gimli 2.6.32-27-server #49-Ubuntu SMP Thu Dec 2 02:05:21 UTC 2010 x86_64 GNU/Linux
```Problem is, I can't access CD's or DVD's. Like, it won't let me mount them. My devices are set up like this:

```
eric@Gimli:~$ ls -l /dev/{cd,dvd}*
lrwxrwxrwx 1 root root 3 2011-01-10 13:02 /dev/cdrom -> sr0
lrwxrwxrwx 1 root root 3 2011-01-10 13:02 /dev/cdrw -> sr0
lrwxrwxrwx 1 root root 3 2011-01-10 13:02 /dev/dvd -> sr0
lrwxrwxrwx 1 root root 3 2011-01-10 13:02 /dev/dvdrw -> sr0
eric@Gimli:~$ file /dev/sr0
/dev/sr0: block special
```At first I actually thought it was a hardware problem, but I've now tried with two different pieces of DVD drives with no success. I'm currently using this one:

```
eric@Gimli:/media$ dmesg | grep CD
[    1.931721] ata2.00: ATAPI: TSSTcorp CDDVDW SH-S223C, SB04, max UDMA/100
[    3.534510] scsi 1:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-S223C  SB04 PQ: 0 ANSI: 5
[    3.541691] Uniform CD-ROM driver Revision: 3.20
[    3.542003] sr 1:0:0:0: Attached scsi CD-ROM sr0
```Now, if I try to mount a DVD:

```
eric@Gimli:~$ sudo mount /dev/cdrom /media/cdrom
mount: /dev/sr0: unknown device
eric@Gimli:~$ sudo mount -t udf /dev/cdrom /media/cdrom
mount: no medium found on /dev/sr0
```The drive doesn't show up when I run [FONT=Courier New]sudo blkid[/FONT], (is this normal?) but the [FONT=Courier New]eject[/FONT] command works.

... Which is absolutely puzzling to me. Any help troubleshooting this is *much *appreciated, the fiancee is nagging me about her favorite DVD flicks. :popcorn:

---

### Post by ubermike on 2012-01-05
I am having a very similar problem. I am unable to mount a DVDs, it is like it is just not recognised. CDs play without a problem.

The weird part is that the problem just manifested out of no where. I was reading DVDs just fine one minute then the next it refused to recognise it.

I have tried loading every codec under the sun but that did not fix the problem. I have also upgraded to the latest Ubuntu (11.10) but the problem still persists.

Any help would be greatly appreciated.

---

### Post by EricJonsson on 2012-01-05
I should note that for me back in January, it was indeed a hardware problem -- I had hooked up too many devices to my (rather weak) PSU, the DVD-drive was the straw that broke its back. It was strong enough to recognize it during boot, but not enough to keep the laser firing. :)

---

