---
title: "Problem with libata 40-wire"
date: 2008-07-01
forum: Hardware
---

### Post by ntrl on 2008-07-01
Hello all!

I use CF-IDE adaptor with CF card SiliconPower 8GB 300x. His support UDMA 6 and fixed ide mode.
I use 2 partitions. On sda1 - winXP, on sda2 Ubuntu 8.04.
On windows XP transfer from flash ~45mb/sec.  Windows booting 5 secs. :)

But in Linux 40-wire problem, udma2 use instead udma6.

I appling [this patch ]("http://pixca.net/blog/bits-and-bytes/limited-to-udma33-due-to-40-wire-cable/")on distro-kernel 2.6.24-19-generic. But nothing to do :(
libata parameter - force_cbl=80

Here dmesg's log:
```

serge@tpx40:~$ dmesg | grep ata
[    0.000000]  BIOS-e820: 000000002f6e0000 - 000000002f6f7000 (ACPI data)
[    3.187618] Memory: 758020k/777088k available (2177k kernel code, 18456k reserved, 1006k data, 368k init, 0k highmem)
[    3.187699]       .data : 0xc0320434 - 0xc041bdc4   (1006 kB)
[    4.027300] ACPI: EC: GPE = 0x1c, I/O: command/status = 0x66, data = 0x62
[    5.647700] libata: no version for "struct_module" found: kernel tainted.
[    5.656391] libata version 3.00 loaded.
[    6.880275] ata_piix 0000:00:1f.1: version 2.12
[    6.881265] scsi0 : ata_piix
[    6.881822] scsi1 : ata_piix
[    6.882937] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
[    6.882983] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
[    7.052143] ata1: forcing 80c
[    7.052207] ata1.00: ATA-0: SILICON POWER, 20070831, max UDMA/133
[    7.052251] ata1.00: 15662304 sectors, multi 0: LBA 
[    7.052307] ata1.00: limited to UDMA/33 due to 40-wire cable
[    7.068085] ata1.00: configured for UDMA/33
[    7.092090] ata1.00: configured for UDMA/33
[    7.092137] ata1: EH complete
[    7.247720] ata2: forcing 80c
[    8.006132] ReiserFS: sda2: using ordered data mode

```

I build new kernel 2.6.25.9, libata parameter force=80c, kernel probing use udma6 mode, but just as nothing to do.
"limited to UDMA/33 due to 40-wire cable, configured for UDMA/33" :(

```

serge@tpx40:~$ sudo hdparm -tT /dev/sda
[sudo] password for serge: 

/dev/sda:
 Timing cached reads:   940 MB in  2.00 seconds = 469.91 MB/sec
 Timing buffered disk reads:   70 MB in  3.05 seconds =  22.98 MB/sec

```


My hardware: IBM thinkpad X40, CF siliconimage 8GB 300x.

Please help me!

PS. sorry for bad English.

---

### Post by ntrl on 2008-07-02
YES!

I build new devel kernel's version 2.6.26rc8, and UDMA100 will work :)

```

root@tpx40:/usr/src# uname -a
Linux tpx40 2.6.26-rc8 #1 SMP Mon Jun 30 00:12:32 MSD 2008 i686 GNU/Linux
root@tpx40:/usr/src#
root@tpx40:/usr/src# dmesg | grep ata
[    0.000000]  BIOS-e820: 000000002f6e0000 - 000000002f6f7000 (ACPI data)
[    0.000000] PERCPU: Allocating 39592 bytes of per cpu data
[    0.004000] Memory: 758752k/777088k available (2152k kernel code, 17764k reserved, 761k data, 360k init, 0k highmem)
[    0.004000]       .data : 0xc031a2ff - 0xc03d8900   ( 761 kB)
[    0.337429] ACPI: EC: GPE = 0x1c, I/O: command/status = 0x66, data = 0x62
[    1.851953] libata version 3.00 loaded.
[    3.405125] ata_piix 0000:00:1f.1: version 2.12
[    3.405136] ata_piix 0000:00:1f.1: enabling device (0005 -> 0007)
[    3.405575] scsi0 : ata_piix
[    3.406125] scsi1 : ata_piix
[    3.407478] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
[    3.407524] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
[    3.576287] ata1.00: ATA-0: SILICON POWER, 20070831, max UDMA/133
[    3.576338] ata1.00: 15662304 sectors, multi 0: LBA
[    3.576392] ata1.00: FORCE: xfer_mask set to udma100
[    3.592226] ata1.00: configured for UDMA/100
[    3.600229] ata1.00: FORCE: xfer_mask set to udma100
[    3.616257] ata1.00: configured for UDMA/100
[    3.616299] ata1: EH complete
[    4.503453] ReiserFS: sda2: using ordered data mode
root@tpx40:/usr/src# hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   1288 MB in  2.00 seconds = 643.81 MB/sec
 Timing buffered disk reads:  136 MB in  3.01 seconds =  45.21 MB/sec




```

---

### Post by Sirilos on 2011-10-18
> I build new devel kernel's version 2.6.26rc8, and UDMA100 will work :)



I have a similar problem with yours... Just a few days ago posted a thread with it but none responds... How exactly did you build this new kernel version? I have the new ubuntu version 11.4 but the problem remains in my computer with the low udma due to 40 wire cable...

---

