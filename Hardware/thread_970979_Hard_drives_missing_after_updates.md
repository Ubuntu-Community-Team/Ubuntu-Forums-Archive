---
title: "Hard drives missing after updates"
date: 2008-11-04
forum: Hardware
---

### Post by kextyn on 2008-11-04
I'm running 8.04.1 64bit Server with a RAID5 array of 7 disks on a Supermicro AOC-SAT2-MV8 SATA2 controller.  Right now I can't get any of the drives on the Supermicro controller to show up in fdisk -l.  I just moved to a new apartment but I was very careful when moving this PC so I don't think that's the issue.  

I was thinking the card wasn't working right so I reseated it and reseated every SATA data and power cable in the system.  The card is showing all of the drives during POST but once Ubuntu boots it doesn't see them.  If I do a lspci I do see the controller listed though.

The only thing I can think of is when I moved it out of the old apartment it may have been the first time it has been restarted since a very recent dist-upgrade which brought me from something like 2.6.19-??-server to 2.6.24-21-server.

---

### Post by kextyn on 2008-11-04
If it helps the controller uses the Marvell 88SX6081 chip.  I believe the driver it uses is Sata_mv.

---

### Post by kextyn on 2008-11-05
Ok, I may have messed something up.  I followed the directions on this post because it seemed to be the closest to my problem that I could find:

[http://ubuntuforums.org/showthread.php?t=959019&highlight=sata_mv](http://ubuntuforums.org/showthread.php?t=959019&highlight=sata_mv)

And now I'm stuck at an initramfs prompt.

---

### Post by RaZoR1394 on 2008-11-09
What I can say is that I had the same problem with a card using:

02:00.0 SCSI storage controller: Marvell Technology Group Ltd. 88SX7042 PCI-e 4-port SATA-II (rev ff)

and the fix in the link you provided worked for me.

What I did as well was to remove some leftover arguments in menu.lst from the Intrepid alpha time.

all_generic_ide floppy=off pci=nomsi

---

### Post by RaZoR1394 on 2008-11-09
Turns out something is really wrong. Even though I can see my drives again  I get crc errors and the computer locks up partially.

I'm abandoning this ship.

---

