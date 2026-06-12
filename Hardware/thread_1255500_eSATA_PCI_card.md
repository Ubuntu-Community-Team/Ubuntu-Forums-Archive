---
title: "eSATA PCI card"
date: 2009-09-01
forum: Hardware
---

### Post by DPic on 2009-09-01
I'm trying to get my external HDD set up with a PCI eSATA card and i can't get it to work. It doesn't seem that the drive is even detected, nevermind mountable. Can anybody help me figure this out?

---

### Post by tgrimley on 2009-09-01
more info?

what's the pci card? did you do a lspci? dmseg?

---

### Post by DPic on 2009-09-01
```
lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IB (ICH9) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IB (ICH9) 2 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G92 [GeForce 8800 GTS 512] (rev a2)
03:00.0 IDE interface: JMicron Technology Corp. JMB368 IDE controller
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
05:04.0 FireWire (IEEE 1394): NEC Corporation uPD72874 IEEE1394 OHCI 1.1 3-port PHY-Link Ctrlr (rev 01)

```

dmesg was too long but another post ([http://ubuntuforums.org/showthread.php?t=544897](http://ubuntuforums.org/showthread.php?t=544897)) said to use dmesg | tail -15 hope that's still helpful
> dmesg | tail -15
[  511.869537] EXT4-fs: file extents enabled
[  511.871087] EXT4-fs: mballoc enabled
[  511.871104] EXT4-fs (sdc1): mounted filesystem with ordered data mode
[  553.229139] end_request: I/O error, dev fd0, sector 0
[ 1185.047278] __ratelimit: 6 callbacks suppressed
[ 1185.047284] chromium-browse[4201]: segfault at 0 ip 000000000138fbd4 sp 00007fffdd3826f8 error 4 in chromium-browser[400000+1e06000]
[ 1187.425083] chromium-browse[4256]: segfault at 0 ip 000000000138fbd4 sp 00007fffdd3826f8 error 4 in chromium-browser[400000+1e06000]
[ 1534.146018] UDP: bad checksum. From 119.160.156.11:16930 to 192.168.1.5:55455 ulen 70
[ 2739.024609] UDP: bad checksum. From 119.160.156.11:16957 to 192.168.1.5:55455 ulen 70
[ 3943.838291] UDP: bad checksum. From 119.160.156.11:17096 to 192.168.1.5:55455 ulen 70
[ 4269.136170] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
[ 4269.137980] SGI XFS Quota Management subsystem
[ 4269.149139] JFS: nTxBlock = 8192, nTxLock = 65536
[ 4269.200864] NTFS driver 2.1.29 [Flags: R/O MODULE].
[ 4269.241224] QNX4 filesystem 0.2.3 registered.


PPA PCI-Express Serial ATA II Controller Card – 3 Ports (2 External + 1 Internal) Model 1349
[http://www.newegg.com/Product/Product.aspx?Item=N82E16815263002](http://www.newegg.com/Product/Product.aspx?Item=N82E16815263002)

---

### Post by tgrimley on 2009-09-01
I can't see the sata controller in either of those, maybe a dmseg | grep ATA will find it?  I can't find what controller it is using but it seems to be compatible with linux.  Is this a new card, there are reports of cards not working at newegg.

---

### Post by DPic on 2009-09-02
```
dmesg | grep ATA
[    0.000000]   NODE_DATA [000000000000d000 - 0000000000011fff]
[    0.000000]   #2 [0001000000 - 00019b2b8c]    TEXT DATA BSS ==> [0001000000 - 00019b2b8c]
[    0.612299] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[    0.612303] ata2: SATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[    0.613186] ata3: SATA max UDMA/133 cmd 0xe700 ctl 0xe800 bmdma 0xeb00 irq 19
[    0.613190] ata4: SATA max UDMA/133 cmd 0xe900 ctl 0xea00 bmdma 0xeb08 irq 19
[    0.615524] ata5: PATA max UDMA/100 cmd 0xc000 ctl 0xc100 bmdma 0xc400 irq 16
[    0.615526] ata6: PATA max UDMA/100 cmd 0xc200 ctl 0xc300 bmdma 0xc408 irq 16
[    0.938622] ata3: SATA link down (SStatus 0 SControl 300)
[    0.949251] ata4: SATA link down (SStatus 0 SControl 300)
[    0.958661] ata2: SATA link down (SStatus 0 SControl 300)
[    1.092053] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.112710] ata1.00: ATA-7: ST3250410AS, 3.AAC, max UDMA/133
[    1.124475] scsi 0:0:0:0: Direct-Access     ATA      ST3250410AS      3.AA PQ: 0 ANSI: 5
[    6.512879] scsi 7:0:0:0: CD-ROM            ATAPI    DVD A  DH20A4P   9P59 PQ: 0 ANSI: 0
```

I've had it for about a year i think. i just haven't tried using it until now (because i didn't have an eSATA cord)

---

