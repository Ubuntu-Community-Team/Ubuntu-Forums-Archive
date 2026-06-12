---
title: "DVD/CD drive only reads CD"
date: 2009-07-16
forum: Hardware
---

### Post by dfaulkner on 2009-07-16
I just did a wipe & install upgrade to Jaunty. I've discovered that there's a problem with the system's DVD-R/CD-RW drive. For some reason it's not reading (commercial) DVD's like movies, etc. I don't have a data DVD to test, so I can't be sure if the problem persist there. CD's read fine however.

I seem to remember a similar problem from the deeps of time: something to do with changing out which driver it's using. Of course, I can't remember the details, and Google (for once) has failed me.

Anyone have any ideas?

(details below)

The drive is an IDE/ATAPI interface.

/proc/scsi/scsi says that the drive is
```

Host: scsi1 Channel: 00 Id: 00 Lun: 00
  Vendor: TEAC     Model: DVD+RW DV-W58E   Rev: D.0C
  Type:   CD-ROM                           ANSI  SCSI revision: 05

```/etc/fstab has the following entry:
```

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```Attempting to manually mount a DVD gives the following:
```

$ sudo mount -t udf /dev/scd0 /media/cdrom0/
mount: no medium found on /dev/sr0

```I also see the following in /var/log/(messages|syslog):
```

kernel: [ 4677.565626] UDF-fs: No VRS found
kernel: [ 5835.921561] cdrom: This disc doesn't have any tracks I recognize!
kernel: [ 5835.971407] end_request: I/O error, dev sr0, sector 0
kernel: [ 5835.971418] Buffer I/O error on device sr0, logical block 0
kernel: [ 5835.974646] end_request: I/O error, dev sr0, sector 0
kernel: [ 5835.974656] Buffer I/O error on device sr0, logical block 0

```/var/log/udev:
```

UDEV  [1247711823.178939] add      /devices/pci0000:00/0000:00:1f.1/host1/target1:0:0/1:0:0:0/block/sr0 (block)
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1f.1/host1/target1:0:0/1:0:0:0/block/sr0
SUBSYSTEM=block
DEVTYPE=disk
SEQNUM=1101
ID_CDROM=1
ID_CDROM_CD_R=1
ID_CDROM_CD_RW=1
ID_CDROM_DVD=1
ID_CDROM_DVD_PLUS_R=1
ID_CDROM_DVD_PLUS_RW=1
ID_CDROM_MRW=1
ID_CDROM_MRW_W=1
ID_VENDOR=TEAC
ID_VENDOR_ENC=TEAC\x20\x20\x20\x20
ID_MODEL=DVD+RW_DV-W58E
ID_MODEL_ENC=DVD+RW\x20DV-W58E\x20\x20
ID_REVISION=D.0C
ID_TYPE=cd
ID_BUS=scsi
ID_PATH=pci-0000:00:1f.1-scsi-1:0:0:0
GENERATED=1
DEVNAME=/dev/sr0
MAJOR=11
MINOR=0
DEVLINKS=/dev/block/11:0 /dev/scd0 /dev/disk/by-path/pci-0000:00:1f.1-scsi-1:0:0:0 /dev/cdrom /dev/cdrw /dev/dvd

```

---

### Post by jerrrys on 2009-07-17
[http://ubuntuforums.org/showthread.php?t=1196003](http://ubuntuforums.org/showthread.php?t=1196003)

[https://help.ubuntu.com/community/RestrictedFormats#Playing%20Restricted%20Formats](https://help.ubuntu.com/community/RestrictedFormats#Playing%20Restricted%20Formats)

[http://ubuntuforums.org/showthread.php?t=938471&highlight=dvd+playback](http://ubuntuforums.org/showthread.php?t=938471&highlight=dvd+playback)

[http://ubuntuforums.org/showthread.php?t=1155698&highlight=vlc](http://ubuntuforums.org/showthread.php?t=1155698&highlight=vlc)

may be an answer in there

---

### Post by dfaulkner on 2009-07-17
Thanks for the links.  I already installed ubuntu-restricted-extras and followed the Medibuntu setup as detailed in the following two urls:  
[LIST]
[*] [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)
[*] [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
[/LIST]
   The output I posted in my original message is what I see after I had applied the medibuntu stuff.

---

### Post by dfaulkner on 2009-07-17
More details.

I just tried booting with "all-generic-ide=1" appended to the end of the grub boot options:
```

[    0.000000] Kernel command line: root=UUID=876090ee-18d3-47b9-977c-b33597f7383c ro quiet splash all-generic-ide=1

```This doesn't appear to have had any effect. Here's more output from dmesg, showing ATA detection and assignment. Is the "Uniform CD-ROM driver" the right thing for dvd's?

```

[    1.726267] Driver 'sd' needs updating - please use bus_type methods
[    1.726279] Driver 'sr' needs updating - please use bus_type methods
[    1.726368] ata_piix 0000:00:1f.1: version 2.12
[    1.726385] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.726433] ata_piix 0000:00:1f.1: setting latency timer to 64
[    1.726549] scsi0 : ata_piix
[    1.726678] scsi1 : ata_piix
[    1.726726] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    1.726730] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    1.726766] ata1: port disabled. ignoring.
[    1.888311] ata2.00: ATAPI: TEAC DVD+RW DV-W58E, D.0C, max UDMA/33
[    1.904251] ata2.00: configured for UDMA/33
[    1.905824] scsi 1:0:0:0: CD-ROM            TEAC     DVD+RW DV-W58E   D.0C PQ: 0 ANSI: 5
[    1.907990] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[    1.907994] Uniform CD-ROM driver Revision: 3.20
[    1.908145] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.908216] sr 1:0:0:0: Attached scsi generic sg0 type 5
[    1.908242] ata_piix 0000:00:1f.2: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.908247] ata_piix 0000:00:1f.2: MAP [ P0 -- P1 -- ]
[    1.908293] ata_piix 0000:00:1f.2: setting latency timer to 64
[    1.908380] scsi2 : ata_piix
[    1.908464] scsi3 : ata_piix
[    1.908521] ata3: SATA max UDMA/133 cmd 0xfe00 ctl 0xfe10 bmdma 0xfea0 irq 18
[    1.908524] ata4: SATA max UDMA/133 cmd 0xfe20 ctl 0xfe30 bmdma 0xfea8 irq 18
[    2.073498] ata3.00: ATA-6: WDC WD2500JD-75GBB0, 02.05D02, max UDMA/100
[    2.073502] ata3.00: 488281250 sectors, multi 8: LBA48 
[    2.073516] ata3.00: applying bridge limits
[    2.089502] ata3.00: configured for UDMA/100
[    3.924152] scsi 2:0:0:0: Direct-Access     ATA      WDC WD2500JD-75G 02.0 PQ: 0 ANSI: 5
[    3.924272] sd 2:0:0:0: [sda] 488281250 512-byte hardware sectors: (250 GB/232 GiB)
[    3.924294] sd 2:0:0:0: [sda] Write Protect is off
[    3.924297] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.924332] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.924410] sd 2:0:0:0: [sda] 488281250 512-byte hardware sectors: (250 GB/232 GiB)
[    3.924429] sd 2:0:0:0: [sda] Write Protect is off
[    3.924433] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.924466] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.924471]  sda: sda1 sda2 < sda5 sda6 >
[    3.958767] sd 2:0:0:0: [sda] Attached SCSI disk
[    3.958827] sd 2:0:0:0: Attached scsi generic sg1 type 0

```

---

### Post by lisati on 2009-07-17
This might seem "obvious", but did the drive play DVDs before? I recall a similar question a few weeks back, and the discussion turned to how not all CD/DVD drives are created equal.

---

### Post by yoyodofield on 2012-06-25
Hey,does your problem solved ???I come across the same situation now...help...

---

### Post by overdrank on 2012-06-25
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

