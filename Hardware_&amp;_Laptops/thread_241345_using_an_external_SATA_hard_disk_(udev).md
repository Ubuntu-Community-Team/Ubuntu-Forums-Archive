---
title: "using an external SATA hard disk (udev?)"
date: 2006-08-22
forum: Hardware &amp; Laptops
---

### Post by aurelieng on 2006-08-22
Hi all,

I'm a lucky guy with a SATA 500Go (HDS725050KLA360) disk inside an IcyBox (external rack w/ SATA interface), and a PCMCIA/SATA controller. The card is recognized upon insertion in my laptop, as reported by lcpci 8) :

0000:04:00.0 RAID bus controller: Silicon Image, Inc. SiI 3112 [SATALink/SATARaid] Serial ATA Controller (rev 02)

Everything works fine, but I have some questions about how to make it work a bit like a USB mass-storage device, which I find very convenient. I'm thus looking for the two following behaviours, and I suppose that they have to do something with udev (Am I wrong?). :-k 

1. Detect the disk without having to unplug/replug the card:
----------
If the rack is turned on and connected to the PCMCIA card when I insert it into my laptop, the disk is assigned a /dev/sd? automatically. The problem is that if I turn on or connect the rack to the PCMCIA card afterward, the disk is not recognized. ](*,) 

My first question is then: is it possible to have the disk automatically without having to unplug/replug the PCMCIA card, and how ?

2. Statically assign /dev/sdX to the disk
----------
Depending whether an external CF/SD/... card read is connected to my laptop, the disk is either recognized as /dev/sdb1 or /dev/sdg1. This is a bit annoying as I have to manually mount it after looking at the logs. I would like it to be automatically mounted in /mnt/external for example, no matters the device node that is chosen :rolleyes: . I guess that udev can do it for me, but I don't clearly understand how to use it. I've added the following lines in a file I created as /etc/udev/rules/10-esata.rules: 

BUS=="scsi", SYSFS{model}=="HDS725050KLA360 ", NAME="sdb"
 ACTION="add", KERNEL=="sdb1", RUN+="/bin/mount -t ext3 -o rw,noauto,sync,dirsync,/dev/sdb /mnt/external", OPTIONS="last_rule"
 ACTION="remove", KERNEL=="sdb", RUN+="/bin/umount -l /mnt/external", OPTIONS="last_rule"

This way, even if i can mount the disk as if it was /dev/sdb, it is still created as /dev/sdg1 in the logs. I believe /dev/sdb is a kind of "alias" created by udev for /dev/sdg1. If so, would it be possible to avoid this "alias" and only make sure that the disk is mounted at the right place ? How safe it is to automatically umount it after it has been disconnected ? :-k 

Thanks a lot for your answers, :) 

Aurélien

PS: the performance of such disk is quite high, hdparm -t -T /dev/sdX reports

Timing cached reads: 3676 MB in 2.00 seconds = 1837.89 MB/sec
Timing buffered disk reads: 186 MB in 3.02 seconds = 61.67 MB/sec

:cool:

---

### Post by aurelieng on 2006-08-24
Well, I finally had some time to look around and found out a rule to automatically mount the disk:

ACTION="add", BUS=="scsi", SYSFS{model}=="HDS725050KLA360 ", RUN+="/bin/mount -t ext3 -o rw,noauto /dev/%k /mnt/icybox", OPTIONS="last_rule"
 
As I do not want to use neither the sync nor the dirsync options of mount to take the full advantage of the performance of this disk, I choosed no to unmount the disk automatically. Otherwise, a rule like that should help:

ACTION="remove", BUS=="scsi", SYSFS{model}=="HDS725050KLA360 ", RUN+="/bin/umount -l /mnt/icybox", OPTIONS="last_rule"

---

### Post by dixon on 2007-03-20
It's not working for me :\

/etc/udev/rules.d/10-my.rules
```
ACTION="add", BUS=="scsi", SYSFS{model}=="HDS722516VLSA80 ", RUN+="/usr/bin/nautilus /media/hda1", OPTIONS="last_rule"

```After adding file I've restarted udev (sudo /etc/init.d/udev restart)

I hope, I've done everything good :(

BTW /media/hda1 is always mounted - I'm using nautilus just to see if it's working, but nautilus never showed up :(

BTW2 After automounting through udev the drive also showed up in "Places"? Cause if I mount it in terminal it won't show up in "Places" :(

---

