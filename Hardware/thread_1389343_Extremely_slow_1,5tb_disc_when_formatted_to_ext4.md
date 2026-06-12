---
title: "Extremely slow 1,5tb disc when formatted to ext4"
date: 2010-01-24
forum: Hardware
---

### Post by pivot@pivpoint.no on 2010-01-24
Greetings!

I've set up a ubuntu server (9.10) to use as download server and filesharing server. I attached my 1,5tb seagate barracuda disc to the sata controller, full of files and with ntfs filesystem, and it all worked splendid. However, I was a bit unsatesfied with 30-40mb/s when copying in midnight commander so I figured I wanted a ext4 filesystem on that as well. My system disc (a 74gb WD 10 000 rpm disc) got ext4 so I assumed that would make it all better. Backed up the data on the disc, and reformatted with the command mkfs.ext4 /dev/sdb1. Only one partition on that drive, a primary partition.

When copying from the WD system drive, and to the Seagate drive I only get around 100-200kbytes/sec. That's horrible!

I upgraded the firmware and reformatted. Still extremely slow. I then reformatted to ntfs with windows, and voila! 30-50mb/sec again.

What's wrong?? 

sudo hdparm -tT /dev/hda

returns:
> /dev/sdb:
 Timing cached reads:   622 MB in  2.00 seconds = 310.77 MB/sec
 Timing buffered disk reads:  240 MB in  3.01 seconds =  79.85 MB/sec

...so doesnt seem to be any problems with the disc. 
Nothing wrong with the WD disc either:
> /dev/sda:
 Timing cached reads:   622 MB in  2.01 seconds = 310.12 MB/sec
 Timing buffered disk reads:  206 MB in  3.02 seconds =  68.16 MB/sec



Additional info from dmesg | grep ata:
> 
[    0.000000]  BIOS-e820: 000000009fff3000 - 00000000a0000000 (ACPI data)
[    0.000000]  modified: 000000009fff3000 - 00000000a0000000 (ACPI data)
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000] PERCPU: Embedded 30 pages at ffff8800019fe000, static data 90720 bytes
[    0.000000] Memory: 2566720k/2621376k available (5303k kernel code, 452k absent, 54204k reserved, 3013k data, 660k init)
[    0.226525] libata version 3.00 loaded.
[    0.482440] sata_nv 0000:00:07.0: version 3.5
[    0.482992] sata_nv 0000:00:07.0: PCI INT A -> Link[APSI] -> GSI 23 (level, low) -> IRQ 23
[    0.483103] sata_nv 0000:00:07.0: setting latency timer to 64
[    0.483194] scsi0 : sata_nv
[    0.483356] scsi1 : sata_nv
[    0.483511] ata1: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xd800 irq 23
[    0.483514] ata2: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xd808 irq 23
[    0.483586] ata1: SATA link down (SStatus 0 SControl 300)
[    0.483608] ata2: SATA link down (SStatus 0 SControl 300)
[    0.484035] sata_nv 0000:00:08.0: PCI INT A -> Link[APSJ] -> GSI 22 (level, low) -> IRQ 22
[    0.484104] sata_nv 0000:00:08.0: setting latency timer to 64
[    0.484159] scsi2 : sata_nv
[    0.484216] scsi3 : sata_nv
[    0.484369] ata3: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xc400 irq 22
[    0.484372] ata4: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xc408 irq 22
[    0.484572] pata_amd 0000:00:06.0: version 0.4.1
[    0.484635] pata_amd 0000:00:06.0: setting latency timer to 64
[    0.484702] scsi4 : pata_amd
[    0.484772] scsi5 : pata_amd
[    0.485472] ata5: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[    0.485475] ata6: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[    0.640038] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    0.660387] ata5.00: ATAPI: _NEC DVD_RW ND-4550A, 1.84, max UDMA/33
[    0.660412] ata5: nv_mode_filter: 0x739f&0x739f->0x739f, BIOS=0x7000 (0xc0000000) ACPI=0x701f (60:600:0x13)
[    0.661583] ata3.00: ATA-6: WDC WD740GD-00FLC0, 33.08F33, max UDMA/133
[    0.661585] ata3.00: 145226112 sectors, multi 1: LBA48 
[    0.700319] ata5.00: configured for UDMA/33
[    0.701492] ata3.00: configured for UDMA/133
[    0.860029] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    0.880415] ata4.00: ATA-8: ST31500341AS, SD1B, max UDMA/133
[    0.880417] ata4.00: 2930277168 sectors, multi 1: LBA48 NCQ (depth 0/32)
[    0.920426] ata4.00: configured for UDMA/133
[    1.091788] Write protecting the kernel read-only data: 7572k
[    1.998676] EXT4-fs (sda1): mounted filesystem with ordered data mode
[  690.850855] EXT4-fs (sdb1): mounted filesystem with ordered data mode

Any suggestions?

---

### Post by pivot@pivpoint.no on 2010-01-24
I've also tried formatting it to ext3 and ext2. Ext2 got 2 mb/s...

---

### Post by pivot@pivpoint.no on 2010-01-24
And I can add that I got the same problem on a new Seagate Barracuda 1,5tb disc I bought, plus an old Seagate Barracuda 500gb disc I tried earlier...

Getting frustrated :(

---

### Post by luffy_chan_19 on 2010-01-24
ext4,3, 2 space out the files when they are being wirtten to the rive, with an ntfs partition they just throw the files right on top of the most recent file writen onto the disk. maybe that is why idk im just throwin this out there maybe im right maybe im not idk right now i just got really depressed all of sudden becaue i just realised how sad my life is. i lay arround on my bed and search the web all day and reply to peoples tech problems on ubuntu... actually i have only recently started posting alot on ubuntu forums.

---

### Post by fourcheeze on 2011-02-11
Don't worry - you are not alone!

I'm having similar problems (extreme slowness) with two identical Seagate Barracuda 2TB drives. I think it must be something in the drive settings but I'm not sure how to go about testing it out.

hdparm -i says:


/dev/sdb:

 Model=ST32000542AS, FwRev=CC34, SerialNo=5XW29VH8
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs RotSpdTol>.5% }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=unknown, BuffSize=0kB, MaxMultSect=16, MultSect=16
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=3907029168
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
 AdvancedPM=yes: unknown setting WriteCache=enabled
 Drive conforms to: unknown:  ATA/ATAPI-4,5,6,7

 * signifies the current active mode


I notice that there are a few things there might be of concern - particular things like "Drive conforms to: unknown" - no idea how something can conform to an unknown.

Reading from the drive doesn't seem to be too bad, but writing is very poor - I'm getting write speeds of about 2MB per second - should be several orders of magnitude above that.

Any help working out where to start looking gratefully received.

Thanks.

---

### Post by pivot@pivpoint.no on 2011-02-13
Can't remember what I did to fix this, but I think I installed a newer version og Ubuntu Server. Cus now it works great. I got two 1,5tb seagate barracuda discs in software raid and they both work like a charm. I think it must have been some issue with drivers in whatever ubuntu version I used back then....

Tnx though. Hope you all get it working!

---

