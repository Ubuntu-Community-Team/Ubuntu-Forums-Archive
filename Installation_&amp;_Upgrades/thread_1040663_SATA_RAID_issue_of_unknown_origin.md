---
title: "SATA RAID issue of unknown origin"
date: 2009-01-15
forum: Installation &amp; Upgrades
---

### Post by freakalad on 2009-01-15
I'm trying to do an installation on a machine (ex-XP), but keep getting cryptic errors. Unable to locate an updated BIOS for this mobo.

Mobo: MSI N1996 aka 650GM-L
2 SATA drives w RAID unconfigured (keeping things simple for now)
Couple of IDE DVD's
NVidia GPU (besides the point @ this stage)

I use a mini.iso installation, with local network cache/repository

Start up system with "Advanced User Installation", which allows me to specify some initial settings (NIC & repository), and then to continue installation via remote SSH terminal.

All good & fine so far.

But when I try to "Detect disks", I get some serious errors & my dmesg spits out the following:

[  304.440226] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0010dc00005c26f2]
[  334.408042] ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[  334.408058] ata5.00: cmd a0/01:00:00:80:00/00:00:00:00:00/a0 tag 0 dma 16512 in
[  334.408060]          cdb 5a 00 2a 00 00 00 00 00  80 00 00 00 00 00 00 00
[  334.408062]          res 40/00:03:00:00:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
[  334.408067] ata5.00: status: { DRDY }
[  339.452013] ata5: link is slow to respond, please be patient (ready=0)
[  344.436013] ata5: device not ready (errno=-16), forcing hardreset
[  344.436024] ata5: soft resetting link
[  344.600388] ata5: nv_mode_filter: 0x39f&0x39f->0x39f, BIOS=0x0 (0xc0000000) ACPI=0x39f (120:600:0x12)
[  344.608295] ata5.00: configured for MWDMA2
[  344.608314] ata5: EH complete
[  374.608035] ata5.00: limiting speed to MWDMA1:PIO4
[  374.608044] ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[  374.608054] ata5.00: cmd a0/01:00:00:80:00/00:00:00:00:00/a0 tag 0 dma 16512 in
[  374.608056]          cdb 5a 00 2a 00 00 00 00 00  80 00 00 00 00 00 00 00
[  374.608058]          res 40/00:03:00:00:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
[  374.608062] ata5.00: status: { DRDY }
[  379.612012] ata5: link is slow to respond, please be patient (ready=0)
[  384.652012] ata5: device not ready (errno=-16), forcing hardreset
[  384.652023] ata5: soft resetting link
[  384.816382] ata5: nv_mode_filter: 0x19f&0x39f->0x19f, BIOS=0x0 (0xc0000000) ACPI=0x39f (120:600:0x12)
[  384.824315] ata5.00: configured for MWDMA1
[  384.824332] ata5: EH complete
[  414.824032] ata5.00: limiting speed to PIO4
[  414.824041] ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[  414.824051] ata5.00: cmd a0/01:00:00:80:00/00:00:00:00:00/a0 tag 0 dma 16512 in
[  414.824053]          cdb 5a 00 2a 00 00 00 00 00  80 00 00 00 00 00 00 00
[  414.824055]          res 40/00:03:00:00:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
[  414.824060] ata5.00: status: { DRDY }
[  419.840013] ata5: link is slow to respond, please be patient (ready=0)
[  424.844013] ata5: device not ready (errno=-16), forcing hardreset
[  424.844025] ata5: soft resetting link
[  425.008383] ata5: nv_mode_filter: 0x1f&0x39f->0x1f, BIOS=0x0 (0xc0000000) ACPI=0x39f (120:600:0x12)
[  425.016288] ata5.00: configured for PIO4
[  425.016305] ata5: EH complete
[  425.017417] sr1: scsi3-mmc drive: 1x/52x cd/rw xa/form2 cdda tray
[  425.017619] sr 4:0:0:0: Attached scsi CD-ROM sr1
[  426.356607] end_request: I/O error, dev sr0, sector 20344
[  426.356619] Buffer I/O error on device sr0, logical block 5086
[  426.638991] end_request: I/O error, dev sr0, sector 20344
[  426.638997] Buffer I/O error on device sr0, logical block 5086
[  426.689716] end_request: I/O error, dev sr0, sector 20344
[  426.689723] Buffer I/O error on device sr0, logical block 5086
[  426.740513] end_request: I/O error, dev sr0, sector 20344
[  426.740520] Buffer I/O error on device sr0, logical block 5086
[  426.791156] end_request: I/O error, dev sr0, sector 20344
[  426.791163] Buffer I/O error on device sr0, logical block 5086
[  426.841880] end_request: I/O error, dev sr0, sector 20344
[  426.841884] Buffer I/O error on device sr0, logical block 5086
[  426.892671] end_request: I/O error, dev sr0, sector 20344
[  426.892675] Buffer I/O error on device sr0, logical block 5086
[  427.129115] end_request: I/O error, dev sr0, sector 20344
[  427.129118] Buffer I/O error on device sr0, logical block 5086
[  427.179866] end_request: I/O error, dev sr0, sector 20344
[  427.179870] Buffer I/O error on device sr0, logical block 5086
[  428.354343] Intel ISA PCIC probe: not found.
[  431.716663] device-mapper: uevent: version 1.0.3
[  431.718208] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [email]dm-devel@redhat.com[/email]
[  467.328596] NET: Registered protocol family 10


I get the following for a "fdisk -l", which leads me to believe that the drives ARE available, but for some reason the system/installer refuses to use it:

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3e2e3e2d
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       14593   117218241   83  Linux
Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x40694068
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14593   117218241   83  Linux


I'm at a loss

Any ideas?

Only only next step I can think of is introducing a small IDE to use for boot & OS, & the SATA's for home, var, or data

---

### Post by freakalad on 2009-01-19
I've tried going with the latest stock-standard debian mini/net release.
Still a no-go. 

Seems to be a hardware compatability issue, as the hardware is functional under windoze

May have to resort to making use of an IDE drive for the OS, and then use the SATA's for /home (& maybe a bit of swap.)

---

### Post by cariboo on 2009-01-19
> 426.356607] end_request: I/O error, dev sr0, sector 20344
[ 426.356619] Buffer I/O error on device sr0, logical block 5086
[ 426.638991] end_request: I/O error, dev sr0, sector 20344
[ 426.638997] Buffer I/O error on device sr0, logical block 5086
[ 426.689716] end_request: I/O error, dev sr0, sector 20344
[ 426.689723] Buffer I/O error on device sr0, logical block 5086
[ 426.740513] end_request: I/O error, dev sr0, sector 20344
[ 426.740520] Buffer I/O error on device sr0, logical block 5086
[ 426.791156] end_request: I/O error, dev sr0, sector 20344
[ 426.791163] Buffer I/O error on device sr0, logical block 5086
[ 426.841880] end_request: I/O error, dev sr0, sector 20344
[ 426.841884] Buffer I/O error on device sr0, logical block 5086
[ 426.892671] end_request: I/O error, dev sr0, sector 20344
[ 426.892675] Buffer I/O error on device sr0, logical block 5086
[ 427.129115] end_request: I/O error, dev sr0, sector 20344
[ 427.129118] Buffer I/O error on device sr0, logical block 5086
[ 427.179866] end_request: I/O error, dev sr0, sector 20344
[ 427.179870] Buffer I/O error on device sr0, logical block 5086

The above are cd disk read errors, try to burn the mini.iso at the slowest speed possible and try again.

Edit: to help with your raid setup have a look at the [FakeRaidHowto]("http://help.ubuntu.com/community/FakeRaidHowto").

JIm

---

