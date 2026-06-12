---
title: "ubuntu 8.04 server hard drive problem"
date: 2009-03-05
forum: Hardware
---

### Post by pyroger101 on 2009-03-05
Hi guys and dolls!

Have my media server built and i am using ubuntu server 8.04 that hosts three harddrives, 1 for the ubuntu os and the other two for media 1tb each.
The machine works great initially however after a short amount of time(an hour or so) the files on my two mounted hard drives that store my media dissappear. Almost as if the hard drives unmount but the hard drive is still visable. When i reboot the machine none of the media hard drives show up then when i reboot again everythin works perfect!

doo dooo dooo dooo dooo dooooooo *x files music!

so i have had this problem for quite some time and i could REALLLYYY do with some help with this issue!

pls pls help

Thanks

Ger


FSTAB

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                    0  0
# /dev/sda1
UUID=3747dfcc-ef9e-499c-8bdd-c8bff3e29637  /              ext3         relatime,errors=remount-ro  0  1
# /dev/sda5
UUID=4bb683f1-cf66-4af2-a4f6-8bd58743f65f  none           swap         sw                          0  0
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8       0  0


/dev/sdb1                                  /media/sdb1    ext3         defaults     0  0
/dev/sdb2                                  /media/sdb2    swap         defaults     0  0
/dev/sdc1                                  /media/sdc1    ext3         defaults     0  0
/dev/sdc5                                  /media/sdc5    swap         defaults     0  0
/dev/sda5                                  /media/sda5    ext3         defaults     0  0

```


#################################################################
##################################################################
dmesg:

##############################################################
```


[   34.767827] PCI: Setting latency timer of device 0000:05:00.0 to 64
[   34.806990] eth0: Tigon3 [partno(BCM95751) rev 4001 PHY(5750)] (PCI Express) 10/100/1000Base-T Ethernet 00:30:05:c9:c4:75
[   34.807004] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[1] TSOcap[1]
[   34.807008] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[   34.912766] usbcore: registered new interface driver usbfs
[   34.912803] usbcore: registered new interface driver hub
[   34.918210] usbcore: registered new device driver usb
[   34.964294] USB Universal Host Controller Interface driver v3.0
[   34.964375] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 20
[   34.964390] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   34.964396] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   34.964651] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   34.964688] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00002400
[   34.964896] usb usb1: configuration #1 chosen from 1 choice
[   34.964937] hub 1-0:1.0: USB hub found
[   34.964947] hub 1-0:1.0: 2 ports detected
[   35.071914] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 22 (level, low) -> IRQ 21
[   35.071930] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   35.071937] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   35.071976] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   35.072011] uhci_hcd 0000:00:1d.1: irq 21, io base 0x00002800
[   35.072198] usb usb2: configuration #1 chosen from 1 choice
[   35.072238] hub 2-0:1.0: USB hub found
[   35.072248] hub 2-0:1.0: 2 ports detected
[   35.160418] SCSI subsystem initialized
[   35.181765] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 21 (level, low) -> IRQ 22
[   35.181782] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   35.181788] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   35.181824] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   35.181859] uhci_hcd 0000:00:1d.2: irq 22, io base 0x00002c00
[   35.182047] usb usb3: configuration #1 chosen from 1 choice
[   35.182090] hub 3-0:1.0: USB hub found
[   35.182099] hub 3-0:1.0: 2 ports detected
[   35.259376] libata version 3.00 loaded.
[   35.268120] FDC 0 is a post-1991 82077
[   35.291588] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 20 (level, low) -> IRQ 23
[   35.291608] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   35.291615] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   35.291666] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   35.291705] uhci_hcd 0000:00:1d.3: irq 23, io base 0x00003000
[   35.291900] usb usb4: configuration #1 chosen from 1 choice
[   35.291946] hub 4-0:1.0: USB hub found
[   35.291958] hub 4-0:1.0: 2 ports detected
[   35.401418] sata_sil 0000:0b:05.0: version 2.3
[   35.401492] ACPI: PCI Interrupt 0000:0b:05.0[A] -> <6>ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 20
[   35.401505] GSI 22 (level, low) -> IRQ 21
[   35.401517] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   35.401524] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   35.401529] sata_sil 0000:0b:05.0: Applying R_ERR on DMA activate FIS errata fix
[   35.401565] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   35.402859] scsi0 : sata_sil
[   35.403898] scsi1 : sata_sil
[   35.404911] scsi2 : sata_sil
[   35.405490] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[   35.405504] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xf0004000
[   35.405930] scsi3 : sata_sil
[   35.405986] ata1: SATA max UDMA/100 mmio m1024@0xf0200000 tf 0xf0200080 irq 21
[   35.405991] ata2: SATA max UDMA/100 mmio m1024@0xf0200000 tf 0xf02000c0 irq 21
[   35.405997] ata3: SATA max UDMA/100 mmio m1024@0xf0200000 tf 0xf0200280 irq 21
[   35.406001] ata4: SATA max UDMA/100 mmio m1024@0xf0200000 tf 0xf02002c0 irq 21
[   35.431231] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   35.431433] usb usb5: configuration #1 chosen from 1 choice
[   35.431476] hub 5-0:1.0: USB hub found
[   35.431487] hub 5-0:1.0: 8 ports detected
[   35.728201] ata1: SATA link down (SStatus 0 SControl 310)
[   36.067614] ata2: SATA link down (SStatus 0 SControl 310)
[   36.556807] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   37.065103] ata3.00: ATA-8: WDC WD10EACS-00D6B1, 01.01A01, max UDMA/133
[   37.065108] ata3.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   37.079444] ata3.00: configured for UDMA/100
[   37.565117] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   37.585522] ata4.00: ATA-7: SAMSUNG HD103UJ, 1AA01109, max UDMA7
[   37.585526] ata4.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   37.605502] ata4.00: configured for UDMA/100
[   37.605662] scsi 2:0:0:0: Direct-Access     ATA      WDC WD10EACS-00D 01.0 PQ: 0 ANSI: 5
[   37.605850] scsi 3:0:0:0: Direct-Access     ATA      SAMSUNG HD103UJ  1AA0 PQ: 0 ANSI: 5
[   37.606836] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 19
[   37.606892] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   37.606911] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
[   37.626383] ata_piix 0000:00:1f.2: version 2.12
[   37.626394] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[   37.629942] Driver 'sd' needs updating - please use bus_type methods
[   37.630066] sd 2:0:0:0: [sda] 1953525168 512-byte hardware sectors (1000205 MB)
[   37.630089] sd 2:0:0:0: [sda] Write Protect is off
[   37.630094] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   37.630127] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   37.630205] sd 2:0:0:0: [sda] 1953525168 512-byte hardware sectors (1000205 MB)
[   37.630224] sd 2:0:0:0: [sda] Write Protect is off
[   37.630228] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   37.630260] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   37.630266]  sda: sda2 < sda5 >
[   37.644668] sd 2:0:0:0: [sda] Attached SCSI disk
[   37.644764] sd 3:0:0:0: [sdb] 1953525168 512-byte hardware sectors (1000205 MB)
[   37.644785] sd 3:0:0:0: [sdb] Write Protect is off
[   37.644790] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   37.644826] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   37.644905] sd 3:0:0:0: [sdb] 1953525168 512-byte hardware sectors (1000205 MB)
[   37.644927] sd 3:0:0:0: [sdb] Write Protect is off
[   37.644931] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   37.644973] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   37.644979]  sdb: sdb1 sdb2
[   37.675397] sd 3:0:0:0: [sdb] Attached SCSI disk
[   37.682390] sd 2:0:0:0: Attached scsi generic sg0 type 0
[   37.682429] sd 3:0:0:0: Attached scsi generic sg1 type 0
[   37.777268] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 19
[   37.777312] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   37.777384] scsi4 : ata_piix
[   37.777620] scsi5 : ata_piix
[   37.778220] ata5: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x3800 irq 14
[   37.778224] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x3808 irq 15
[   38.011802] ata5.01: ATA-7: ST3808110AS, 3.AAE, max UDMA/133
[   38.011807] ata5.01: 156301488 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   38.094972] ata5.01: configured for UDMA/133
[   38.254133] scsi 4:0:1:0: Direct-Access     ATA      ST3808110AS      3.AA PQ: 0 ANSI: 5
[   38.254257] sd 4:0:1:0: [sdc] 156301488 512-byte hardware sectors (80026 MB)
[   38.254279] sd 4:0:1:0: [sdc] Write Protect is off
[   38.254284] sd 4:0:1:0: [sdc] Mode Sense: 00 3a 00 00
[   38.254318] sd 4:0:1:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   38.254396] sd 4:0:1:0: [sdc] 156301488 512-byte hardware sectors (80026 MB)
[   38.254416] sd 4:0:1:0: [sdc] Write Protect is off
[   38.254421] sd 4:0:1:0: [sdc] Mode Sense: 00 3a 00 00
[   38.254456] sd 4:0:1:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   38.254463]  sdc: sdc1 sdc2 < sdc5 >
[   38.300770] sd 4:0:1:0: [sdc] Attached SCSI disk
[   38.300830] sd 4:0:1:0: Attached scsi generic sg2 type 0
[   38.645004] Attempting manual resume
[   38.645008] swsusp: Resume From Partition 8:37
[   38.645011] PM: Checking swsusp image.
[   38.645139] PM: Resume from disk failed.
[   38.696674] kjournald starting.  Commit interval 5 seconds
[   38.696689] EXT3-fs: mounted filesystem with ordered data mode.
[   43.555217] Linux agpgart interface v0.102
[   43.662428] intel_rng: FWH not detected
[   43.695002] agpgart: Detected an Intel 945G Chipset.
[   43.695758] agpgart: Detected 7932K stolen memory.
[   43.710171] agpgart: AGP aperture is 256M @ 0xe0000000
[   43.765933] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   43.784930] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   43.894869] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   43.947729] iTCO_vendor_support: vendor-support=0
[   43.964431] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   43.975114] iTCO_wdt: Found a ICH7 or ICH7R TCO device (Version=2, TCOBASE=0xf060)
[   43.975161] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   43.998246] input: Power Button (FF) as /devices/virtual/input/input3
[   44.076737] ACPI: Power Button (FF) [PWRF]
[   44.076854] input: Power Button (CM) as /devices/virtual/input/input4
[   44.156592] ACPI: Power Button (CM) [PWRB]
[   45.574343] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 18 (level, low) -> IRQ 18
[   45.574382] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   46.127358] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input5
[   46.423044] parport_pc 00:0c: reported by Plug and Play ACPI
[   46.423116] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   47.013408] tg3: eth0: Link is up at 100 Mbps, full duplex.
[   47.013414] tg3: eth0: Flow control is off for TX and off for RX.
[   47.182659] NET: Registered protocol family 17
[   47.358017] loop: module loaded
[   47.377997] lp0: using parport0 (interrupt-driven).
[   47.493480] Adding 3004112k swap on /dev/sdc5.  Priority:-1 extents:1 across:3004112k
[   47.495809] Adding 481940k swap on /dev/sdb2.  Priority:-2 extents:1 across:481940k
[   48.062514] EXT3 FS on sdc1, internal journal
[   49.868648] kjournald starting.  Commit interval 5 seconds
[   49.868660] EXT3-fs warning: mounting fs with errors, running e2fsck is recommended
[   49.891098] EXT3 FS on sdb1, internal journal
[   49.891102] EXT3-fs: recovery complete.
[   49.893310] EXT3-fs: mounted filesystem with ordered data mode.
[   53.691788] kjournald starting.  Commit interval 5 seconds
[   53.691803] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[   53.706103] EXT3 FS on sda5, internal journal
[   53.706107] EXT3-fs: recovery complete.
[   53.707455] EXT3-fs: mounted filesystem with ordered data mode.
[   54.227659] ip_tables: (C) 2000-2006 Netfilter Core Team
[   54.906484] No dock devices found.
[   54.980078] NET: Registered protocol family 10
[   54.980539] lo: Disabled Privacy Extensions
[   56.547562] apm: BIOS not found.
[   61.807493] [drm] Initialized drm 1.1.0 20060810
[   61.811022] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 17
[   61.811036] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   61.811126] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   65.920086] eth0: no IPv6 routers present
[42149.321486] irq 21: nobody cared (try booting with the "irqpoll" option)
[42149.321497] Pid: 0, comm: swapper Not tainted 2.6.24-23-server #1
[42149.321519]  [<c016e4a4>] __report_bad_irq+0x24/0x80
[42149.321538]  [<c016e77b>] note_interrupt+0x27b/0x2c0
[42149.321556]  [<c016d9a0>] handle_IRQ_event+0x30/0x60
[42149.321568]  [<c016f146>] handle_fasteoi_irq+0x86/0xe0
[42149.321581]  [<c010a92b>] do_IRQ+0x3b/0x70
[42149.321599]  [<c0108def>] common_interrupt+0x23/0x28
[42149.321624]  [<c01062cc>] mwait_idle_with_hints+0x2c/0x60
[42149.321639]  [<c01066c3>] cpu_idle+0x73/0xd0
[42149.321650]  [<c043ea8f>] start_kernel+0x31f/0x3b0
[42149.321658]  [<c043e150>] unknown_bootoption+0x0/0x1f0
[42149.321680]  =======================
[42149.321682] handlers:
[42149.321684] [<f88e5ca0>] (usb_hcd_irq+0x0/0x60 [usbcore])
[42149.321707] [<f88db560>] (sil_interrupt+0x0/0x250 [sata_sil])
[42149.321716] Disabling IRQ #21
[56734.614923] ata4.00: exception Emask 0x52 SAct 0x0 SErr 0xffffffff action 0xe
[56734.614934] ata4: SError: { RecovData RecovComm UnrecovData Persist Proto HostInt PHYRdyChg PHYInt CommWake 10B8B Dispar BadCRC Handshk LinkSeq TrStaTrns UnrecFIS DevExch }
[56734.614951] ata4.00: cmd 25/00:30:4f:10:78/00:00:43:00:00/e0 tag 0 dma 24576 in
[56734.614954]          res 40/00:fe:00:00:00/00:00:00:00:00/50 Emask 0x72 (host bus error)
[56734.614959] ata4.00: status: { DRDY }
[56734.614975] ata4: hard resetting link
[56735.363643] ata4: SATA link down (SStatus FFFFFFFF SControl FFFFFFFF)
[56735.363657] ata4: failed to recover some devices, retrying in 5 secs
[56740.365267] ata4: hard resetting link
[56740.714678] ata4: SATA link down (SStatus FFFFFFFF SControl FFFFFFFF)
[56740.714696] ata4: failed to recover some devices, retrying in 5 secs
[56745.716306] ata4: hard resetting link
[56746.065711] ata4: SATA link down (SStatus FFFFFFFF SControl FFFFFFFF)
[56746.065726] ata4.00: disabled
[56746.574862] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[56746.574870] sd 3:0:0:0: [sdb] Sense Key : Aborted Command [current] [descriptor]
[56746.574879] Descriptor sense data with sense descriptors (in hex):
[56746.574883]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00
[56746.574901]         00 00 00 00
[56746.574908] sd 3:0:0:0: [sdb] Add. Sense: No additional sense information
[56746.574919] end_request: I/O error, dev sdb, sector 1131941967
[56746.574934] sd 3:0:0:0: rejecting I/O to offline device
[56746.574946] sd 3:0:0:0: rejecting I/O to offline device
[56746.574961] ata4: EH complete
[56746.574976] sd 3:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[56746.574984] end_request: I/O error, dev sdb, sector 1132204111
[56746.575016] sd 3:0:0:0: rejecting I/O to offline device
[56746.575030] ata4.00: detaching (SCSI 3:0:0:0)
[56746.575307] Buffer I/O error on device sdb1, logical block 122000601
[56746.575314] lost page write due to I/O error on sdb1
[56746.575326] Aborting journal on device sdb1.
[56746.575339] Buffer I/O error on device sdb1, logical block 121995778
[56746.575346] lost page write due to I/O error on sdb1
[56746.575409] journal commit I/O error
[56746.575475] Buffer I/O error on device sdb1, logical block 98729989
[56746.575481] lost page write due to I/O error on sdb1
[56746.585308] ext3_abort called.
[56746.585318] EXT3-fs error (device sdb1): ext3_journal_start_sb: Detected aborted journal
[56746.585323] Remounting filesystem read-only
[56746.827527] sd 3:0:0:0: [sdb] Synchronizing SCSI cache
[56746.827600] sd 3:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[56746.827608] sd 3:0:0:0: [sdb] Stopping disk
[56746.827623] sd 3:0:0:0: [sdb] START_STOP FAILED
[56746.827627] sd 3:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[56751.916109] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #2 offset 0
[56780.589352] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #25239553 offset 0
[56780.589399] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #25239553 offset 0
[56780.589462] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #2 offset 0 


```

Anything you can do to help would be great! Thanks

---

### Post by taurus on 2009-03-05
> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                    0  0
# /dev/sda1
UUID=3747dfcc-ef9e-499c-8bdd-c8bff3e29637  /              ext3         relatime,errors=remount-ro  0  1
# /dev/sda5
UUID=4bb683f1-cf66-4af2-a4f6-8bd58743f65f  none           swap         sw                          0  0
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8       0  0


/dev/sdb1                                  /media/sdb1    ext3         defaults     0  0
**[COLOR="Red"]/dev/sdb2                                  /media/sdb2    swap         defaults     0  0[/COLOR]**
/dev/sdc1                                  /media/sdc1    ext3         defaults     0  0
**[COLOR="Red"]/dev/sdc5                                  /media/sdc5    swap         defaults     0  0[/COLOR]**
/dev/sda5                                  /media/sda5    ext3         defaults     0  0


Can you post the outputs of these commands?

```
sudo fdisk -l
sudo blkid
df -h
```

---

### Post by pyroger101 on 2009-03-05
sudo fdisk -l:
```

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5697f496

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        9355    75144006   83  Linux
/dev/sdc2            9356        9729     3004155    5  Extended
/dev/sdc5            9356        9729     3004123+  82  Linux swap / Solaris

```

sudo blkid:
```

/dev/sdc1: UUID="3747dfcc-ef9e-499c-8bdd-c8bff3e29637" TYPE="ext3"
/dev/sdc5: TYPE="swap" UUID="4bb683f1-cf66-4af2-a4f6-8bd58743f65f"

```

df -h:
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sdc1              72G  2.8G   65G   5% /
varrun                501M  452K  501M   1% /var/run
varlock               501M     0  501M   0% /var/lock
udev                  501M   40K  501M   1% /dev
devshm                501M   12K  501M   1% /dev/shm
/dev/sdb1             917G  384G  487G  45% /media/sdb1
/dev/sdc1              72G  2.8G   65G   5% /media/sdc1
/dev/sda5             917G  558G  314G  65% /media/sda5
gvfs-fuse-daemon       72G  2.8G   65G   5% /home/media-admin/.gvfs

```


thanks... hope that helps....

---

### Post by taurus on 2009-03-05
What happens to the other two harddrives?  They don't show up from **sudo fdisk -l**.  Are those internal or external drives?

And apparently, you have /dev/sdc1 mounted twice, one to / and one to /media/sdc1!

---

### Post by pyroger101 on 2009-03-05
Ok i have three drives, one 80gb that is internally connected via SATA. The other two are 1tb also internal drives that go trough a SATA pci card.

These readings were taken after the malfunction. If i reboot the machine twice everything works great for a few hours.

Thats strange about the sdc... ill do something about that now..


Thats really weird... the file system is on sda not sdc...?! hmmmmmmm

---

### Post by taurus on 2009-03-05
Instead of using /dev/sda5 & /dev/sdb1 for the other two drives, you should consider using the UUID's for them since UUID is unique for each drive even if /dev/sda1 changes to /dev/sdc1 or whatever later.

---

