---
title: "Hard Drive Errors"
date: 2006-03-02
forum: Hardware &amp; Laptops
---

### Post by dmonty on 2006-03-02
My /var/log/kern.log is showing some errors.  I am worried that this is going to result in data loss.

```

Feb 28 20:33:30 yerushalayim kernel: [47689.526467] ata1: translated ATA stat/err 0x25/00 to SCSI SK/ASC/ASCQ 0x4/00/00
Feb 28 20:33:30 yerushalayim kernel: [47689.526471] ata1: status=0x25 { DeviceFault CorrectedError Error }
Feb 28 20:33:30 yerushalayim kernel: [47689.526484] SCSI error : <0 0 0 0> return code = 0x8000002
Feb 28 20:33:30 yerushalayim kernel: [47689.526487] sda: Current: sense key: Hardware Error
Feb 28 20:33:30 yerushalayim kernel: [47689.526490]     Additional sense: No additional sense information
Feb 28 20:33:30 yerushalayim kernel: [47689.526494] end_request: I/O error, dev sda, sector 60566211
Feb 28 20:33:30 yerushalayim kernel: [47689.526499] Buffer I/O error on device dm-2, logical block 2145109
Feb 28 20:33:33 yerushalayim kernel: [47691.155044] ata1: translated ATA stat/err 0x25/00 to SCSI SK/ASC/ASCQ 0x4/00/00
Feb 28 20:33:33 yerushalayim kernel: [47691.155049] ata1: status=0x25 { DeviceFault CorrectedError Error }
Feb 28 20:33:33 yerushalayim kernel: [47691.155060] SCSI error : <0 0 0 0> return code = 0x8000002
Feb 28 20:33:33 yerushalayim kernel: [47691.155063] sda: Current: sense key: Hardware Error
Feb 28 20:33:33 yerushalayim kernel: [47691.155065]     Additional sense: No additional sense information
Feb 28 20:33:33 yerushalayim kernel: [47691.155069] end_request: I/O error, dev sda, sector 60566211
Feb 28 20:33:33 yerushalayim kernel: [47691.155074] Buffer I/O error on device dm-2, logical block 2145109
Feb 28 20:48:10 yerushalayim kernel: [48198.205825] ddcprobe: vm86 mode not supported on 64 bit kernel
Mar  1 06:20:07 yerushalayim kernel: [67255.159156] ata1: translated ATA stat/err 0x25/00 to SCSI SK/ASC/ASCQ 0x4/00/00
Mar  1 06:20:08 yerushalayim kernel: [67255.159161] ata1: status=0x25 { DeviceFault CorrectedError Error }
Mar  1 06:20:08 yerushalayim kernel: [67255.159173] SCSI error : <0 0 0 0> return code = 0x8000002
Mar  1 06:20:08 yerushalayim kernel: [67255.159176] sda: Current: sense key: Hardware Error
Mar  1 06:20:08 yerushalayim kernel: [67255.159179]     Additional sense: No additional sense information
Mar  1 06:20:08 yerushalayim kernel: [67255.159183] end_request: I/O error, dev sda, sector 64163627
Mar  1 06:20:08 yerushalayim kernel: [67256.797158] ata1: translated ATA stat/err 0x25/00 to SCSI SK/ASC/ASCQ 0x4/00/00
Mar  1 06:20:08 yerushalayim kernel: [67256.797163] ata1: status=0x25 { DeviceFault CorrectedError Error }
Mar  1 06:20:08 yerushalayim kernel: [67256.797178] SCSI error : <0 0 0 0> return code = 0x8000002
Mar  1 06:20:08 yerushalayim kernel: [67256.797180] sda: Current: sense key: Hardware Error
Mar  1 06:20:08 yerushalayim kernel: [67256.797183]     Additional sense: No additional sense information
Mar  1 06:20:08 yerushalayim kernel: [67256.797187] end_request: I/O error, dev sda, sector 64163635


```

Here is some more info:
```

root@yerushalayim:/var/log# lvscan
  ACTIVE            '/dev/vg1/lv-root' [10.00 GB] inherit
  ACTIVE            '/dev/vg1/lv-usr' [10.00 GB] inherit
  ACTIVE            '/dev/vg1/lv-var' [10.00 GB] inherit
  ACTIVE            '/dev/vg1/lv-home' [10.00 GB] inherit

root@yerushalayim:/var/log# pvscan
  PV /dev/sda2   VG vg1   lvm2 [46.57 GB / 6.57 GB free]
  Total: 1 [46.57 GB] / in use: 1 [46.57 GB] / in no VG: 0 [0   ]

root@yerushalayim:/var/log# mount
/dev/mapper/vg1-lv--root on / type reiserfs (rw)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
usbfs on /proc/bus/usb type usbfs (rw)
tmpfs on /lib/modules/2.6.12-10-amd64-k8/volatile type tmpfs (rw,mode=0755)
/dev/sda1 on /boot type reiserfs (rw,notail)
/dev/mapper/vg1-lv--home on /home type reiserfs (rw)
/dev/mapper/vg1-lv--usr on /usr type reiserfs (rw)
/dev/mapper/vg1-lv--var on /var type reiserfs (rw)
/home on /var/chroot/home type none (rw,bind)
/media/cdrom0 on /var/chroot/media/cdrom0 type none (rw,bind)
/dev on /var/chroot/dev type none (rw,bind)
/tmp on /var/chroot/tmp type none (rw,bind)
proc-chroot on /var/chroot/proc type proc (rw)
devpts-chroot on /var/chroot/dev/pts type devpts (rw)
tmpfs on /dev type tmpfs (rw,size=10M,mode=0755)

root@yerushalayim:/var/log# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/vg1-lv--root
                       10G  438M  9.6G   5% /
tmpfs                 248M     0  248M   0% /dev/shm
tmpfs                 248M   14M  234M   6% /lib/modules/2.6.12-10-amd64-k8/volatile
/dev/sda1             714M   65M  650M   9% /boot
/dev/mapper/vg1-lv--home
                       10G  9.0G  1.1G  90% /home
/dev/mapper/vg1-lv--usr
                       10G  2.7G  7.4G  27% /usr
/dev/mapper/vg1-lv--var
                       10G  5.1G  5.0G  51% /var
/home                  10G  9.0G  1.1G  90% /var/chroot/home
/media/cdrom0          10G  438M  9.6G   5% /var/chroot/media/cdrom0
/tmp                   10G  438M  9.6G   5% /var/chroot/tmp

```

```

root@yerushalayim:/var/log# dmesg
[   15.432518] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   15.432522] ACPI: bus type ide registered
[   15.435696] SCSI subsystem initialized
[   15.436644] libata version 1.11 loaded.
[   15.437688] sata_nv version 0.6
[   15.438140] ACPI: PCI Interrupt Link [LTID] BIOS reported IRQ 0, using IRQ 22
[   15.438143] ACPI: PCI Interrupt Link [LTID] enabled at IRQ 22
[   15.438150] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LTID] -> GSI 22 (level, low) -> IRQ 22
[   15.438162] PCI: Setting latency timer of device 0000:00:0a.0 to 64
[   15.438199] ata1: SATA max UDMA/133 cmd 0x9F0 ctl 0xBF2 bmdma 0xC800 irq 22
[   15.438214] ata2: SATA max UDMA/133 cmd 0x970 ctl 0xB72 bmdma 0xC808 irq 22
[   15.792319] ata1: dev 0 cfg 49:2f00 82:7c6b 83:7f09 84:4673 85:7c69 86:3e01 87:4663 88:407f
[   15.792323] ata1: dev 0 ATA, max UDMA/133, 398297088 sectors: lba48
[   15.793272] nv_sata: Primary device added
[   15.793274] nv_sata: Primary device removed
[   15.793276] nv_sata: Secondary device removed
[   15.793279] ata1: dev 0 configured for UDMA/133
[   15.793281] scsi0 : sata_nv
[   15.994143] ata2: no device found (phy stat 00000000)
[   15.994145] scsi1 : sata_nv
[   15.994208]   Vendor: ATA       Model: Maxtor 6L200S0    Rev: BANC
[   15.994215]   Type:   Direct-Access                      ANSI SCSI revision: 05
[   16.008000] NFORCE3-250: IDE controller at PCI slot 0000:00:08.0
[   16.008096] NFORCE3-250: chipset revision 162
[   16.008099] NFORCE3-250: not 100% native mode: will probe irqs later
[   16.008105] NFORCE3-250: 0000:00:08.0 (rev a2) UDMA133 controller
[   16.008113]     ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:pio, hdb:pio
[   16.008121]     ide1: BM-DMA at 0xffa8-0xffaf, BIOS settings: hdc:DMA, hdd:pio
[   16.008128] Probing IDE interface ide0...
[   16.525949] Probing IDE interface ide1...
[   17.196781] hdc: HL-DT-ST DVDRAM GSA-4167B, ATAPI CD/DVD-ROM drive
[   17.502908] ide1 at 0x170-0x177,0x376 on irq 15
[   17.502998] Probing IDE interface ide0...
[   18.021404] Probing IDE interface ide2...
[   18.533216] Probing IDE interface ide3...
[   19.045030] Probing IDE interface ide4...
[   19.556843] Probing IDE interface ide5...
[   20.075178] hdc: ATAPI 63X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache
[   20.075185] Uniform CD-ROM driver Revision: 3.20
[   20.099227] SCSI device sda: 398297088 512-byte hdwr sectors (203928 MB)
[   20.099236] SCSI device sda: drive cache: write back
[   20.099293] SCSI device sda: 398297088 512-byte hdwr sectors (203928 MB)
[   20.099299] SCSI device sda: drive cache: write back
[   20.099302]  /dev/scsi/host0/bus0/target0/lun0: p1 p2 p3
[   20.126572] Attached scsi disk sda at scsi0, channel 0, id 0, lun 0
[   20.509143] Attempting manual resume
[   20.509285] swsusp: Suspend partition has wrong signature?
[   20.527453] ohci_hcd: 2004 Nov 08 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[   20.527864] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 21
[   20.527871] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LUS0] -> GSI 21 (level, low) -> IRQ 21
[   20.527887] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   20.527890] ohci_hcd 0000:00:02.0: nVidia Corporation CK8S USB Controller
[   20.528028] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[   20.528039] ohci_hcd 0000:00:02.0: irq 21, io mem 0xfebfd000
[   20.580544] hub 1-0:1.0: USB hub found
[   20.580552] hub 1-0:1.0: 4 ports detected
[   20.583825] ACPI: PCI Interrupt Link [LUS1] enabled at IRQ 20
[   20.583830] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [LUS1] -> GSI 20 (level, low) -> IRQ 20
[   20.583843] PCI: Setting latency timer of device 0000:00:02.1 to 64
[   20.583846] ohci_hcd 0000:00:02.1: nVidia Corporation CK8S USB Controller (#2)
[   20.583892] ohci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
[   20.583900] ohci_hcd 0000:00:02.1: irq 20, io mem 0xfebfe000
[   20.636492] hub 2-0:1.0: USB hub found
[   20.636500] hub 2-0:1.0: 4 ports detected
[   20.649880] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 22
[   20.649885] ACPI: PCI Interrupt 0000:00:02.2[C] -> Link [LUS2] -> GSI 22 (level, low) -> IRQ 22
[   20.649898] PCI: Setting latency timer of device 0000:00:02.2 to 64
[   20.649902] ehci_hcd 0000:00:02.2: nVidia Corporation nForce3 EHCI USB 2.0 Controller
[   20.649907] ehci_hcd 0000:00:02.2: debug port 1
[   20.649944] ehci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 3
[   20.649952] ehci_hcd 0000:00:02.2: irq 22, io mem 0xfebffc00
[   20.649973] PCI: cache line size of 64 is not supported by device 0000:00:02.2
[   20.649978] ehci_hcd 0000:00:02.2: USB 2.0 initialized, EHCI 1.00, driver 10 Dec 2004
[   20.650054] hub 3-0:1.0: USB hub found
[   20.650060] hub 3-0:1.0: 8 ports detected
[   20.675681] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.41.
[   20.676082] ACPI: PCI Interrupt Link [LKLN] enabled at IRQ 21
[   20.676085] ACPI: PCI Interrupt 0000:00:05.0[A] -> Link [LKLN] -> GSI 21 (level, low) -> IRQ 21
[   20.676091] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   21.188421] eth0: forcedeth.c: subsystem: 01043:80a7 bound to 0000:00:05.0
[   21.239207] Linux Tulip driver version 1.1.13 (May 11, 2002)
[   21.239640] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 19
[   21.239647] ACPI: PCI Interrupt 0000:02:07.0[A] -> Link [LNKB] -> GSI 19 (level, low) -> IRQ 19
[   21.259572] eth1: Macronix 98715 PMAC rev 32 at 000000000001b800, 00:80:C6:F8:22:41, IRQ 19.
[   21.269837] sata_sil version 0.9
[   21.270229] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 18
[   21.270235] ACPI: PCI Interrupt 0000:02:0c.0[A] -> Link [LNKC] -> GSI 18 (level, low) -> IRQ 18
[   21.270287] ata3: SATA max UDMA/100 cmd 0xFFFFC2000004C880 ctl 0xFFFFC2000004C88A bmdma 0xFFFFC2000004C800 irq 18
[   21.270306] ata4: SATA max UDMA/100 cmd 0xFFFFC2000004C8C0 ctl 0xFFFFC2000004C8CA bmdma 0xFFFFC2000004C808 irq 18
[   21.270324] ata5: SATA max UDMA/100 cmd 0xFFFFC2000004CA80 ctl 0xFFFFC2000004CA8A bmdma 0xFFFFC2000004CA00 irq 18
[   21.270341] ata6: SATA max UDMA/100 cmd 0xFFFFC2000004CAC0 ctl 0xFFFFC2000004CACA bmdma 0xFFFFC2000004CA08 irq 18
[   21.471148] ata3: no device found (phy stat 00000000)
[   21.471151] scsi2 : sata_sil
[   21.672072] ata4: no device found (phy stat 00000000)
[   21.672074] scsi3 : sata_sil
[   21.873000] ata5: no device found (phy stat 00000000)
[   21.873002] scsi4 : sata_sil
[   22.073926] ata6: no device found (phy stat 00000000)
[   22.073928] scsi5 : sata_sil
[   24.639516] ACPI: CPU0 (power states: C1[C1])
[   24.838793] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[   25.247349] Attempting manual resume
[   25.247494] swsusp: Suspend partition has wrong signature?
[   25.252254] ReiserFS: dm-0: found reiserfs format "3.6" with standard journal
[   25.782799] ReiserFS: dm-0: using ordered data mode
[   25.791746] ReiserFS: dm-0: journal params: device dm-0, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[   25.793629] ReiserFS: dm-0: checking transaction log (dm-0)
[   25.842837] ReiserFS: dm-0: replayed 11 transactions in 0 seconds
[   25.880211] ReiserFS: dm-0: Using r5 hash to sort names
[   26.478736] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[   28.730354] Adding 489972k swap on /dev/sda3.  Priority:-1 extents:1
[   29.085651] ReiserFS: dm-0: Removing [43 8948 0x0 SD]..done
[   29.085710] ReiserFS: dm-0: Removing [43 8947 0x0 SD]..done
[   29.085734] ReiserFS: dm-0: Removing [43 8946 0x0 SD]..done
[   29.085754] ReiserFS: dm-0: There were 3 uncompleted unlinks/truncates. Completed
[   33.002673] parport: PnPBIOS parport detected.
[   33.002698] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[   33.054153] parport0: Printer, Canon BJC-250
[   33.056126] lp0: using parport0 (interrupt-driven).
[   33.062752] mice: PS/2 mouse device common for all mice
[   33.076203] Real Time Clock Driver v1.12
[   33.083904] ieee1394: Initialized config rom entry `ip1394'
[   33.086087] sbp2: $Rev: 1219 $ Ben Collins <bcollins@debian.org>
[   33.114522] nvidia: module license 'NVIDIA' taints kernel.
[   33.120316] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 17
[   33.120324] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKE] -> GSI 17 (level, low) -> IRQ 17
[   33.120475] NVRM: loading NVIDIA Linux x86_64 NVIDIA Kernel Module  1.0-7667  Fri Jun 17 07:14:03 PDT 2005
[   33.132667] i2c_adapter i2c-0: nForce2 SMBus adapter at 0x5000
[   33.133556] i2c_adapter i2c-1: nForce2 SMBus adapter at 0x5040
[   33.343891] it87: Found IT8712F chip at 0xd00, revision 7
[   33.393884] input: ImPS/2 Generic Wheel Mouse on isa0060/serio1
[   33.579747] ts: Compaq touchscreen protocol output
[   44.277094] ReiserFS: sda1: found reiserfs format "3.6" with standard journal
[   44.313924] ReiserFS: sda1: using ordered data mode
[   44.319526] ReiserFS: sda1: journal params: device sda1, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[   44.321450] ReiserFS: sda1: checking transaction log (sda1)
[   44.325426] ReiserFS: sda1: Using r5 hash to sort names
[   44.326104] ReiserFS: dm-3: found reiserfs format "3.6" with standard journal
[   44.326521] ReiserFS: dm-3: using ordered data mode
[   44.326630] ReiserFS: dm-3: journal params: device dm-3, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[   44.328523] ReiserFS: dm-3: checking transaction log (dm-3)
[   44.328738] ReiserFS: dm-3: Using r5 hash to sort names
[   44.329145] ReiserFS: dm-1: found reiserfs format "3.6" with standard journal
[   44.329897] ReiserFS: dm-1: using ordered data mode
[   44.330004] ReiserFS: dm-1: journal params: device dm-1, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[   44.331930] ReiserFS: dm-1: checking transaction log (dm-1)
[   44.345840] ReiserFS: dm-1: Using r5 hash to sort names
[   44.389212] ReiserFS: dm-2: found reiserfs format "3.6" with standard journal
[   44.389660] ReiserFS: dm-2: using ordered data mode
[   44.389773] ReiserFS: dm-2: journal params: device dm-2, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[   44.391705] ReiserFS: dm-2: checking transaction log (dm-2)
[   44.400194] ReiserFS: dm-2: Using r5 hash to sort names
[   44.414412] ReiserFS: dm-2: Removing [2130 20039 0x0 SD]..done
[   44.414450] ReiserFS: dm-2: There were 1 uncompleted unlinks/truncates. Completed
[   46.872710] ACPI: PCI Interrupt Link [LAUI] enabled at IRQ 20
[   46.872715] ACPI: PCI Interrupt 0000:00:06.0[A] -> Link [LAUI] -> GSI 20 (level, low) -> IRQ 20
[   46.872743] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   47.180773] intel8x0_measure_ac97_clock: measured 49586 usecs
[   47.180777] intel8x0: clocking to 46822
[   47.916848] ohci1394: $Rev: 1250 $ Ben Collins <bcollins@debian.org>
[   47.916870] ACPI: PCI Interrupt 0000:02:0b.0[A] -> Link [LNKB] -> GSI 19 (level, low) -> IRQ 19
[   47.916876] PCI: Via IRQ fixup for 0000:02:0b.0, from 11 to 3
[   47.973099] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[19]  MMIO=[feaff000-feaff7ff]  Max Packet=[2048]
[   49.238589] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0011d80000085574]
[   49.281499] input: PC Speaker
[   49.321028] Floppy drive(s): fd0 is 1.44M
[   49.415073] FDC 0 is a post-1991 82077
[   51.170813] NET: Registered protocol family 17
[   52.563294] NET: Registered protocol family 10
[   52.563391] Disabled Privacy Extensions on device ffffffff803861a0(lo)
[   52.563827] IPv6 over IPv4 tunneling driver
[   54.317886] ACPI: Power Button (FF) [PWRF]
[   54.317912] ACPI: Power Button (CM) [PWRB]
[   54.364373] ibm_acpi: ec object not found
[   62.876045] eth0: no IPv6 routers present
[   63.032993] eth1: no IPv6 routers present
[   63.918840] powernow-k8: Found 1 AMD Athlon 64 / Opteron processors (version 1.40.4)
[   63.920639] powernow-k8:    0 : fid 0x2 (1000 MHz), vid 0x12 (1100 mV)
[   63.920643] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0x6 (1400 mV)
[   63.920976] cpu_init done, current fid 0xa, vid 0x6
[   64.791447] eth1: Promiscuous mode enabled.
[   64.791452] device eth1 entered promiscuous mode
[   67.279479] Bluetooth: Core ver 2.7
[   67.279489] NET: Registered protocol family 31
[   67.279491] Bluetooth: HCI device and connection manager initialized
[   67.279501] Bluetooth: HCI socket layer initialized
[   67.307540] Bluetooth: L2CAP ver 2.7
[   67.307544] Bluetooth: L2CAP socket layer initialized
[   67.363000] Bluetooth: RFCOMM ver 1.5
[   67.363009] Bluetooth: RFCOMM socket layer initialized
[   67.363019] Bluetooth: RFCOMM TTY layer initialized
[   68.194123] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[   68.194140] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[   68.194165] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[   68.443623] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[   68.443641] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[   68.443667] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[   82.301110] ip_tables: (C) 2000-2002 Netfilter core team
[   82.431935] ip_conntrack version 2.1 (2047 buckets, 16376 max) - 336 bytes per conntrack


```

```

root@yerushalayim:/var/log# lspci
0000:00:00.0 Host bridge: nVidia Corporation: Unknown device 00e1 (rev a1)
0000:00:01.0 ISA bridge: nVidia Corporation: Unknown device 00e0 (rev a2)
0000:00:01.1 SMBus: nVidia Corporation: Unknown device 00e4 (rev a1)
0000:00:02.0 USB Controller: nVidia Corporation: Unknown device 00e7 (rev a1)
0000:00:02.1 USB Controller: nVidia Corporation: Unknown device 00e7 (rev a1)
0000:00:02.2 USB Controller: nVidia Corporation: Unknown device 00e8 (rev a2)
0000:00:05.0 Bridge: nVidia Corporation: Unknown device 00df (rev a2)
0000:00:06.0 Multimedia audio controller: nVidia Corporation: Unknown device 00ea (rev a1)
0000:00:08.0 IDE interface: nVidia Corporation: Unknown device 00e5 (rev a2)
0000:00:0a.0 IDE interface: nVidia Corporation: Unknown device 00e3 (rev a2)
0000:00:0b.0 PCI bridge: nVidia Corporation: Unknown device 00e2 (rev a2)
0000:00:0e.0 PCI bridge: nVidia Corporation: Unknown device 00ed (rev a2)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
0000:02:07.0 Ethernet controller: Macronix, Inc. [MXIC] MX987x5 (rev 20)
0000:02:0b.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
0000:02:0c.0 RAID bus controller: Silicon Image, Inc. (formerly CMD Technology Inc) SiI 3114 [SATALink/SATARaid] Serial ATA Controller (rev 02)


```

---

### Post by rorowe on 2006-03-10
I recently started having the same problems. (different hardware, though)

---

