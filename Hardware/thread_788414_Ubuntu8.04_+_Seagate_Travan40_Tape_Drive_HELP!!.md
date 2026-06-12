---
title: "Ubuntu8.04 + Seagate Travan40 Tape Drive??? HELP!!"
date: 2008-05-09
forum: Hardware
---

### Post by joshlindem on 2008-05-09
Hey everyone, I've looked through the archives and found some questions on this very topic, but I've never found an answer for it. I did at one time have this working when I was using SUSE. After switching to Ubuntu over a year ago, I've never been able to get it working since than.

I don't get it. It shows up in Ubuntu's syslog shown below, but I can't seem to mount it or access it.
I do notice there are some errors in this log that may be referring to the tape drive, but I'm not sure.

Can anyone please help me get this working again?

> 
May 7 15:11:06 tux kernel: [ 35.810347] ata1.00: ATA-7: Maxtor 7L300R0, BAJ41G20, max UDMA/133
May 7 15:11:06 tux kernel: [ 35.810352] ata1.00: 586114704 sectors, multi 16: LBA48
May 7 15:11:06 tux kernel: [ 35.810373] ata1.01: ATAPI: BENQ DVD DUAL DW1610, B8B9, max UDMA/33
May 7 15:11:06 tux kernel: [ 35.826253] ata1.00: configured for UDMA/100
May 7 15:11:06 tux kernel: [ 35.996849] ata1.01: configured for UDMA/33
May 7 15:11:06 tux kernel: [ 36.748140] ieee1394: Host added: ID:BUS[0-00:1023] GUID[000000301b282c19]
May 7 15:11:06 tux kernel: [ 38.319567] ata2.00: ATAPI: Seagate STT3401A, 309I, max PIO3
May 7 15:11:06 tux kernel: [ 38.491425] ata2.00: configured for PIO3
May 7 15:11:06 tux kernel: [ 38.491587] scsi 1:0:0:0: Direct-Access ATA Maxtor 7L300R0 BAJ4 PQ: 0 ANSI: 5
May 7 15:11:06 tux kernel: [ 38.494038] scsi 1:0:1:0: CD-ROM BENQ DVD DUAL DW1610 B8B9 PQ: 0 ANSI: 5
May 7 15:11:06 tux kernel: [ 38.511673] scsi 2:0:0:0: Sequential-Access Seagate STT3401A 309I PQ: 0 ANSI: 2
May 7 15:11:06 tux kernel: [ 38.519771] Driver 'sd' needs updating - please use bus_type methods
May 7 15:11:06 tux kernel: [ 38.519865] sd 1:0:0:0: [sda] 586114704 512-byte hardware sectors (300091 MB)
May 7 15:11:06 tux kernel: [ 38.519877] sd 1:0:0:0: [sda] Write Protect is off
May 7 15:11:06 tux kernel: [ 38.519880] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
May 7 15:11:06 tux kernel: [ 38.519896] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May 7 15:11:06 tux kernel: [ 38.519945] sd 1:0:0:0: [sda] 586114704 512-byte hardware sectors (300091 MB)
May 7 15:11:06 tux kernel: [ 38.519954] sd 1:0:0:0: [sda] Write Protect is off
May 7 15:11:06 tux kernel: [ 38.519956] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
May 7 15:11:06 tux kernel: [ 38.519971] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May 7 15:11:06 tux kernel: [ 38.519975] sda:<4>Driver 'sr' needs updating - please use bus_type methods
May 7 15:11:06 tux kernel: [ 38.531947] sd 1:0:0:0: Attached scsi generic sg0 type 0
May 7 15:11:06 tux kernel: [ 38.531968] scsi 1:0:1:0: Attached scsi generic sg1 type 5
May 7 15:11:06 tux kernel: [ 38.531988] scsi 2:0:0:0: Attached scsi generic sg2 type 1
May 7 15:11:06 tux kernel: [ 38.537668] sda1 sda2 <<6>osst :I: Tape driver with OnStream support version 0.99.4
May 7 15:11:06 tux kernel: [ 38.544825] osst :I: $Id: osst.c,v 1.73 2005/01/01 21:13:34 wriede Exp $
May 7 15:11:06 tux kernel: [ 38.544854] Driver 'osst' needs updating - please use bus_type methods
May 7 15:11:06 tux kernel: [ 38.554620] sda5 >
May 7 15:11:06 tux kernel: [ 38.554726] sd 1:0:0:0: [sda] Attached SCSI disk
May 7 15:11:06 tux kernel: [ 38.568666] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
May 7 15:11:06 tux kernel: [ 38.568671] Uniform CD-ROM driver Revision: 3.20
May 7 15:11:06 tux kernel: [ 38.568736] sr 1:0:1:0: Attached scsi CD-ROM sr0
May 7 15:11:06 tux kernel: [ 38.571224] st: Version 20070203, fixed bufsize 32768, s/g segs 256
May 7 15:11:06 tux kernel: [ 38.571251] Driver 'st' needs updating - please use bus_type methods
May 7 15:11:06 tux kernel: [ 38.571389] st 2:0:0:0: Attached scsi tape st0
May 7 15:11:06 tux kernel: [ 38.571391] st 2:0:0:0: st0: try direct i/o: yes (alignment 512 B)
May 7 15:11:06 tux kernel: [ 38.794251] Attempting manual resume


---

### Post by joshlindem on 2008-05-15
**BUMP**

This is a largely on-going problem I've found in Ubuntu that many users have asked for help on. Since this forum gets a lot of activity I'm going to keep this alive every so often.

---

### Post by joshlindem on 2008-06-08
**bump**

any forum admin or Ubuntu guru that can help with this?

---

