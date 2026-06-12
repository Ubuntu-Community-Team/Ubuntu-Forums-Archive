---
title: "Install does not see SCSI Raid drives"
date: 2006-04-04
forum: Hardware &amp; Laptops
---

### Post by ndhskp on 2006-04-04
Hi I am trying to install Breezy 5.10 onto an HP LC3 Netserver.  It has a 1GB of ram and 3 SCSI drives and a CD-ROM drive.  Also i960 is there.

When I try to install the Breezy the install starts then durring the scroll it shows i2o failed error code -110.  And then it continues on showing the Adaptec AIC-7880 as being reconized.  I can get all the way to the hardrive setup but it shows blank, meaning no hard drives are listed.

How the heck do I install onto an SCSI raid system.  The system board bios is set to boot from CD-ROM and hard drive boot is from the raid.  The SCSI raid bios is set up I think?  Are there any special bios setting I need to do.  I used the adapter card bios to set up the 3 SCSI drives as a logical drive that is handled by the bios.  But linux shows the bios being disabled.  I am very confused.> Adaptec AIC-7880
Bus:00h
Device:0Ah
BIOS information
IRQ:09
I/O Port Address:F800h

---

