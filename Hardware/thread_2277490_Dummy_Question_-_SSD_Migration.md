---
title: "Dummy Question - SSD Migration"
date: 2015-05-09
forum: Hardware
---

### Post by Quarkrad on 2015-05-09
Apologies for this stupid question - done a bit of researching but still not clear.  I'm currently running 14.04 on a 1TB HD that has a partition for storage - I have another 1TB hd for Backup.  I'm thinking of migrating to ssd, which means a re-install, but I can't afford the largest ssd's on the market.  So ........... I'm thinking, get a smaller ssd, to hold 14.04 and run my PC, and keep one of my 1TB for data storage (music, photos, video files etc).  But ......  at the moment I have a large partition (on my 1TB hd) and another 1TB drive for Backup.   Using a smaller ssd and one 1TB storage drive I have no Backup.  Can you use three drives?   The ssd to run my pc, one of my 1TB hdds for storage and the other 1TB drive for Backup?   You can normally only have 2 HDs in a PC - does this change for ssd?  (Note - I use 14.04 99.9% of the time but I do dual boot with win7 because of the occasional need to 'have to use Windows').

---

### Post by dino99 on 2015-05-09
see your mobo doc to know how many devices can be handled, and check the psu power (as a limit to run them)
[http://powersupplycalculator.net/](http://powersupplycalculator.net/)

---

### Post by Bucky Ball on 2015-05-09
Never heard of a limitation to how many drives, of any kind, you can put in the box. Best way is to have a look inside and see what cabling you have coming out of the power supply and if there is another slot on the motherboard to plug more drives. Three drives isn't an issue if the motherboard has the slots (I have four drives in my desktop and one of them is an SSD, plus an optical drive). 

Your other option is to purchase an external hard drive case and stick your other 1Tb drive in that (and a better option as you have another backup NOT on the machine ...). They are reasonably inexpensive now. If you can use eSATA or USB3 to connect with you computer, better as faster. Fast as an internal drive. USB2 drive not so. 

The easiest way I've found of migrating installs is Clonezilla. Here's a few links to get you going. 

Home site:
[http://clonezilla.org/](http://clonezilla.org/)

Create image:
[http://rbgeek.wordpress.com/2013/04/14/how-to-use-clonezilla-to-backup-hard-drive-and-create-recovery-iso-image/](http://rbgeek.wordpress.com/2013/04/14/how-to-use-clonezilla-to-backup-hard-drive-and-create-recovery-iso-image/)

Create recovery ISO:
[https://rbgeek.wordpress.com/tag/using-clonezilla-to-create-iso-image/](https://rbgeek.wordpress.com/tag/using-clonezilla-to-create-iso-image/)

Partition cloning step by step:
[http://cdonner.com/partition-cloning-with-clonezilla.htm](http://cdonner.com/partition-cloning-with-clonezilla.htm)

Create Live media (with pics):
[http://clonezilla.org/fine-print-live-doc.php?path=./clonezilla-live/doc/04_Create_Recovery_Clonezilla/01-clonezilla-boot-menu.doc#01-clonezilla-boot-menu.doc](http://clonezilla.org/fine-print-live-doc.php?path=./clonezilla-live/doc/04_Create_Recovery_Clonezilla/01-clonezilla-boot-menu.doc#01-clonezilla-boot-menu.doc)

---

### Post by efflandt on 2015-05-11
Number of available drive bays do not necessarily matter. See how many SATA connectors are on your motherboard, or maybe even dmesg in Linux would give you a clue. I currently have 1 hd, 1 ssd, and 1 CD/DVD drive connected.```
efflandt@XPS-8100-1404:~$ cat /var/log/dmesg | grep SATA
[    0.697134] ata1: SATA max UDMA/133 abar m2048@0xf9ff4000 port 0xf9ff4100 irq 41
[    0.697137] ata2: SATA max UDMA/133 abar m2048@0xf9ff4000 port 0xf9ff4180 irq 41
[    0.697138] ata3: SATA max UDMA/133 abar m2048@0xf9ff4000 port 0xf9ff4200 irq 41
[    0.697140] ata4: SATA max UDMA/133 abar m2048@0xf9ff4000 port 0xf9ff4280 irq 41
[    0.697143] ata6: SATA max UDMA/133 abar m2048@0xf9ff4000 port 0xf9ff4380 irq 41
[    1.016171] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.340372] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.660572] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.008786] ata4: SATA link down (SStatus 0 SControl 300)
[    2.328970] ata6: SATA link down (SStatus 0 SControl 300)
```In an older computer with IDE drives (when drives had less capacity)  with only 2 available drive bays, I actually had 4 hard drives mounted in it (besides floppy and DVD). There were holes to mount 2 additional hard drives on the frame of the PC.

---

### Post by leunam12 on 2015-05-14
I have 2 SSD's and one HDD in my PC. As long as you have enough connectors and power I don't think there is a limitation to the number of drives you can have. 

Also, I went from HDD to SSD without doing a new install. I shrank my HDD home partition with parted magic and then used clonezilla to  move the installation from the HDD to the SSD; I had no problems whatsoever. In clonezilla you have to select "advanced" instead of beginner and select the option that skips checking the destination disk's size.

---

