---
title: "USB HD: How to know which /dev/... to use for mounting?"
date: 2006-10-30
forum: Hardware &amp; Laptops
---

### Post by jyer on 2006-10-30
Hello,
I'm trying to use an old Dell Latitude Laptop as a server at home. I've configured it fine so far and have started sharing stuff with Nfs and Samba. Only, I now want to plug an external usb harddisk into the machine in order to share more data and have regular backups of my files.
The only problem is that I don't know how to know which /dev my harddisk referes to and hence don't know which /dev to use to mount my harddisk (mount /dev/? ext).
I'm using Debian 3.1 and haven't install any X11 server or desktop. I haven't installed any specific USB driver either. My dmesg is:

```


Linux version 2.2.20 (herbert@gondolin) (gcc version 2.7.2.3) #1 Sat Apr 20 11:45:28 EST 2002 BIOS-provided physical RAM map: BIOS-e820: 0009f000 @ 00000000 (usable) BIOS-e820: 07ef0000 @ 00100000 (usable) Detected 300687 kHz processor. Console: colour VGA+ 80x25 Calibrating delay loop... 599.65 BogoMIPS Memory: 127024k/131008k available (1756k kernel code, 412k reserved, 1664k data, 152k init) Dentry hash table entries: 16384 (order 5, 128k) Buffer cache hash table entries: 131072 (order 7, 512k) Page cache hash table entries: 32768 (order 5, 128k) VFS: Diskquotas version dquot_6.4.0 initialized Intel machine check architecture supported. Intel machine check reporting enabled on CPU#0. 512K L2 cache (4 way) CPU: L2 Cache: 512K CPU: Intel Pentium II (Deschutes) stepping 02 Checking 386/387 coupling... OK, FPU using exception 16 error reporting. Checking 'hlt' instruction... OK. Checking for popad bug... OK. POSIX conformance testing by UNIFIX mtrr: v1.35a (19990819) Richard Gooch (rgooch@atnf.csiro.au) PCI: PCI BIOS revision 2.10 entry at 0xfbc7e PCI: Using configuration type 1 PCI: Probing PCI hardware Linux NET4.0 for Linux 2.2 Based upon Swansea University Computer Society NET3.039 NET4: Linux TCP/IP 1.0 for NET4.0 IP Protocols: ICMP, UDP, TCP, IGMP TCP: Hash tables configured (ehash 131072 bhash 65536) Starting kswapd v 1.5 Serial driver version 4.27 with HUB-6 MANY_PORTS MULTIPORT SHARE_IRQ enabled ttyS00 at 0x03f8 (irq = 4) is a 16550A pty: 256 Unix98 ptys configured Real Time Clock Driver v1.09 RAM disk driver initialized: 16 RAM disks of 4096K size loop: registered device at major 7 PIIX4: IDE controller on PCI bus 00 dev 39 PIIX4: not 100% native mode: will probe irqs later ide0: BM-DMA at 0x0860-0x0867, BIOS settings: hda:DMA, hdb:pio ide1: BM-DMA at 0x0868-0x086f, BIOS settings: hdc:DMA, hdd:pio hda: TOSHIBA MK2018GAP, ATA DISK drive hdc: TOSHIBA CD-ROM XM-1902B, ATAPI CDROM drive ide0 at 0x1f0-0x1f7,0x3f6 on irq 14 ide1 at 0x170-0x177,0x376 on irq 15 hda: TOSHIBA MK2018GAP, 19077MB w/0kB Cache, CHS=2432/255/63 hdc: ATAPI 24X CD-ROM drive, 128kB Cache Uniform CD-ROM driver Revision: 3.11 Floppy drive(s): fd0 is 1.44M FDC 0 is a post-1991 82077 md driver 0.36.6 MAX_MD_DEV=4, MAX_REAL=8 scsi: <fdomain> Detection failed (no card) NCR53c406a: no available ports found sym53c416.c: Version 1.0.0 Failed initialization of WD-7000 SCSI card! IBM MCA SCSI: Version 3.2 IBM MCA SCSI: No Microchannel-bus present --> Aborting. This machine does not have any IBM MCA-bus or the MCA-Kernel-support is not enabled! megaraid: v1.11 (Aug 23, 2000) aec671x_detect: 3ware Storage Controller device driver for Linux v1.02.00.008. 3w-xxxx: tw_findcards(): No cards found. scsi : 0 hosts. scsi : detected total. Partition check: hda: hda1 hda2 hda3 hda4 apm: BIOS version 1.2 Flags 0x03 (Driver version 1.13) apm: disabled on user request. VFS: Mounted root (ext2 filesystem) readonly. Freeing unused kernel memory: 152k freed NET4: Unix domain sockets 1.0 for Linux NET4.0. Adding Swap: 979956k swap-space (priority -1) Installing knfsd (copyright (C) 1996 okir@monad.swb.de) Linux PCMCIA Card Services 3.1.33 kernel build: 2.2.20 #1 Sat Apr 20 11:45:28 EST 2002 options: [pci] [cardbus] [apm] PCI routing table version 1.0 at 0xfb940 00:03.0 -> irq 11 00:03.1 -> irq 11 Intel ISA/PCI/CardBus PCIC probe: TI 1131 rev 01 PCI-to-CardBus at slot 00:03, mem 0x68000000 host opts [0]: [ring] [pci + serial irq] [pci irq 11] [lat 32/32] [bus 32/34] host opts [1]: [ring] [pci + serial irq] [pci irq 11] [lat 32/32] [bus 35/37] ISA irqs (scanned) = 3,4,9,10 PCI status changes cs: cb_alloc(bus 32): vendor 0x1317, device 0x1985 cs: cb_config(bus 32) cs: IO port probe 0x0100-0x04ff: excluding 0x210-0x217 0x220-0x22f 0x378-0x37f 0x388-0x38f 0x4d0-0x4d7 cs: IO port probe 0x0218-0x021f: clean. cs: IO port probe 0x0230-0x0377: clean. cs: IO port probe 0x0380-0x0387: clean. cs: IO port probe 0x0390-0x04cf: clean. cs: IO port probe 0x04d8-0x04ff: clean. cs: IO port probe 0x0800-0x08ff: excluding 0x800-0x84f cs: IO port probe 0x0a00-0x0aff: clean. cs: IO port probe 0x0c00-0x0cff: excluding 0xcf8-0xcff fn 0 bar 1: io 0xa00-0xaff fn 0 bar 2: mem 0x60060000-0x600603ff fn 0 rom: mem 0x60040000-0x6005ffff irq 11 cs: cb_enable(bus 32) bridge io map 0 (flags 0x21): 0xa00-0xaff bridge mem map 0 (flags 0x1): 0x60040000-0x60060fff tulip_attach(device 20:00.0) tulip.c:v0.91g-ppc 7/16/99 becker@scyld.com (modified by danilo@cs.uni-magdeburg.de for XIRCOM CBE, fixed by Doug Ledford) eth0: ADMtek Centaur-C rev 17 at 0xa00, 00:10:7A:69:37:F7, IRQ 11. cs: memory probe 0xa0000000-0xa0ffffff: clean. tty01 at 0x02f8 (irq = 3) is a 16550A

```

Thanks a lot for any help,
jr

---

### Post by jyer on 2006-10-30
ah, yeah. Neither sda 1-5 or sdb 1-5 work to mount the device.

---

