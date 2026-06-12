---
title: "Express Card 54 eSATA problem"
date: 2010-08-29
forum: Hardware
---

### Post by sokairyk on 2010-08-29
I bought an Express Card 54 for my Acer 5920G that provides one eSATA and one SATA port to connect my external eSATA HDD's (Seagate 320GB & Verbatim 1TB).

I used a SATA to eSATA cable for connecting one HDD on the SATA port of the card.

The controller of the card is a JMB36X (Vendor: JMicro).

Under Windows using the drivers from the JMicro site, the controller and
both disks work fine. They both use NTFS filesystem.

Under Ubuntu 9.04 I experience instability with the eSATA port. I use scsiadd before mounting/unmounting the drives (if they're not plugged during boot).

Although randomly I have managed to have both drives to work after some time one of them will fail (gives an input / output error and the device disappears from the system).

When this happens or when I try to add with scsiadd the HDD on the eSATA port and then mount it one of my 2 cores hits 100% usage and under gnome-system-monitor there isn't any program that corresponds to that CPU usage.

I should also notice that most times during boot if both drives are connected one of them will give an error like (I don't remember exactly the messages):

Device connection changed: Status frozen.
SoftReset failed.
Device status error (-50)

I have checked both drives in Windows using: 

chkdsk /F /R /V /B

Also BIOS settings for my SATA controllers are under AHCI.

I know this is not a hardware problem because the controller and the disks work under Windows.

Any idea what should I do?

---

