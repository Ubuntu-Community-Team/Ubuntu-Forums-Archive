---
title: "can't detect hard drive while trying to install"
date: 2008-12-06
forum: Installation &amp; Upgrades
---

### Post by kieranrimmer on 2008-12-06
Hi,

I've been trying to install kubuntu 8.04.1 on my brand new ASUS gladiator V1400 desktop.  This unit has a 500 GB hard drive.  The problem is that the installation CDs (both live and alternate) cannot detect the hard drive.  

It is possible to install version 8.10, but i would prefer to use the 8.04.1 with the earler version of KDE for reasons including:
1) it has a far superior adept package
2) it has good screen resolution control (unlike 8.10)

I've mucked around with some aspects of the bios in an attempt to rectify the problem, to no avail.  Examples of this mucking around include:
-removing a non-existent floppy drive from the list and boot list (this prevents the live CD from reaching KDE for some reason)
-changing and changing back the ATA/IDE Configuration

I've read some stuff about changing RAID options, but can't find anywhere to do it

In attempting to get it recognised in 8.04.1, i've used the live cd and opened a console, typing:

sudo fdisk -lu

This yields nothing.

If i then install 8.10 and type sudo fdisk -lu then I get this

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0007e80a

Device   Boot Start       End       Blocks        Id   System
/dev/sda1  *   63        955498004   477748971     83   Linux
/dev/sda2    955498005  976768064    10635030      5  Extended
/dev/sda5    976768068  976768064    10634998+    82  Linux swap / solaris  

After exhaustively googling and checking out forum threads, i really don't know what to do.

I've included a jpeg snapshot of the main bios setup screen if that's any help

[IMG]/home/rimmer/Desktop/imgp0586.jpg[/IMG]

Would greatly appreciate any help

Cheers

---

### Post by taurus on 2008-12-07
When you get to the partition screen, it says that you have no harddrive at all?  Have you tried the Manual option?

---

### Post by kieranrimmer on 2008-12-07
It doesn't detect any partitions to start with.  I've tried to manually insert, to no avail.  

The live CD just gives you a blank partition table, which you can't do anything with.  It doesn't detect the pre-existing partitions (from version 8.10).  Neither will it simply let you create new partitions

The alternate CD tells you that it has detected zero disk space and offers you a list of drivers, none of which work.

I've also tried going in first with gparted and either removing all partitions or placing the entire disk space in one big partition and the kubuntu 8.04.1 CDs still can't pick it up.

---

### Post by taurus on 2008-12-07
How did you create those two partitions, /dev/sda1 & /dev/sda5, because /dev/sda1 doesn't even start at the beginning of the harddrive?

Probably best to use gparted from the LiveCD to erase them all.  Then, create a partition and format it to ext3.  Hopefully the installer will detect it and will use the whole harddrive now.

---

### Post by kieranrimmer on 2008-12-07
The partitions were created when i installed 8.10, using the guided partitioning.

I'll give gparted a go and get right back to you

cheers

---

### Post by kieranrimmer on 2008-12-07
Okay, so i removed all visible partitions using gparted and replaced them with a single ext3 formatted filesystem.

The info gparted relayed for this partition is:

Partition   Filesystem   Size       Used        Unused        Flags

/dev/sda1     ext3       465.76   7.50 GiB    458.26 GiB

After this, I try the 8.04.8.04.1 live CD and choose the run kubuntu option and it just take me through to:

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12)  Built-in shell (ash)

From this i rebboted then tried the 8.04.1 alternate install CD.  Choosing the option install kubuntu, it comes up with:

[********]irq 19: nobody cared (try booting with the "irqpoll" option)
[********]handlers:
[********][<f8882b80>] (usb_hcd_irq+0x0/ox60 [usbcore])
[********]Disabling IRQ #19
[********]ata3.00: revalidation failed (errno=-5)

where ******* represents a bunch of numbers

This sits there for a while before a couple more lines flash by and it gets to the usual install procedure.  As usual, the disk detection fails

---

