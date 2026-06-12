---
title: "how to put SATA drives in standby?"
date: 2005-06-15
forum: Hardware &amp; Laptops
---

### Post by Neduz on 2005-06-15
Hi,

For my IDE disks I use hdparm to set the stanby timeout, but for my sata disk it says:
/dev/sda:
 setting standby to 120 (10 minutes)
 HDIO_DRIVE_CMD(setidle1) failed: Inappropriate ioctl for device

The sata controller is an onboard ICH5 from Intel and the disk is a Seagate ST3200822AS, Linux 2.6.11.5 kernel.

Another problem is hddtemp, it says:
/dev/sda: ATA     ST3200822AS     : S.M.A.R.T. not available

I've googled for these questions a while, but found nothing but other people having the same questions. Maybe someone here knows how to put the sata disk in standby?

thx,

Neduz

---

