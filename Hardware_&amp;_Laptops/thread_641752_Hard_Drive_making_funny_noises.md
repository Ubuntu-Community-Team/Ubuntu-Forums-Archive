---
title: "Hard Drive making funny noises"
date: 2007-12-15
forum: Hardware &amp; Laptops
---

### Post by subject117 on 2007-12-15
My hard drive sometimes makes funny clicking noises and my machine slows down considerably, then it recovers.  It sounds like the drive is doing something and the clicking noise is in regular intervals.  I fear that one of my drives is dying.

I looked in the logs and it seems that it had a problem with /dev/sdb.  Can someone read the log messages and tell me what it means?  Do I need to replace one of the drives?  Was there a mirroring problem? [both drives are mirrored in a RAID configuration]  These symptoms have appeared several times in the past week.

I researched this problem in the forum before posting, and I learned about smartctl, but unfortunately my drives do not support it.  Info about my drives and a copy of my system log is below.  Any help would be greatly appreciated.

root@Dell:/home/jim# smartctl -i /dev/sda
smartctl version 5.36 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

Device: ATA      Maxtor 7L250S0   Version: BANC
Serial number: L59DP9JH    L59DP9JH
Device type: disk
Local Time is: Sat Dec 15 20:23:47 2007 EST
Device does not support SMART
root@Dell:/home/jim# smartctl -i /dev/sdb
smartctl version 5.36 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

Device: ATA      Maxtor 7L250S0   Version: BANC
Serial number: L590VDVG    L590VDVG
Device type: disk
Local Time is: Sat Dec 15 20:23:49 2007 EST
Device does not support SMART

system log:
Dec 15 19:20:10 Dell kernel: [ 8126.376230] ata3.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Dec 15 19:20:10 Dell kernel: [ 8126.376236] ata3.01: (BMDMA stat 0x64)
Dec 15 19:20:10 Dell kernel: [ 8126.376241] ata3.01: cmd c8/00:18:e7:4d:4c/00:00:00:00:00/f1 tag 0 cdb 0x0 data 12288 in
Dec 15 19:20:10 Dell kernel: [ 8126.376243]          res 51/10:18:e7:4d:4c/00:00:00:00:00/f1 Emask 0x81 (invalid argument)
Dec 15 19:20:10 Dell kernel: [ 8126.455332] ata3.01: ata_hpa_resize 1: sectors = 488281250, hpa_sectors = 488281250
Dec 15 19:20:10 Dell kernel: [ 8126.466994] ata3.00: ata_hpa_resize 1: sectors = 488281250, hpa_sectors = 488281250
Dec 15 19:20:10 Dell kernel: [ 8126.467000] ata3.00: configured for UDMA/133
Dec 15 19:20:10 Dell kernel: [ 8126.474985] ata3.01: ata_hpa_resize 1: sectors = 488281250, hpa_sectors = 488281250
Dec 15 19:20:10 Dell kernel: [ 8126.474990] ata3.01: configured for UDMA/133
Dec 15 19:20:10 Dell kernel: [ 8126.475003] sd 2:0:1:0: SCSI error: return code = 0x08000002
Dec 15 19:20:10 Dell kernel: [ 8126.475006] sdb: Current [descriptor]: sense key: Aborted Command
Dec 15 19:20:10 Dell kernel: [ 8126.475009]     Additional sense: Recorded entity not found
Dec 15 19:20:10 Dell kernel: [ 8126.475013] Descriptor sense data with sense descriptors (in hex):
Dec 15 19:20:10 Dell kernel: [ 8126.475015]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
Dec 15 19:20:10 Dell kernel: [ 8126.475022]         01 4c 4d e7 
[B]Dec 15 19:20:10 Dell kernel: [ 8126.475026] end_request: I/O error, dev sdb, sector 21777895
Dec 15 19:20:10 Dell kernel: [ 8126.475030] raid1: sdb1: rescheduling sector 21777832[/B]
Dec 15 19:20:10 Dell kernel: [ 8126.475045] ata3: EH complete
Dec 15 19:20:10 Dell kernel: [ 8126.500800] SCSI device sda: 488281250 512-byte hdwr sectors (250000 MB)
Dec 15 19:20:10 Dell kernel: [ 8126.521898] sda: Write Protect is off
Dec 15 19:20:10 Dell kernel: [ 8126.521903] sda: Mode Sense: 00 3a 00 00
Dec 15 19:20:11 Dell kernel: [ 8126.576000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 15 19:20:11 Dell kernel: [ 8126.597552] SCSI device sdb: 488281250 512-byte hdwr sectors (250000 MB)
Dec 15 19:20:11 Dell kernel: [ 8126.624268] sdb: Write Protect is off
Dec 15 19:20:11 Dell kernel: [ 8126.624273] sdb: Mode Sense: 00 3a 00 00
Dec 15 19:20:11 Dell kernel: [ 8126.648379] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 15 19:20:44 Dell kernel: [ 8160.432739] ata3.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
Dec 15 19:20:44 Dell kernel: [ 8160.432748] ata3.01: cmd c8/00:08:e7:4d:4c/00:00:00:00:00/f1 tag 0 cdb 0x0 data 4096 in
Dec 15 19:20:44 Dell kernel: [ 8160.432750]          res 40/00:18:e7:4d:4c/00:00:00:00:00/f1 Emask 0x4 (timeout)
Dec 15 19:20:51 Dell kernel: [ 8167.419247] ata3: port is slow to respond, please be patient (Status 0xd0)
Dec 15 19:21:14 Dell kernel: [ 8190.377699] ata3: port failed to respond (30 secs, Status 0xd0)
Dec 15 19:21:14 Dell kernel: [ 8190.377705] ata3: soft resetting port
Dec 15 19:21:15 Dell kernel: [ 8190.542402] ata3.01: ata_hpa_resize 1: sectors = 488281250, hpa_sectors = 488281250
Dec 15 19:21:15 Dell kernel: [ 8190.550370] ata3.00: ata_hpa_resize 1: sectors = 488281250, hpa_sectors = 488281250
Dec 15 19:21:15 Dell kernel: [ 8190.558371] ata3.00: ata_hpa_resize 1: sectors = 488281250, hpa_sectors = 488281250
Dec 15 19:21:15 Dell kernel: [ 8190.558377] ata3.00: configured for UDMA/133
Dec 15 19:21:15 Dell kernel: [ 8190.566356] ata3.01: ata_hpa_resize 1: sectors = 488281250, hpa_sectors = 488281250
Dec 15 19:21:15 Dell kernel: [ 8190.566363] ata3.01: configured for UDMA/133
Dec 15 19:21:15 Dell kernel: [ 8190.566374] ata3: EH complete
Dec 15 19:21:15 Dell kernel: [ 8190.902328] SCSI device sda: 488281250 512-byte hdwr sectors (250000 MB)
Dec 15 19:21:15 Dell kernel: [ 8190.902661] sda: Write Protect is off
Dec 15 19:21:15 Dell kernel: [ 8190.902664] sda: Mode Sense: 00 3a 00 00
Dec 15 19:21:15 Dell kernel: [ 8190.903053] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
**Dec 15 19:21:15 Dell kernel: [ 8190.903119] raid1: sdb1: redirecting sector 21777832 to another mirror**
Dec 15 19:21:15 Dell kernel: [ 8190.903441] SCSI device sdb: 488281250 512-byte hdwr sectors (250000 MB)
Dec 15 19:21:15 Dell kernel: [ 8190.942978] sdb: Write Protect is off
Dec 15 19:21:15 Dell kernel: [ 8190.942984] sdb: Mode Sense: 00 3a 00 00
Dec 15 19:21:15 Dell kernel: [ 8190.943620] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 15 19:21:15 Dell kernel: [ 8190.944432] SCSI device sda: 488281250 512-byte hdwr sectors (250000 MB)
Dec 15 19:21:15 Dell kernel: [ 8190.944567] sda: Write Protect is off
Dec 15 19:21:15 Dell kernel: [ 8190.944570] sda: Mode Sense: 00 3a 00 00
Dec 15 19:21:15 Dell kernel: [ 8190.998527] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 15 19:21:15 Dell kernel: [ 8190.999811] SCSI device sdb: 488281250 512-byte hdwr sectors (250000 MB)
Dec 15 19:21:15 Dell kernel: [ 8191.000119] sdb: Write Protect is off
Dec 15 19:21:15 Dell kernel: [ 8191.000123] sdb: Mode Sense: 00 3a 00 00
Dec 15 19:21:15 Dell kernel: [ 8191.003162] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA

---

### Post by Sef on 2007-12-15
> y hard drive sometimes makes funny clicking noises and my machine slows down considerably, then it recovers. It sounds like the drive is doing something and the clicking noise is in regular intervals. I fear that one of my drives is dying.
[

B]Back up[/B] all your information and anything else you want to save.  Then install a new hard drive.  That funny clicking noise over time indicates a hard drive going bad.

---

### Post by dbqp on 2007-12-16
Could also be from Ubuntu spinning your drive too much...

Take a look at:

[http://ubuntuforums.org/showthread.php?t=531866]("http://ubuntuforums.org/showthread.php?t=531866")

It may be too late and you may want to listen to the previous poster, but on future installs you should be aware of this issue.

Hope it helps.

---

### Post by subject117 on 2007-12-22
As predicted by Sef, the drive went bad and Linux is only using one of my two mirrored drives.  The "good" one is making some funny noises too.

Of course I have a full backup completed, which I have been doing since before this whole mess started.  That computer is off and I will not turn it on again until I have new drives to put in it.

Both drives were under warantee and will be replaced by Dell.  They are both refurbished drives, and I assume the new ones will be refurbished too.  The drives I have now didn't last very long, maybe a year?  The original drives died [within a week of each other], now the replacement drives died.

I am kind of sick of refurbished drives, I don't think they have the same lifespan as new drives.

I was thinking maybe I could buy two, larger, new quality drives and put them in my machine and mirror them.  And then I could use one of the refurbished drives for less important stuff that doesn't need to be mirrored, and perhaps put the other one in my windows machine, which currently has a 28GB drive and is hurting for space.

Does that sound like a reasonable plan?  Does anyone have other suggestions that make sense and would help me improve the reliability of my system?

When doing partitioning in linux, what stuff would a wise person put on the mirrored part and what would go on an unmirrored disk?  How does one learn about disk partitioning and planning?

Thanks-Jim

---

