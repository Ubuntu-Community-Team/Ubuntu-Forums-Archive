---
title: "install system can't see or access sdb"
date: 2009-01-21
forum: Installation &amp; Upgrades
---

### Post by alpage2 on 2009-01-21
I'm having a problem with the ubuntu 8.10 install. My old tower PC has two internal hard drives, presently running WinXP on sda1 (120GB), and edubuntu 8.04 on sdb (20GB), a Fujitsu MPD3173AT.

I was planning to do a clean install of ubuntu 8.10 on sdb, but the installer is only able to see and access the partitions on sda, which is not what I want - I would rather have ubuntu on sdb. Whether I choose guided or manual partitioning - the partitioner only offers the sda partitions for installing.

When the 'live CD' is run, /dev contains entries for the various partitions on sda, but there is no entry for sdb - does this mean the hardware protection has failed?

I guess as a last resort, I can try an online upgrade, but I would rather do a clean install if anyone can help with the sdb access. Particularly when the install disk will not get me out of trouble if the online upgrade does pear-shaped!

Are there any log files, etc., that I should post?

Thanks in anticipation
Alan

---

### Post by dabl on 2009-01-21
Probably the solution lies in your BIOS settings -- the Linux installer takes its cues from there.

Look at the mode settings in BIOS, for the hard drive bus.  If it is IDE, it may need to be set to "Primary Master", for example.  Also you don't want the hdd jumpered as "slave"  -- "CS" is the better jumper setting.

---

### Post by alpage2 on 2009-01-21
> **dabl said:**
> Probably the solution lies in your BIOS settings -- the Linux installer takes its cues from there.

Look at the mode settings in BIOS, for the hard drive bus.  If it is IDE, it may need to be set to "Primary Master", for example.  Also you don't want the hdd jumpered as "slave"  -- "CS" is the better jumper setting.

Thanks for those tips - very useful - and very encouraging!

My BIOS settings are

IDE channel 0 master - corresponds to my sda drive
IDE channel 0 slave - my sdb drive
IDE channel 1 is assigned to my two dvd drives (slave and master)
IDE channels 2 and 3 are unassigned.

Are there any advantages/disadvantages to either:

leave the sdb drive on channel 0, and just change the jumper to 'CS'

or attach it instead as a master on channel 2 or 3?

Thanks in anticipation..

Alan

---

### Post by dabl on 2009-01-22
If you can put the second hard drive on one of the unassigned IDE channels, set to "Master", and make sure the jumper is on "CS", I think you'll be able to use it as /dev/sdb and have it recognized correctly.

---

### Post by alpage2 on 2009-01-22
> **dabl said:**
> If you can put the second hard drive on one of the unassigned IDE channels, set to "Master", and make sure the jumper is on "CS", I think you'll be able to use it as /dev/sdb and have it recognized correctly.

Thanks for that. I have had a try, and still some problems:

Despite the BIOS listing a couple of unused channels, when I opened the case, there are only two IDE sockets, one in use for the two hard drives, and one in use by the two DVD drives, so I have left the connections as they are, but changed the jumper on the 'slave' fujitsu drive to 'cable select'.

Everything still works as before, with edubuntu 8.04 booting from the fujistsu drive.

However, again when I try to install ubuntu 8.10, the partitioner is unable to detect the fujitsu drive.

I took a look at dmesg, and the section that seems to deal with the IDE drives is below - there are entries for the sda drive - a Maxtor, and for the two DVD drives - a Pioneer and a TSST, but I don't see anything for the Fujitsu drive. Strange that 8.04 (and before) can see it, but 8.10 can't.

Any other suggestions will be most helpful. However, worst case scenario, I could do an online upgrade, or I have a spare 20Gb drive that I could substitute, or I could partition the maxtor drive, if there was no alternative.

Thanks again
Alan

dmesg extract:
> 
[    5.792286] ACPI: PCI Interrupt Link [ALKA] BIOS reported IRQ 0, using IRQ 20
[    5.792295] ACPI: PCI Interrupt Link [ALKA] enabled at IRQ 20
[    5.792311] pata_acpi 0000:00:0f.0: PCI INT B -> Link[ALKA] -> GSI 20 (level, low) -> IRQ 20
[    5.792431] pata_acpi 0000:00:0f.0: PCI INT B disabled
[    5.792465] pata_acpi 0000:00:0f.1: PCI INT A -> Link[ALKA] -> GSI 20 (level, low) -> IRQ 20
[    5.792505] pata_acpi 0000:00:0f.1: PCI INT A disabled
[    5.800328] sata_via 0000:00:0f.0: version 2.3
[    5.800365] sata_via 0000:00:0f.0: PCI INT B -> Link[ALKA] -> GSI 20 (level, low) -> IRQ 20
[    5.800461] sata_via 0000:00:0f.0: routed to hard irq line 11
[    5.808255] scsi0 : sata_via
[    5.808594] scsi1 : sata_via
[    5.808688] ata1: SATA max UDMA/133 cmd 0x9400 ctl 0x9800 bmdma 0xa400 irq 20
[    5.808695] ata2: SATA max UDMA/133 cmd 0x9c00 ctl 0xa000 bmdma 0xa408 irq 20
[    5.892327] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00004c0107002db7]
[    5.920133] usb 5-3: new high speed USB device using ehci_hcd and address 2
[    6.012061] ata1: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[    6.090510] Marking TSC unstable due to TSC halts in idle
[    6.191610] usb 5-3: configuration #1 chosen from 1 choice
[    6.216075] ata2: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[    6.216257] pata_via 0000:00:0f.1: version 0.3.3
[    6.216295] pata_via 0000:00:0f.1: PCI INT A -> Link[ALKA] -> GSI 20 (level, low) -> IRQ 20
[    6.217435] scsi2 : pata_via
[    6.217607] scsi3 : pata_via
[    6.221446] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xac00 irq 14
[    6.221453] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xac08 irq 15
[    6.497326] ata3.00: ATA-7: Maxtor 6Y120L0, YAR41BW0, max UDMA/133
[    6.497336] ata3.00: 240121728 sectors, multi 16: LBA 
[    6.512451] ata3.00: configured for UDMA/133
[    6.592040] usb 2-2: new full speed USB device using uhci_hcd and address 4
[    6.676425] ata4.00: ATAPI: PIONEER DVD-RW  DVR-106D, 1.07, max UDMA/33
[    6.676456] ata4.01: ATAPI: TSSTcorpCD/DVDW TS-H552U, US01, max UDMA/33
[    6.684284] ata4.00: configured for UDMA/33
[    6.700274] ata4.01: configured for UDMA/33
[    6.700505] scsi 2:0:0:0: Direct-Access     ATA      Maxtor 6Y120L0   YAR4 PQ: 0 ANSI: 5
[    6.706947] scsi 3:0:0:0: CD-ROM            PIONEER  DVD-RW  DVR-106D 1.07 PQ: 0 ANSI: 5
[    6.707728] scsi 3:0:1:0: CD-ROM            TSSTcorp CD/DVDW TS-H552U US01 PQ: 0 ANSI: 5
[    6.744485] scsi 2:0:0:0: Attached scsi generic sg0 type 0
[    6.744568] scsi 3:0:0:0: Attached scsi generic sg1 type 5
[    6.744657] scsi 3:0:1:0: Attached scsi generic sg2 type 5
[    6.781895] usb 2-2: configuration #1 chosen from 1 choice
[    6.807571] Driver 'sd' needs updating - please use bus_type methods
[    6.811523] sd 2:0:0:0: [sda] 240121728 512-byte hardware sectors (122942 MB)
[    6.811571] sd 2:0:0:0: [sda] Write Protect is off
[    6.811578] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.811640] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.811817] sd 2:0:0:0: [sda] 240121728 512-byte hardware sectors (122942 MB)
[    6.811853] sd 2:0:0:0: [sda] Write Protect is off
[    6.811859] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.811918] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.811928]  sda: sda1 sda2 <<4>Driver 'sr' needs updating - please use bus_type methods
[    6.844663]  sda5 >
[    6.845001] sd 2:0:0:0: [sda] Attached SCSI disk
[    6.856893] sr0: scsi3-mmc drive: 32x/32x writer cd/rw xa/form2 cdda tray
[    6.856906] Uniform CD-ROM driver Revision: 3.20
[    6.857143] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    6.863482] sr1: scsi3-mmc drive: 1x/48x writer cd/rw xa/form2 cdda tray
[    6.863672] sr 3:0:1:0: Attached scsi CD-ROM sr1
[   10.690046] ISO 9660 Extensions: Microsoft Joliet Level 3
[   10.713971] ISO 9660 Extensions: RRIP_1991A
[   11.094368] aufs 20080922
[   11.117138] loop: module loaded
[   11.482627] squashfs: version 3.3 (2007/10/31) Phillip Lougher
[   77.748307] udevd version 124 started
[   79.572717] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   79.747228] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   80.162032] Linux agpgart interface v0.103


---

### Post by dabl on 2009-01-22
Yep, they can be tricky -- the Fujitsu is still in hiding.  I would experiment with that BIOS Channel 0 mode setting -- can both drives be set as "Master", or both as "Slave"?  If the Fujitsu can also be set to "Master", that might be all it needs.  Or it might work with the Fujitsu as master and the Maxtor as slave, if there has to be one of each on the channel.

Also, you changed the jumper on the Fujitsu to "CS" -- but is the Maxtor jumpered as something else?  I've had best results with IDE drives jumpered to "CS" and then let BIOS control them through the cable.

And what about the cable connections -- is the Fujitsu on the middle connector or the end connector?

Final thought (well, maybe final) -- you could put a hard drive and an optical drive on each channel.  I'd give that approach real high odds of working, if none of the other methods produces results.

---

### Post by alpage2 on 2009-01-24
> **dabl said:**
> Yep, they can be tricky -- the Fujitsu is still in hiding.  I would experiment with that BIOS Channel 0 mode setting -- can both drives be set as "Master", or both as "Slave"?  If the Fujitsu can also be set to "Master", that might be all it needs.  Or it might work with the Fujitsu as master and the Maxtor as slave, if there has to be one of each on the channel.

Also, you changed the jumper on the Fujitsu to "CS" -- but is the Maxtor jumpered as something else?  I've had best results with IDE drives jumpered to "CS" and then let BIOS control them through the cable.

And what about the cable connections -- is the Fujitsu on the middle connector or the end connector?

Final thought (well, maybe final) -- you could put a hard drive and an optical drive on each channel.  I'd give that approach real high odds of working, if none of the other methods produces results.

Thanks, dable, for all those ideas. It gave me plenty of options to try. It turned out that the big Maxtor drive (my windows 'C' drive - so it needs to remain the master) was originally set to CS, and when the Fujitsu drive is slave or CS, or master, the install system still can't see it - and same results when Maxtor jumpered as master. The Maxtor is on the end of the cable, but when I switched the cable positions of the two hard drives, the Fujitsu was listed by the BIOS as the 'Master', and the Maxtor not visible to the BIOS, at all. Maybe switching the Maxtor back to CS would have made it visible as a slave, but this is not what I want, since windows needs the larger Maxtor drive, which therefore needs to be the Master.

So with Maxtor as master, the fujitsu drive seems invisible to the install system, at all combinations of settings. However, with Maxtor as master, it can see my other spare drive - a SAMSUNG SV2044D - an old IDE drive from the same era as the Fujitsu, although probably not quite as old.

Based on the above, I think your final suggestion will work,  but not with my current IDE cables. Due to the physical locations and orientations of the drives, I would need some IDE cables with a longer gap between the master and slave connectors - and I am not sure how easy they would be to come by. Possibly the newer round-cabled type would accomodate the necessary twists and turns better than my old ribbon-type cables.

But I do know with my current cabling that I can either do an online upgrade with the Fujitsu, or swap it for the Samsung, so I'll do one or the other.

Many thanks for all your help - it has been an eye-opener - I've learned a thing or two in the process ;-)

Thanks again
Alan

---

### Post by dabl on 2009-01-26
Hmmm -- I wonder if that middle connector on your ribbon cable has a problem?

You should be able, if you find the right Radio Shack or store with computer accessories, to find longer IDE ribbon cables.  Not to mention online cable vendor sites.

Also, it isn't exactly rocket science to make one of those cables, if you can find the connectors.  They are basically just snap/pressed onto the square-cut end of the ribbon, and there is a little metal "knife" for each pin, that cuts through the insulation and makes contact with the wire that it is aligned to.  You just need to do a careful job with some pliers, to put even pressure on the two halves of the connector.

Good luck with it!

---

