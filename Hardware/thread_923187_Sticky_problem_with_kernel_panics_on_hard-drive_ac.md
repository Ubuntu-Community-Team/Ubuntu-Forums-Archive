---
title: "Sticky problem with kernel panics on hard-drive access"
date: 2008-09-18
forum: Hardware
---

### Post by neo1985 on 2008-09-18
Hello folks,

Let me explain: Since two weeks, I moved from Windows to Linux, but I never got a stable operating system since then. Just for the protocol, my system is an EagleTEC M825 series Mainboard with VIA KM266 Northbridge and VT8253 Southbridge, using a socket-A AMD Athlon XP 1800+ (1.5Ghz) and 768 MB of SDRAM. GPU is an Nvidia Geforce 5500FX.

My IDE hard drive configuration:
Primary IDE Master: Seagate Hard drive, 40 GB (ext3), jumpered as Master
Primary IDE Slave: TSSCorp DVD-ROM drive, jumpered as Slave
Secondary IDE Master: Excelstor hard drive, 250 GB (ext3), jumpered as Master
Secondary IDE Slave: LG DVD-RAM drive, jumpered as Slave


I'm capitulating with this problem, my system - both Kubuntu 8.04 and my new Linux Mint 5 Elyssa installation - causes kernel panics with system hangup when I try to copy any data from my 250GB IDE hard drive under Linux. I found out that the problem is only when using the SATA/libata driver of the Kernel to access my hard-disks.
Blacklisting the module "ata_piix" solves the problem, but slows the system down (hard drive gets only rates of 1.97MB/sec when calling **hdparm -t /dev/hda1** - when I perform **hdparm -t /dev/sda1** without blacklisted ata_piix module, I get rates around 48MB/sec).

This is what hdparm tells me when running 
```
neo-mint neo # hdparm -t /dev/hda

/dev/hda:
 Timing buffered disk reads:   10 MB in  3.41 seconds =   2.93 MB/sec
```


I tried so many things until now but nothing really helps to fix this problem. The system will only run stable when I blacklist ata_piix, but then, the mouse unter X11 laggs and programs need seconds to start when any hard-drive accesses are done simultaneous. When no huger hard-drive access occurs, I can use features like Compiz without any lags - so the problem must be on the HDD accesses and the low rate. It's also not possible to assign a DMA to my harddrives, I always get

```
neo-mint neo # hdparm /dev/hda

/dev/hda:
 multcount     =  0 (off)
 IO_support    =  0 (default)
16-bit)
 unmaskirq     =  0 (off)
 using_dma     =  0 (off)
 keepsettings  =  0 (off)
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 65535/16/63, sectors = 78165360, start = 0
neo-mint neo # hdparm -d1 /dev/hda

/dev/hda:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Operation not permitted
 using_dma     =  0 (off)
```

The best results I got was when I tried to run Debian on my machine. Debian directly uses other drivers to access my IDE hard drives. The system was quick and stable, but Debian is nothing for a Linux newbie like me. Too much hardwork ;).

When I run kubuntu or Mint with no special kernel boot parameters, I always get messages of the form

```
[  503.154094] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2
[  503.154182] ata2.00: BMDMA stat 0x64
[  503.154251] ata2.00: cmd 25/00:b8:48:c4:d5/00:00:18:00:00/e0 tag 0 dma 94208 in
[  503.154254]          res 51/84:00:48:c4:d5/84:00:18:00:00/e0 Emask 0x10 (ATA bus error)
[  503.154331] ata2.00: status: { DRDY ERR }
[  503.154394] ata2.00: error: { ICRC ABRT }
[  503.154489] ata2: soft resetting link
[  503.498612] ata2.00: configured for UDMA/100
[  503.667919] ata2.01: configured for UDMA/33
[  503.667962] ata2: EH complete
[  503.727676] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2
[  503.727761] ata2.00: BMDMA stat 0x64
[  503.727830] ata2.00: cmd 25/00:b8:48:c4:d5/00:00:18:00:00/e0 tag 0 dma 94208 in
[  503.727833]          res 51/84:00:48:c4:d5/84:00:18:00:00/e0 Emask 0x10 (ATA bus error)
[  503.727910] ata2.00: status: { DRDY ERR }
[  503.727973] ata2.00: error: { ICRC ABRT }
[  503.728067] ata2: soft resetting link
[  504.071782] ata2.00: configured for UDMA/100
[  504.243236] ata2.01: configured for UDMA/33
[  504.243283] ata2: EH complete
[  504.299259] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2
[  504.299346] ata2.00: BMDMA stat 0x64
[  504.299416] ata2.00: cmd 25/00:b8:48:c4:d5/00:00:18:00:00/e0 tag 0 dma 94208 in
[  504.299418]          res 51/84:00:48:c4:d5/84:00:18:00:00/e0 Emask 0x10 (ATA bus error)
[  504.299496] ata2.00: status: { DRDY ERR }
[  504.299558] ata2.00: error: { ICRC ABRT }
[  504.299653] ata2: soft resetting link
[  504.637435] ata2.00: configured for UDMA/100
[  504.810571] ata2.01: configured for UDMA/33
[  504.810613] ata2: EH complete
[  504.871910] ata2.00: limiting speed to UDMA/33:PIO4
[  504.871927] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2
[  504.872006] ata2.00: BMDMA stat 0x64
[  504.872075] ata2.00: cmd 25/00:b8:48:c4:d5/00:00:18:00:00/e0 tag 0 dma 94208 in
[  504.872077]          res 51/84:00:48:c4:d5/84:00:18:00:00/e0 Emask 0x10 (ATA bus error)
[  504.872154] ata2.00: status: { DRDY ERR }
[  504.872217] ata2.00: error: { ICRC ABRT }
[  504.872313] ata2: soft resetting link
[  505.216442] ata2.00: configured for UDMA/33
[  505.385997] ata2.01: configured for UDMA/33
[  505.386033] ata2: EH complete
```

From other forums, I found some kernel boot parameters that disable these messages coming up, these where **noapic nolapic acpi=off**, but anyway, the system gets kernel panic when I try to copy data from my 250GB drive over to the 40GB drive. I should note, that I bought a brand-new IDE 250GB hard-disk because my old one had the same problem - and the advice of some users had been "Your harddrive is damaged". But no, it isn't. Running with blacklisted ata_piix copies the data without any panics...

The kernel panic I get on copying data from my harddisk, with enabled kernel parameters **noapic nolapic acpi=off** gives me this crash log:
[http://linuxmint.com/forum/download/file.php?id=857](http://linuxmint.com/forum/download/file.php?id=857)

I even tried to use the kernel boot parameters **noapic nolapic acpi=off all_generic_ide noapci linux ide=nodma idle=poll irqpoll**. I tried several of them always in different compositions, but nothing helped. Always the same problem. The system even crashes with this error when running from a live system. fsck on both hard-drives says "no errors". BIOS resets and several BIOS settings even took no effect.

I'm giving up with this problem. Windows ran on this machine without any problems for years. And also Debian runs very well - but Debian is not "my system", it's too superior for me currently. I wish to use Linux Mint (its Ubuntu-based), but this with an acceptable system performance, especially on hard drive accesses.

Any further ideas on my problem? Or should I now buy a new computer next to the new hard-drive, which even was NOT the problem?

Best regards,
neo1985

PS: Oh right, one thing I had forgotten: I replaced all IDE cables with new ones within the system...

---

### Post by Gimble on 2008-12-17
Stupid suggestion, I am sure, but have you tried running the two hard drives as master/slave on one controller, and the two DVDs as master/slave on the secondary controller?

---

