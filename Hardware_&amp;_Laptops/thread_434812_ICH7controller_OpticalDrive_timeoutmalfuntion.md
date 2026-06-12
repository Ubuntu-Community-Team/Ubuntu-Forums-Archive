---
title: "ICH7controller OpticalDrive timeout/malfuntion"
date: 2007-05-06
forum: Hardware &amp; Laptops
---

### Post by TRat on 2007-05-06
Feisty install

Dell 9100 Dimension Desktop with ICH7 SATA controller.  SATA hard drives seem to function fine.  Optical (DVD=cdrom0 and CD=cdrom1) don't seem to respond.  Mounting and unmounting a CD are fine until one tries to get information then the timeouts occur.  K3b or K9copy cause a complete system freeze with hard reboot necessary.  Using the install CD and attempting to upgrade with packages from the CD cause the CD to lockup but machine is functional otherwise.

I believe this is a ata_piix problem.  I've tried to pass options to libata and rebuilt initrd (update-initramfs) but I don't know what I'm doing.  And I'm not sure how to pass parameters to the kernel to use ide_generic with DMA turned on which I've seen suggested.

Help is appreciated.

This is what is in /var/log/messages

May  6 07:14:25 dell kernel: [34019.754247] ata5: soft resetting port
May  6 07:14:26 dell kernel: [34020.400378] ata5.00: configured for UDMA/33
May  6 07:14:26 dell kernel: [34020.564066] ata5.01: configured for UDMA/33
May  6 07:14:26 dell kernel: [34020.564079] ata5: EH complete
May  6 07:14:27 dell kernel: [34021.561626]          res 18/01:01:01:14:eb/00:00:00:00:00/b0 Emask 0x2 (HSM violation)
May  6 07:14:27 dell kernel: [34021.562753] ata5: soft resetting port
May  6 07:14:28 dell kernel: [34021.891880] ATA: abnormal status 0xD0 on port 0x000101f7
May  6 07:14:28 dell kernel: [34021.891913] ata5.01: failed to IDENTIFY (I/O error, err_mask=0x2)
May  6 07:14:28 dell kernel: [34021.893032] ata5: failed to recover some devices, retrying in 5 secs
May  6 07:14:40 dell kernel: [34033.880877] ata5: port is slow to respond, please be patient (Status 0xd0)
May  6 07:15:03 dell kernel: [34056.857253] ata5: soft resetting port
May  6 07:15:03 dell kernel: [34057.504435] ata5.00: configured for UDMA/33
May  6 07:15:03 dell kernel: [34057.668107] ata5.01: configured for UDMA/33
May  6 07:15:03 dell kernel: [34057.668122] ata5: EH complete
May  6 07:15:03 dell kernel: [34057.669853] sr1: CDROM not ready.  Make sure there is a disc in the drive.
May  6 07:27:50 dell -- MARK --
May  6 07:33:28 dell kernel: [35160.618059] ata5.01: ATAPI check failed
May  6 07:33:28 dell kernel: [35160.618102]          res 51/21:03:00:00:20/00:00:00:00:00/b0 Emask 0x3 (HSM violation)
May  6 07:33:28 dell kernel: [35160.618127] ata5: soft resetting port
May  6 07:33:29 dell kernel: [35160.944521] ATA: abnormal status 0xD0 on port 0x000101f7
May  6 07:33:29 dell kernel: [35160.944549] ata5.01: failed to IDENTIFY (I/O error, err_mask=0x2)
May  6 07:33:29 dell kernel: [35160.944555] ata5: failed to recover some devices, retrying in 5 secs
May  6 07:33:41 dell kernel: [35172.925541] ata5: port is slow to respond, please be patient (Status 0xd0)
May  6 07:34:04 dell kernel: [35195.901916] ata5: soft resetting port
May  6 07:34:04 dell kernel: [35196.549078] ata5.00: configured for UDMA/33
May  6 07:34:04 dell kernel: [35196.712772] ata5.01: configured for UDMA/33
May  6 07:34:04 dell kernel: [35196.712785] ata5: EH complete

---

