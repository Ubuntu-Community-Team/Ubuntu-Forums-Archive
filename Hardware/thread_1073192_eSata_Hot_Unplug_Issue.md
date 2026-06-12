---
title: "eSata Hot Unplug Issue"
date: 2009-02-18
forum: Hardware
---

### Post by pmagid on 2009-02-18
1) I have a GIGABYTE GA-MA78GM-S2H motherboard which has an onboard eSata port and supports AHCI.
2) I have a SATA drive in a Thermaltake BlakX enclosure.
3) Once I turned on AHCI (and rebooted) I am able to hotplug the drive and the drive is recognized on the fly. (i.e. no reboot required)
4) No matter what I do (i.e. disconnect the drive or shut off the Blakx etc) the drives are not removed from the system.
5) I have run lshal -m while connecting the drive and the messages look normal.  However, there is absolutely no activity displayed when I disconnect the drive.
6) To remove the drive from the system I have to issue: "echo 1 |sudo tee -a /sys/bus/scsi/drivers/sd/5\:0\:0\:0/delete"
7) When I issue the command mentioned in item 6 above the drive is correctly removed from the system.   If I don't do this when I shut down the machine I get the following message and things seem to freeze up "scsi 5:0:0:0: rejecting I/O to dead device"
8) I am using Ubuntu 8.10 with the 2.6.27-11-server kernel.

So, is there any way to get eSata hot _un_plugging to work?

Any help greatly appreciated!

Paul

---

