---
title: "SATA Link problems"
date: 2007-07-26
forum: Hardware &amp; Laptops
---

### Post by hooper82 on 2007-07-26
I'm installing a ubuntu file server.  The servers configuration - 

AMD 2500XP
Albatron KX18DS mother board
1 gig ram
Intel 1000/GT pro NIC
Promise SATA300 TX4 4 Port Controller
Promise SATA300 TX2 2 Port Controller

6x Seagate SATAII 320 gig drives (connected to promise controllers, not to mobo)
1x Seagate PATA 120 gig drive (connected to motherboard)
2x Samsung PATA 80 gig drives (connected to motherboard)


I originaly tryed loading the LTS server software, but it couldn't deal with my promise cards.  Once i moved to 7.04 things started working for me.  I got the server installed successfully into the 120 gig drive.  However, when I was copying data from one of the SATA drives to the 120, I kept getting an error.  I checked /var/log/messages and found - 

Jul 27 09:06:19 focssrv kernel: [41183.948968]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x14 (ATA bus error)
Jul 27 09:06:20 focssrv kernel: [41184.677860] ata1: soft resetting port
Jul 27 09:06:20 focssrv kernel: [41184.837651] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jul 27 09:06:50 focssrv kernel: [41214.815271] ata1.00: qc timeout (cmd 0xec)
Jul 27 09:06:50 focssrv kernel: [41214.815480] ata1.00: failed to IDENTIFY (I/O error, err_mask=0x104)
Jul 27 09:06:50 focssrv kernel: [41214.815540] ata1: failed to recover some devices, retrying in 5 secs
Jul 27 09:06:55 focssrv kernel: [41219.818161] ata1: hard resetting port
Jul 27 09:06:56 focssrv kernel: [41220.726900] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jul 27 09:06:56 focssrv kernel: [41220.791993] ata1.00: ata_hpa_resize 1: sectors = 625142448, hpa_sectors = 625142448
Jul 27 09:06:56 focssrv kernel: [41220.866858] ata1.00: ata_hpa_resize 1: sectors = 625142448, hpa_sectors = 625142448
Jul 27 09:06:56 focssrv kernel: [41220.866864] ata1.00: configured for UDMA/133
Jul 27 09:06:56 focssrv kernel: [41220.866875] ata1: EH complete
Jul 27 09:06:56 focssrv kernel: [41220.932172] SCSI device sda: 625142448 512-byte hdwr sectors (320073 MB)
Jul 27 09:06:56 focssrv kernel: [41220.936620] sda: Write Protect is off
Jul 27 09:06:56 focssrv kernel: [41220.945353] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA

Any ideas?
I really need to get this sorted before I build a RAID5 array on thoes drives.


Thanks in advance,
Hooper

---

### Post by ianare on 2007-07-27
with that many drives ... how many watts is the power supply? I set up a backup server with 5 drives: 1x IDE 100gb for OS, 4x SATA 500gb for storage. No optical or floppy drive. Similar speed processor/ram as you, maybe a bit faster (can't remember exactly), definitely intel CPU.

Anyway with a 500-watt power supply I would get weird data corruption errors sometimes. If I unplugged a drive, everything was OK ... After going to 700 watts, no problems. You may need even more, maybe a dual power supply setup. 

Also, are you using a hot swap drive trays? Those can cause errors sometimes. If you are using those, plug the drives directly into the SATA cable, re-test.

---

### Post by hooper82 on 2007-07-27
I'm currently running it on an antec 480watt true power supply.  No hot-swap trays all direct plugin.

I'll get another PSU and see if that works.   Thanks for your help!


Hooper

---

