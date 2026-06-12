---
title: "touchpad bug"
date: 2010-07-11
forum: Hardware
---

### Post by jason.rgd on 2010-07-11
I have a HP pavillion dv 6845 and a slightly old synaptic trackpad!! ubuntu installs without any errors but after installation I found one bug with the trackpad on/off button... 

when is the bug encountered?
if my trackpad is on and I switch it off... everything is fine.. but if I switch it on back again... then my usb mouse doesn't work and even keyboard stops working.. my ubuntu system is upto date...

how to recover
restart the system...

other comments
upto ubuntu 9.10 everything was working fine!!!  don't know about 32 bit!!

---

### Post by ubudog on 2010-07-11
Open a terminal (Applications>Accessories>Terminal) and post the output of ```
dmesg
```  That will probably be very helpful.

---

### Post by jason.rgd on 2010-07-11
[    0.512435] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.512437] EDD information not available.
[    0.512909] ACPI: Battery Slot [BAT0] (battery present)
[    0.528092] Freeing initrd memory: 8143k freed
[    0.543673] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    0.620562] ata1.00: ATAPI: TSSTcorp CDDVDW TS-L632N, 0503, max MWDMA2
[    0.660465] ata1.00: configured for MWDMA2
[    0.663211] scsi 0:0:0:0: CD-ROM            TSSTcorp CDDVDW TS-L632N  0503 PQ: 0 ANSI: 5
[    0.667342] sr0: scsi3-mmc drive: 62x/62x writer dvd-ram cd/rw xa/form2 cdda tray
[    0.667345] Uniform CD-ROM driver Revision: 3.20
[    0.667455] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    0.667509] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    0.667583] Freeing unused kernel memory: 880k freed
[    0.668032] Write protecting the kernel read-only data: 7692k
[    0.685491] udev: starting version 151
[    0.750097] usb 1-4: new high speed USB device using ehci_hcd and address 2
[    0.807857]   alloc irq_desc for 20 on node -1
[    0.807860]   alloc kstat_irqs on node -1
[    0.807869] ohci1394 0000:09:09.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.809038] ahci 0000:00:1f.2: version 3.0
[    0.809054] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.809099]   alloc irq_desc for 28 on node -1
[    0.809101]   alloc kstat_irqs on node -1
[    0.809113] ahci 0000:00:1f.2: irq 28 for MSI/MSI-X
[    0.809183] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x7 impl SATA mode
[    0.809187] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ccc 
[    0.809194] ahci 0000:00:1f.2: setting latency timer to 64
[    0.809521] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    0.809544] r8169 0000:08:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.809594] r8169 0000:08:00.0: setting latency timer to 64
[    0.809675]   alloc irq_desc for 29 on node -1
[    0.809677]   alloc kstat_irqs on node -1
[    0.809694] r8169 0000:08:00.0: irq 29 for MSI/MSI-X
[    0.810351] eth0: RTL8101e at 0xffffc9000037a000, 00:23:8b:8c:22:c5, XID 94200000 IRQ 29
[    0.833969] scsi2 : ahci
[    0.836433] scsi3 : ahci
[    0.836551] scsi4 : ahci
[    0.836720] ata3: SATA max UDMA/133 abar m2048@0xf8404000 port 0xf8404100 irq 28
[    0.836725] ata4: SATA max UDMA/133 abar m2048@0xf8404000 port 0xf8404180 irq 28
[    0.836729] ata5: SATA max UDMA/133 abar m2048@0xf8404000 port 0xf8404200 irq 28
[    0.864621] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[20]  MMIO=[f8100000-f81007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    0.903593] usb 1-4: configuration #1 chosen from 1 choice
[    0.911231] Initializing USB Mass Storage driver...
[    0.911393] scsi5 : SCSI emulation for USB Mass Storage devices
[    0.911490] usbcore: registered new interface driver usb-storage
[    0.911494] USB Mass Storage support registered.
[    0.911500] usb-storage: device found at 2
[    0.911501] usb-storage: waiting for device to settle before scanning
[    1.020210] usb 2-4: new high speed USB device using ehci_hcd and address 2
[    1.180221] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.180256] ata4: SATA link down (SStatus 0 SControl 300)
[    1.180286] ata5: SATA link down (SStatus 0 SControl 300)
[    1.181016] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    1.181097] ata3.00: ATA-8: TOSHIBA MK2546GSX, LB014C, max UDMA/100
[    1.181103] ata3.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.181913] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    1.182012] ata3.00: configured for UDMA/100
[    1.200222] scsi 2:0:0:0: Direct-Access     ATA      TOSHIBA MK2546GS LB01 PQ: 0 ANSI: 5
[    1.200403] sd 2:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    1.200418] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    1.200514] sd 2:0:0:0: [sda] Write Protect is off
[    1.200518] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.200546] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.200699]  sda:
[    1.247743] usb 2-4: configuration #1 chosen from 1 choice
[    1.280819]  sda1 sda2 < sda5 >
[    1.317402] sd 2:0:0:0: [sda] Attached SCSI disk
[    1.712427] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    1.712432] EXT4-fs (sda1): write access will be enabled during recovery
[    1.830057] usb 7-2: new full speed USB device using uhci_hcd and address 2
[    2.009867] usb 7-2: configuration #1 chosen from 1 choice
[    2.180507] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00241b00c1a66001]
[    2.415239] usb 1-4: USB disconnect, address 2
[    3.001816] EXT4-fs (sda1): recovery complete
[    3.002336] EXT4-fs (sda1): mounted filesystem with ordered data mode
[   12.960049] usb 2-1: new high speed USB device using ehci_hcd and address 4
[   14.942233] udev: starting version 151
[   14.995756] Adding 6022136k swap on /dev/sda5.  Priority:-1 extents:1 across:6022136k 
[   15.015578] lp: driver loaded but no devices found
[   15.021031] vga16fb: initializing
[   15.021036] vga16fb: mapped to 0xffff8800000a0000
[   15.021108] fb0: VGA16 VGA frame buffer device
[   15.277275] type=1505 audit(1278822651.257:2):  operation="profile_load" pid=660 name="/sbin/dhclient3"
[   15.278015] type=1505 audit(1278822651.257:3):  operation="profile_load" pid=660 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   15.278413] type=1505 audit(1278822651.257:4):  operation="profile_load" pid=660 name="/usr/lib/connman/scripts/dhclient-script"
[   15.284487] nvidia: module license 'NVIDIA' taints kernel.
[   15.284491] Disabling lock debugging due to kernel taint
[   15.298166] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   15.298172] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[   15.298178] sr 0:0:0:0: [sr0] Add. Sense: Logical block address out of range
[   15.298183] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[   15.298193] end_request: I/O error, dev sr0, sector 0
[   15.298258] Buffer I/O error on device sr0, logical block 0
[   15.330082] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   15.330089] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[   15.330094] sr 0:0:0:0: [sr0] Add. Sense: Logical block address out of range
[   15.330100] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[   15.330110] end_request: I/O error, dev sr0, sector 0
[   15.330174] Buffer I/O error on device sr0, logical block 0
[   15.336318] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   15.336324] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[   15.336329] sr 0:0:0:0: [sr0] Add. Sense: Logical block address out of range
[   15.336334] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[   15.336344] end_request: I/O error, dev sr0, sector 0
[   15.336405] Buffer I/O error on device sr0, logical block 0
[   15.337779] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   15.337784] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[   15.337789] sr 0:0:0:0: [sr0] Add. Sense: Logical block address out of range
[   15.337794] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[   15.337804] end_request: I/O error, dev sr0, sector 0
[   15.337867] Buffer I/O error on device sr0, logical block 0
[   15.339147] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   15.339152] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[   15.339157] sr 0:0:0:0: [sr0] Add. Sense: Logical block address out of range
[   15.339161] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[   15.339171] end_request: I/O error, dev sr0, sector 0
[   15.339232] Buffer I/O error on device sr0, logical block 0
[   15.340559] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   15.340564] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[   15.340569] sr 0:0:0:0: [sr0] Add. Sense: Logical block address out of range
[   15.340574] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[   15.340583] end_request: I/O error, dev sr0, sector 0
[   15.340646] Buffer I/O error on device sr0, logical block 0
[   15.346420] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   15.346427] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[   15.346432] sr 0:0:0:0: [sr0] Add. Sense: Logical block address out of range
[   15.346438] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[   15.346448] end_request: I/O error, dev sr0, sector 0
[   15.346513] Buffer I/O error on device sr0, logical block 0
[   15.347882] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   15.347888] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[   15.347892] sr 0:0:0:0: [sr0] Add. Sense: Logical block address out of range
[   15.347897] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[   15.347907] end_request: I/O error, dev sr0, sector 0
[   15.349182] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   15.349187] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[   15.349192] sr 0:0:0:0: [sr0] Add. Sense: Logical block address out of range
[   15.349197] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[   15.349207] end_request: I/O error, dev sr0, sector 0
[   15.350500] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   15.350506] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[   15.350511] sr 0:0:0:0: [sr0] Add. Sense: Logical block address out of range
[   15.350515] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[   15.350525] end_request: I/O error, dev sr0, sector 0
[   15.352441] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   15.352447] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[   15.352452] sr 0:0:0:0: [sr0] Add. Sense: Logical block address out of range
[   15.352457] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[   15.352467] end_request: I/O error, dev sr0, sector 0
[   15.353804] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   15.353809] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[   15.353814] sr 0:0:0:0: [sr0] Add. Sense: Logical block address out of range
[   15.353819] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[   15.353829] end_request: I/O error, dev sr0, sector 0
[   15.355191] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   15.355196] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[   15.355201] sr 0:0:0:0: [sr0] Add. Sense: Logical block address out of range
[   15.355206] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[   15.355216] end_request: I/O error, dev sr0, sector 0
[   15.356576] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   15.356582] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[   15.356586] sr 0:0:0:0: [sr0] Add. Sense: Logical block address out of range
[   15.356591] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[   15.356601] end_request: I/O error, dev sr0, sector 0
[   15.357957] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   15.357962] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[   15.357967] sr 0:0:0:0: [sr0] Add. Sense: Logical block address out of range
[   15.357972] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[   15.357982] end_request: I/O error, dev sr0, sector 0
[   15.360118] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   15.360124] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[   15.360129] sr 0:0:0:0: [sr0] Add. Sense: Logical block address out of range
[   15.360135] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[   15.360145] end_request: I/O error, dev sr0, sector 0
[   15.361496] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   15.361501] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[   15.361506] sr 0:0:0:0: [sr0] Add. Sense: Logical block address out of range
[   15.361511] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[   15.361521] end_request: I/O error, dev sr0, sector 0
[   15.367382] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   15.367389] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[   15.367394] sr 0:0:0:0: [sr0] Add. Sense: Logical block address out of range
[   15.367400] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[   15.367410] end_request: I/O error, dev sr0, sector 0
[   15.368833] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   15.368839] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[   15.368843] sr 0:0:0:0: [sr0] Add. Sense: Logical block address out of range
[   15.368849] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[   15.368859] end_request: I/O error, dev sr0, sector 0
[   15.370224] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   15.370229] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[   15.370234] sr 0:0:0:0: [sr0] Add. Sense: Logical block address out of range
[   15.370239] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[   15.370249] end_request: I/O error, dev sr0, sector 0
[   15.371611] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   15.371616] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[   15.371621] sr 0:0:0:0: [sr0] Add. Sense: Logical block address out of range
[   15.371626] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[   15.371636] end_request: I/O error, dev sr0, sector 0
[   15.372993] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   15.372998] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[   15.373002] sr 0:0:0:0: [sr0] Add. Sense: Logical block address out of range
[   15.373007] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[   15.373017] end_request: I/O error, dev sr0, sector 0
[   15.374374] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   15.374379] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[   15.374383] sr 0:0:0:0: [sr0] Add. Sense: Logical block address out of range
[   15.374388] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[   15.374398] end_request: I/O error, dev sr0, sector 0
[   15.375674] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   15.375679] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[   15.375684] sr 0:0:0:0: [sr0] Add. Sense: Logical block address out of range
[   15.375688] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[   15.375698] end_request: I/O error, dev sr0, sector 0
[   15.377052] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   15.377057] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[   15.377062] sr 0:0:0:0: [sr0] Add. Sense: Logical block address out of range
[   15.377067] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[   15.377077] end_request: I/O error, dev sr0, sector 0
[   15.378423] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   15.378429] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[   15.378433] sr 0:0:0:0: [sr0] Add. Sense: Logical block address out of range
[   15.378438] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[   15.378448] end_request: I/O error, dev sr0, sector 0
[   15.379806] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   15.379811] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[   15.379816] sr 0:0:0:0: [sr0] Add. Sense: Logical block address out of range
[   15.379821] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[   15.379831] end_request: I/O error, dev sr0, sector 0
[   15.381191] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   15.381196] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[   15.381201] sr 0:0:0:0: [sr0] Add. Sense: Logical block address out of range
[   15.381206] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[   15.381216] end_request: I/O error, dev sr0, sector 0
[   15.382796] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   15.382801] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[   15.382806] sr 0:0:0:0: [sr0] Add. Sense: Logical block address out of range
[   15.382810] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[   15.382820] end_request: I/O error, dev sr0, sector 0
[   15.391801] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   15.391809] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[   15.391814] sr 0:0:0:0: [sr0] Add. Sense: Logical block address out of range
[   15.391820] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[   15.391830] end_request: I/O error, dev sr0, sector 0
[   15.400086] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   15.400094] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[   15.400099] sr 0:0:0:0: [sr0] Add. Sense: Logical block address out of range
[   15.400105] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[   15.400116] end_request: I/O error, dev sr0, sector 0
[   15.401672] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   15.401677] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[   15.401682] sr 0:0:0:0: [sr0] Add. Sense: Logical block address out of range
[   15.401687] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[   15.401697] end_request: I/O error, dev sr0, sector 0
[   15.403061] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   15.403067] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[   15.403071] sr 0:0:0:0: [sr0] Add. Sense: Logical block address out of range
[   15.403077] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[   15.403086] end_request: I/O error, dev sr0, sector 0
[   15.404398] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   15.404403] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[   15.404408] sr 0:0:0:0: [sr0] Add. Sense: Logical block address out of range
[   15.404413] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[   15.404422] end_request: I/O error, dev sr0, sector 0
[   15.416967] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   15.416974] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[   15.416979] sr 0:0:0:0: [sr0] Add. Sense: Logical block address out of range
[   15.416985] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[   15.416995] end_request: I/O error, dev sr0, sector 0
[   15.418410] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   15.418415] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[   15.418420] sr 0:0:0:0: [sr0] Add. Sense: Logical block address out of range
[   15.418424] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[   15.418434] end_request: I/O error, dev sr0, sector 0
[   15.419800] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   15.419804] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[   15.419809] sr 0:0:0:0: [sr0] Add. Sense: Logical block address out of range
[   15.419813] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[   15.419823] end_request: I/O error, dev sr0, sector 0
[   15.421604] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   15.421609] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[   15.421614] sr 0:0:0:0: [sr0] Add. Sense: Logical block address out of range
[   15.421619] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[   15.421629] end_request: I/O error, dev sr0, sector 0
[   15.423284] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   15.423290] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[   15.423295] sr 0:0:0:0: [sr0] Add. Sense: Logical block address out of range
[   15.423301] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[   15.423311] end_request: I/O error, dev sr0, sector 0
[   15.424760] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   15.424765] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[   15.424770] sr 0:0:0:0: [sr0] Add. Sense: Logical block address out of range
[   15.424776] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[   15.424785] end_request: I/O error, dev sr0, sector 0
[   15.430573] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   15.430581] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[   15.430586] sr 0:0:0:0: [sr0] Add. Sense: Logical block address out of range
[   15.430592] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[   15.430602] end_request: I/O error, dev sr0, sector 0
[   15.431991] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   15.431996] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[   15.432001] sr 0:0:0:0: [sr0] Add. Sense: Logical block address out of range
[   15.432006] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[   15.432016] end_request: I/O error, dev sr0, sector 0
[   15.433537] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   15.433543] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[   15.433548] sr 0:0:0:0: [sr0] Add. Sense: Logical block address out of range
[   15.433553] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[   15.433563] end_request: I/O error, dev sr0, sector 0
[   15.434901] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   15.434906] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[   15.434910] sr 0:0:0:0: [sr0] Add. Sense: Logical block address out of range
[   15.434915] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[   15.434925] end_request: I/O error, dev sr0, sector 0
[   15.436281] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   15.436286] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[   15.436291] sr 0:0:0:0: [sr0] Add. Sense: Logical block address out of range
[   15.436296] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[   15.436306] end_request: I/O error, dev sr0, sector 0
[   15.437661] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   15.437666] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[   15.437671] sr 0:0:0:0: [sr0] Add. Sense: Logical block address out of range
[   15.437676] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[   15.437685] end_request: I/O error, dev sr0, sector 0
[   15.438962] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   15.438967] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[   15.438972] sr 0:0:0:0: [sr0] Add. Sense: Logical block address out of range
[   15.438977] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[   15.438987] end_request: I/O error, dev sr0, sector 0
[   15.440364] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   15.440369] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[   15.440373] sr 0:0:0:0: [sr0] Add. Sense: Logical block address out of range
[   15.440378] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[   15.440388] end_request: I/O error, dev sr0, sector 0
[   15.441807] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   15.441812] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[   15.441817] sr 0:0:0:0: [sr0] Add. Sense: Logical block address out of range
[   15.441822] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[   15.441838] end_request: I/O error, dev sr0, sector 0
[   15.443398] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   15.443403] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[   15.443408] sr 0:0:0:0: [sr0] Add. Sense: Logical block address out of range
[   15.443413] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[   15.443422] end_request: I/O error, dev sr0, sector 0
[   15.722444] r8169: eth0: link down
[   15.722707] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   15.762401] acpi device:04: registered as cooling_device2
[   15.762584] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/LNXVIDEO:00/input/input6
[   15.762641] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   15.860686]   alloc irq_desc for 22 on node -1
[   15.860690]   alloc kstat_irqs on node -1
[   15.860698] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   15.860742] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   15.864376] sdhci: Secure Digital Host Controller Interface driver
[   15.864380] sdhci: Copyright(c) Pierre Ossman
[   15.865704] sdhci-pci 0000:09:09.1: SDHCI controller found [1180:0822] (rev 22)
[   15.865722] sdhci-pci 0000:09:09.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[   15.866745] sdhci-pci 0000:09:09.1: Will use DMA mode even though HW doesn't fully claim to support it.
[   15.867785] Registered led device: mmc0::
[   15.868824] mmc0: SDHCI controller on PCI [0000:09:09.1] using DMA
[   15.877747] ricoh-mmc: Ricoh MMC Controller disabling driver
[   15.877750] ricoh-mmc: Copyright(c) Philip Langdale
[   15.877779] ricoh-mmc: Ricoh MMC controller found at 0000:09:09.2 [1180:0843] (rev 12)
[   15.877798] ricoh-mmc: Controller is now disabled.
[   15.907649] Bluetooth: Core ver 2.15
[   15.907738] NET: Registered protocol family 31
[   15.907741] Bluetooth: HCI device and connection manager initialized
[   15.907744] Bluetooth: HCI socket layer initialized
[   15.910748] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   15.911086] usbcore: registered new interface driver btusb
[   15.962352] Bluetooth: L2CAP ver 2.14
[   15.962355] Bluetooth: L2CAP socket layer initialized
[   15.969624] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   15.969628] Bluetooth: BNEP filters: protocol multicast
[   15.980971] Bridge firewalling registered
[   15.984780] Linux video capture interface: v2.00
[   15.987842] uvcvideo: Found UVC 1.00 device HP Webcam (0c45:62c0)
[   15.996213] cfg80211: Calling CRDA to update world regulatory domain
[   16.022990] nvidia 0000:01:00.0: power state changed by ACPI to D0
[   16.023062] nvidia 0000:01:00.0: power state changed by ACPI to D0
[   16.023079] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   16.023097] nvidia 0000:01:00.0: setting latency timer to 64
[   16.023106] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   16.025965] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  195.36.24  Thu Apr 22 19:10:14 PDT 2010
[   16.046275] input: HP Webcam as /devices/pci0000:00/0000:00:1d.7/usb2/2-4/2-4:1.0/input/input7
[   16.046340] usbcore: registered new interface driver uvcvideo
[   16.046343] USB Video Class driver (v0.1.0)
[   16.065399] cfg80211: World regulatory domain updated:
[   16.065402] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   16.065406] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.065408] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   16.065411] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   16.065413] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.065415] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.066189] Bluetooth: SCO (Voice Link) ver 0.6
[   16.066191] Bluetooth: SCO socket layer initialized
[   16.076029] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[   16.076032] iwl3945: Copyright(c) 2003-2009 Intel Corporation
[   16.076178] iwl3945 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   16.076199] iwl3945 0000:02:00.0: setting latency timer to 64
[   16.157366] iwl3945 0000:02:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   16.157369] iwl3945 0000:02:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   16.157565]   alloc irq_desc for 30 on node -1
[   16.157567]   alloc kstat_irqs on node -1
[   16.157616] iwl3945 0000:02:00.0: irq 30 for MSI/MSI-X
[   16.164126] phy0: Selected rate control algorithm 'iwl-3945-rs'
[   16.178263] iwl3945 0000:02:00.0: firmware: requesting iwlwifi-3945-2.ucode
[   16.196780] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input8
[   16.220007] Bluetooth: RFCOMM TTY layer initialized
[   16.220012] Bluetooth: RFCOMM socket layer initialized
[   16.220014] Bluetooth: RFCOMM ver 1.11
[   16.287834] Console: switching to colour frame buffer device 80x30
[   16.454274] iwl3945 0000:02:00.0: loaded firmware version 15.32.2.9
[   16.472345] ppdev: user-space parallel port driver
[   16.518358] Registered led device: iwl-phy0::radio
[   16.518860] Registered led device: iwl-phy0::assoc
[   16.518947] Registered led device: iwl-phy0::RX
[   16.519211] Registered led device: iwl-phy0::TX
[   16.543685] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   17.201156] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04711/0xa00000
[   17.305707] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9
[   18.172158] usb 2-1: configuration #1 chosen from 1 choice
[   18.176743] scsi6 : SCSI emulation for USB Mass Storage devices
[   18.177874] usb-storage: device found at 4
[   18.177876] usb-storage: waiting for device to settle before scanning
[   22.637453] cdrom: This disc doesn't have any tracks I recognize!
[   23.170272] usb-storage: device scan complete
[   23.359121] scsi 6:0:0:0: Direct-Access     SAMSUNG  HM500JI               PQ: 0 ANSI: 2
[   23.359843] sd 6:0:0:0: Attached scsi generic sg2 type 0
[   23.362775] sd 6:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[   23.365061] sd 6:0:0:0: [sdb] Write Protect is off
[   23.365069] sd 6:0:0:0: [sdb] Mode Sense: 38 00 00 00
[   23.365074] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[   23.368291] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[   23.368298]  sdb: sdb1
[   23.809163] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[   23.809169] sd 6:0:0:0: [sdb] Attached SCSI disk
[ 2968.210184] usb 4-2: new low speed USB device using uhci_hcd and address 2
[ 2968.386535] usb 4-2: configuration #1 chosen from 1 choice
[ 2968.771903] usbcore: registered new interface driver hiddev
[ 2968.785805] input: PIXART USB OPTICAL MOUSE as /devices/pci0000:00/0000:00:1a.1/usb4/4-2/4-2:1.0/input/input10
[ 2968.786022] generic-usb 0003:093A:2510.0001: input,hidraw0: USB HID v1.11 Mouse [PIXART USB OPTICAL MOUSE] on usb-0000:00:1a.1-2/input0
[ 2968.786076] usbcore: registered new interface driver usbhid
[ 2968.786082] usbhid: v2.6:USB HID core driver
[ 4290.476986] usb 2-1: USB disconnect, address 4
[ 4315.220185] usb 2-2: new high speed USB device using ehci_hcd and address 5
[ 4320.374634] usb 2-2: configuration #1 chosen from 1 choice
[ 4320.376425] scsi7 : SCSI emulation for USB Mass Storage devices
[ 4320.376574] usb-storage: device found at 5
[ 4320.376579] usb-storage: waiting for device to settle before scanning
[ 4325.370570] usb-storage: device scan complete
[ 4325.669893] scsi 7:0:0:0: Direct-Access     SAMSUNG  HM500JI               PQ: 0 ANSI: 2
[ 4325.675589] sd 7:0:0:0: Attached scsi generic sg2 type 0
[ 4325.677487] sd 7:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[ 4325.679722] sd 7:0:0:0: [sdb] Write Protect is off
[ 4325.679729] sd 7:0:0:0: [sdb] Mode Sense: 38 00 00 00
[ 4325.679734] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[ 4325.682963] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[ 4325.682971]  sdb: sdb1
[ 4326.115489] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[ 4326.115498] sd 7:0:0:0: [sdb] Attached SCSI disk
[ 4329.020005] ata1: drained 4700 bytes to clear DRQ.
[ 4329.033092] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[ 4329.033098] sr 0:0:0:0: CDB: Test Unit Ready: 00 00 00 00 00 00
[ 4329.033110] ata1.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[ 4329.033112]          res 7f/7f:7f:7f:7f:7f/00:00:00:00:00/7f Emask 0x2 (HSM violation)
[ 4329.033115] ata1.00: status: { DRDY DF DRQ ERR }
[ 4329.033152] ata1: soft resetting link
[ 4329.250542] ata1.00: configured for MWDMA2
[ 4329.252216] ata1: EH complete
jason@Lily:~$

---

