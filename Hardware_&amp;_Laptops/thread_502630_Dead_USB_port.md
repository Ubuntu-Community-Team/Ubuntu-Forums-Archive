---
title: "Dead USB port"
date: 2007-07-16
forum: Hardware &amp; Laptops
---

### Post by ndogg1982 on 2007-07-16
OK, so this isn't an Ubuntu problem, but I figured I'd ask here since the help is so good. I have one USB 2.0 port on the front of my pc that just will not work. No matter what I plug into it, nothing gets recognized by the OS (be it Ubuntu, Windows, or even other linux distros.) However, I do know that power is still running through the port because if I plug in a cheap usb joystick, the power light comes on. Plus, Ubuntu and Windows both recognized the port and nothing seems wrong with it as far as driver issues go. This was the whole reason I switched to linux in the first place, because one day ALL the usb ports stopped working in Windows, but when I switched to Ubuntu and other distros the 1.1 ports worked fine. So, I'm figuring that it's just a dead port...but is there any fix for that? Other than installing a brand new port? Any help or suggestions will be appreciated. Thanks.

---

### Post by jgordon510 on 2007-07-16
The port on the front has a cable that connects to the motherboard.  Did you check to make sure it's still connected?  Depending on the type of connection, it's entirely possible that the power is still flowing to the usb port, but not the data.

---

### Post by fdrake on 2007-07-16
> **ndogg1982 said:**
>  one day ALL the usb ports stopped working in Windows, but when I switched to Ubuntu and other distros the 1.1 ports worked fine. So, I'm figuring that it's just a dead port...

that's weird, all in 1 day. can u post here the output  of this commands on the terminal :

dmesg


lsusb -v

and make sure u plugin something

---

### Post by ndogg1982 on 2007-07-16
That makes sense, I did check that the last time I opened the box. Question: does the power cable and data cable both run to the same spot on the mobo? When I last checked, there are 3 or 4 wires that go into a single connector then plug into the mobo. Maybe one wire is loose from the connector? That connector has not only the 2.0 port, but also a 9 in 1 card reader as well, which also does not work. I will go ahead and recheck all the connections then post what I can find.

---

### Post by ndogg1982 on 2007-07-16
> **fdrake said:**
> that's weird, all in 1 day. can u post here the output  of this commands on the terminal :

dmesg


lsusb -v

and make sure u plugin something

[HTML][   23.180580] NET: Registered protocol family 2
[   23.219729] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   23.219816] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[   23.219905] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[   23.219952] TCP: Hash tables configured (established 16384 bind 8192)
[   23.219955] TCP reno registered
[   23.231745] checking if image is initramfs... it is
[   23.731644] Freeing initrd memory: 6764k freed
[   23.732222] audit: initializing netlink socket (disabled)
[   23.732240] audit(1184405741.192:1): initialized
[   23.732368] VFS: Disk quotas dquot_6.5.1
[   23.732390] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   23.732447] io scheduler noop registered
[   23.732450] io scheduler anticipatory registered
[   23.732452] io scheduler deadline registered
[   23.732460] io scheduler cfq registered (default)
[   23.732722] isapnp: Scanning for PnP cards...
[   24.083768] isapnp: No Plug & Play device found
[   24.117172] Real Time Clock Driver v1.12ac
[   24.117224] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   24.117387] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   24.118616] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   24.118939] mice: PS/2 mouse device common for all mice
[   24.119517] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   24.119779] input: Macintosh mouse button emulation as /class/input/input0
[   24.119817] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   24.119821] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   24.120128] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   24.123746] serio: i8042 KBD port at 0x60,0x64 irq 1
[   24.123756] serio: i8042 AUX port at 0x60,0x64 irq 12
[   24.123938] EISA: Probing bus 0 at eisa.0
[   24.123948] Cannot allocate resource for EISA slot 1
[   24.123950] Cannot allocate resource for EISA slot 2
[   24.123952] Cannot allocate resource for EISA slot 3
[   24.123978] EISA: Detected 0 cards.
[   24.153986] TCP cubic registered
[   24.153993] NET: Registered protocol family 1
[   24.154018] Using IPI No-Shortcut mode
[   24.154088] ACPI: (supports S0 S1 S3 S4 S5)
[   24.154135]   Magic number: 15:40:576
[   24.154230]   hash matches device ptyb8
[   24.154640] Freeing unused kernel memory: 328k freed
[   24.156790] Time: tsc clocksource has been installed.
[   24.171144] input: AT Translated Set 2 keyboard as /class/input/input1
[   25.363418] Capability LSM initialized
[   25.400353] ACPI: Processor [CPU0] (supports 8 throttling states)
[   25.400365] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[   25.400373] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[   25.400379] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[   25.871994] SCSI subsystem initialized
[   25.877286] libata version 2.20 loaded.
[   25.880320] sata_sil 0000:00:11.0: version 2.2
[   25.880359] ACPI: PCI Interrupt 0000:00:11.0[A] -> GSI 23 (level, low) -> IRQ 16
[   25.880380] PCI: Setting latency timer of device 0000:00:11.0 to 64
[   25.880439] ata1: SATA max UDMA/100 cmd 0xd8848680 ctl 0xd884868a bmdma 0xd8848600 irq 16
[   25.880470] ata2: SATA max UDMA/100 cmd 0xd88486c0 ctl 0xd88486ca bmdma 0xd8848608 irq 16
[   25.880488] scsi0 : sata_sil
[   25.899583] usbcore: registered new interface driver usbfs
[   25.899614] usbcore: registered new interface driver hub
[   25.899638] usbcore: registered new device driver usb
[   25.919069] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   26.007509] 8139too Fast Ethernet driver 0.9.28
[   26.190674] ata1: SATA link down (SStatus 0 SControl 310)
[   26.190701] scsi1 : sata_sil
[   26.501733] ata2: SATA link down (SStatus 0 SControl 310)
[   26.501853] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 22 (level, low) -> IRQ 17
[   26.501879] PCI: Setting latency timer of device 0000:00:12.0 to 64
[   26.501928] ata3: SATA max UDMA/100 cmd 0xd8862480 ctl 0xd886248a bmdma 0xd8862400 irq 17
[   26.501955] ata4: SATA max UDMA/100 cmd 0xd88624c0 ctl 0xd88624ca bmdma 0xd8862408 irq 17
[   26.501974] scsi2 : sata_sil
[   26.812792] ata3: SATA link down (SStatus 0 SControl 310)
[   26.812818] scsi3 : sata_sil
[   27.123851] ata4: SATA link down (SStatus 0 SControl 310)
[   27.124052] PCI: Enabling device 0000:00:13.0 (0000 -> 0002)
[   27.124067] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 18
[   27.124086] ohci_hcd 0000:00:13.0: OHCI Host Controller
[   27.124457] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[   27.124484] ohci_hcd 0000:00:13.0: irq 18, io mem 0x40204000
[   27.184188] usb usb1: configuration #1 chosen from 1 choice
[   27.184402] hub 1-0:1.0: USB hub found
[   27.184419] hub 1-0:1.0: 4 ports detected
[   27.288028] PCI: Enabling device 0000:00:13.1 (0000 -> 0002)
[   27.288040] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 18
[   27.288064] ohci_hcd 0000:00:13.1: OHCI Host Controller
[   27.288193] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[   27.288213] ohci_hcd 0000:00:13.1: irq 18, io mem 0x40205000
[   27.347717] usb usb2: configuration #1 chosen from 1 choice
[   27.347936] hub 2-0:1.0: USB hub found
[   27.347954] hub 2-0:1.0: 4 ports detected
[   27.451625] ATIIXP: IDE controller at PCI slot 0000:00:14.1
[   27.451656] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 19
[   27.451669] ATIIXP: chipset revision 128
[   27.451671] ATIIXP: not 100% native mode: will probe irqs later
[   27.451682]     ide0: BM-DMA at 0x3000-0x3007, BIOS settings: hda:DMA, hdb:DMA
[   27.451701]     ide1: BM-DMA at 0x3008-0x300f, BIOS settings: hdc:DMA, hdd:pio
[   27.451713] Probing IDE interface ide0...
[   27.738442] hda: WDC WD800BB-00JHC0, ATA DISK drive
[   28.017598] hdb: WDC WD300BB-32AUA1, ATA DISK drive
[   28.074048] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   28.098174] Probing IDE interface ide1...
[   28.831164] hdc: TSSTcorp CDW/DVD TS-H492C, ATAPI CD/DVD-ROM drive
[   29.501026] ide1 at 0x170-0x177,0x376 on irq 15
[   29.518724] PCI: Enabling device 0000:00:13.2 (0000 -> 0002)
[   29.518735] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 18
[   29.518757] ehci_hcd 0000:00:13.2: EHCI Host Controller
[   29.518937] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[   29.519001] ehci_hcd 0000:00:13.2: irq 18, io mem 0x40206000
[   29.519014] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   29.519501] usb usb3: configuration #1 chosen from 1 choice
[   29.519703] hub 3-0:1.0: USB hub found
[   29.519717] hub 3-0:1.0: 8 ports detected
[   29.525642] hda: max request size: 128KiB
[   29.538509] hda: 156301488 sectors (80026 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(100)
[   29.539360] hda: cache flushes supported
[   29.539412]  hda: hda1 hda2 < hda5 >
[   29.575529] hdb: max request size: 128KiB
[   29.576509] hdb: 58633344 sectors (30020 MB) w/2048KiB Cache, CHS=58168/16/63, UDMA(100)
[   29.576516] hdb: cache flushes not supported
[   29.576549]  hdb: hdb1 hdb2 < hdb5 >
[   29.620473] hub 3-0:1.0: over-current change on port 5
[   29.620659] ACPI: PCI Interrupt 0000:02:02.0[A] -> GSI 21 (level, low) -> IRQ 21
[   29.620675] PCI: Setting latency timer of device 0000:02:02.0 to 64
[   29.621398] eth0: RealTek RTL8139 at 0xd8850000, 00:16:76:65:fb:a4, IRQ 21
[   29.621401] eth0:  Identified 8139 chip type 'RTL-8101'
[   29.623008] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   29.633787] hdc: ATAPI 52X DVD-ROM CD-R/RW drive, 1536kB Cache, UDMA(33)
[   29.633798] Uniform CD-ROM driver Revision: 3.20
[   29.908839] ehci_hcd 0000:00:13.2: port 5 reset error -110
[   29.908901] hub 3-0:1.0: hub_port_status failed (err = -32)
[   30.016617] Attempting manual resume
[   30.016621] swsusp: Resume From Partition 3:5
[   30.016623] PM: Checking swsusp image.
[   30.016836] PM: Resume from disk failed.
[   30.040433] kjournald starting.  Commit interval 5 seconds
[   30.040446] EXT3-fs: mounted filesystem with ordered data mode.
[   30.112222] ehci_hcd 0000:00:13.2: port 5 reset error -110
[   30.112231] hub 3-0:1.0: hub_port_status failed (err = -32)
[   30.315607] ehci_hcd 0000:00:13.2: port 5 reset error -110
[   30.315616] hub 3-0:1.0: hub_port_status failed (err = -32)
[   30.519111] ehci_hcd 0000:00:13.2: port 5 reset error -110
[   30.519121] hub 3-0:1.0: hub_port_status failed (err = -32)
[   30.722372] ehci_hcd 0000:00:13.2: port 5 reset error -110
[   30.722381] hub 3-0:1.0: hub_port_status failed (err = -32)
[   30.722383] hub 3-0:1.0: Cannot enable port 5.  Maybe the USB cable is bad?
[   30.778203] ehci_hcd 0000:00:13.2: port 5 reset error -110
[   30.778212] hub 3-0:1.0: hub_port_status failed (err = -32)
[   30.981592] ehci_hcd 0000:00:13.2: port 5 reset error -110
[   30.981601] hub 3-0:1.0: hub_port_status failed (err = -32)
[   31.184973] ehci_hcd 0000:00:13.2: port 5 reset error -110
[   31.184983] hub 3-0:1.0: hub_port_status failed (err = -32)
[   31.388363] ehci_hcd 0000:00:13.2: port 5 reset error -110
[   31.388370] hub 3-0:1.0: hub_port_status failed (err = -32)
[   31.591748] ehci_hcd 0000:00:13.2: port 5 reset error -110
[   31.591757] hub 3-0:1.0: hub_port_status failed (err = -32)
[   31.591759] hub 3-0:1.0: Cannot enable port 5.  Maybe the USB cable is bad?
[   31.647571] ehci_hcd 0000:00:13.2: port 5 reset error -110
[   31.647575] hub 3-0:1.0: hub_port_status failed (err = -32)
[   31.850962] ehci_hcd 0000:00:13.2: port 5 reset error -110
[   31.850970] hub 3-0:1.0: hub_port_status failed (err = -32)
[   32.054345] ehci_hcd 0000:00:13.2: port 5 reset error -110
[   32.054352] hub 3-0:1.0: hub_port_status failed (err = -32)
[   32.257730] ehci_hcd 0000:00:13.2: port 5 reset error -110
[   32.257736] hub 3-0:1.0: hub_port_status failed (err = -32)
[   32.461117] ehci_hcd 0000:00:13.2: port 5 reset error -110
[   32.461126] hub 3-0:1.0: hub_port_status failed (err = -32)
[   32.461128] hub 3-0:1.0: Cannot enable port 5.  Maybe the USB cable is bad?
[   32.516949] ehci_hcd 0000:00:13.2: port 5 reset error -110
[   32.516958] hub 3-0:1.0: hub_port_status failed (err = -32)
[   32.720328] ehci_hcd 0000:00:13.2: port 5 reset error -110
[   32.720338] hub 3-0:1.0: hub_port_status failed (err = -32)
[   32.923726] ehci_hcd 0000:00:13.2: port 5 reset error -110
[   32.923781] hub 3-0:1.0: hub_port_status failed (err = -32)
[   33.127113] ehci_hcd 0000:00:13.2: port 5 reset error -110
[   33.127166] hub 3-0:1.0: hub_port_status failed (err = -32)
[   33.330489] ehci_hcd 0000:00:13.2: port 5 reset error -110
[   33.330495] hub 3-0:1.0: hub_port_status failed (err = -32)
[   33.330497] hub 3-0:1.0: Cannot enable port 5.  Maybe the USB cable is bad?
[   33.513960] ehci_hcd 0000:00:13.2: port 6 reset error -110
[   33.514013] hub 3-0:1.0: hub_port_status failed (err = -32)
[   33.717408] ehci_hcd 0000:00:13.2: port 6 reset error -110
[   33.717431] hub 3-0:1.0: hub_port_status failed (err = -32)
[   33.920698] ehci_hcd 0000:00:13.2: port 6 reset error -110
[   33.920751] hub 3-0:1.0: hub_port_status failed (err = -32)
[   34.124084] ehci_hcd 0000:00:13.2: port 6 reset error -110
[   34.124089] hub 3-0:1.0: hub_port_status failed (err = -32)
[   34.327469] ehci_hcd 0000:00:13.2: port 6 reset error -110
[   34.327476] hub 3-0:1.0: hub_port_status failed (err = -32)
[   34.327478] hub 3-0:1.0: Cannot enable port 6.  Maybe the USB cable is bad?
[   34.383331] ehci_hcd 0000:00:13.2: port 6 reset error -110
[   34.383385] hub 3-0:1.0: hub_port_status failed (err = -32)
[   34.586695] ehci_hcd 0000:00:13.2: port 6 reset error -110
[   34.586722] hub 3-0:1.0: hub_port_status failed (err = -32)
[   34.790104] ehci_hcd 0000:00:13.2: port 6 reset error -110
[   34.790130] hub 3-0:1.0: hub_port_status failed (err = -32)
[   34.993497] ehci_hcd 0000:00:13.2: port 6 reset error -110
[   34.993549] hub 3-0:1.0: hub_port_status failed (err = -32)
[   35.196841] ehci_hcd 0000:00:13.2: port 6 reset error -110
[   35.196891] hub 3-0:1.0: hub_port_status failed (err = -32)
[   35.196894] hub 3-0:1.0: Cannot enable port 6.  Maybe the USB cable is bad?
[   35.252721] ehci_hcd 0000:00:13.2: port 6 reset error -110
[   35.252772] hub 3-0:1.0: hub_port_status failed (err = -32)
[   35.456064] ehci_hcd 0000:00:13.2: port 6 reset error -110
[   35.456073] hub 3-0:1.0: hub_port_status failed (err = -32)
[   35.659444] ehci_hcd 0000:00:13.2: port 6 reset error -110
[   35.659453] hub 3-0:1.0: hub_port_status failed (err = -32)
[   35.862839] ehci_hcd 0000:00:13.2: port 6 reset error -110
[   35.862849] hub 3-0:1.0: hub_port_status failed (err = -32)
[   36.066231] ehci_hcd 0000:00:13.2: port 6 reset error -110
[   36.066242] hub 3-0:1.0: hub_port_status failed (err = -32)
[   36.066245] hub 3-0:1.0: Cannot enable port 6.  Maybe the USB cable is bad?
[   36.122065] ehci_hcd 0000:00:13.2: port 6 reset error -110
[   36.122075] hub 3-0:1.0: hub_port_status failed (err = -32)
[   36.325443] ehci_hcd 0000:00:13.2: port 6 reset error -110
[   36.325468] hub 3-0:1.0: hub_port_status failed (err = -32)
[   36.528816] ehci_hcd 0000:00:13.2: port 6 reset error -110
[   36.528826] hub 3-0:1.0: hub_port_status failed (err = -32)
[   36.732208] ehci_hcd 0000:00:13.2: port 6 reset error -110
[   36.732233] hub 3-0:1.0: hub_port_status failed (err = -32)
[   36.935590] ehci_hcd 0000:00:13.2: port 6 reset error -110
[   36.935599] hub 3-0:1.0: hub_port_status failed (err = -32)
[   36.935602] hub 3-0:1.0: Cannot enable port 6.  Maybe the USB cable is bad?
[   36.935632] hub 3-0:1.0: over-current change on port 7
[   37.165490] hub 3-0:1.0: over-current change on port 8
[   37.326446] ehci_hcd 0000:00:13.2: port 8 reset error -110
[   37.326509] hub 3-0:1.0: hub_port_status failed (err = -32)
[   37.529801] ehci_hcd 0000:00:13.2: port 8 reset error -110
[   37.529811] hub 3-0:1.0: hub_port_status failed (err = -32)
[   37.733189] ehci_hcd 0000:00:13.2: port 8 reset error -110
[   37.733200] hub 3-0:1.0: hub_port_status failed (err = -32)
[   37.936561] ehci_hcd 0000:00:13.2: port 8 reset error -110
[   37.936571] hub 3-0:1.0: hub_port_status failed (err = -32)
[   38.139939] ehci_hcd 0000:00:13.2: port 8 reset error -110
[   38.139949] hub 3-0:1.0: hub_port_status failed (err = -32)
[   38.139952] hub 3-0:1.0: Cannot enable port 8.  Maybe the USB cable is bad?
[   38.195786] ehci_hcd 0000:00:13.2: port 8 reset error -110
[   38.195795] hub 3-0:1.0: hub_port_status failed (err = -32)
[   38.327250] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   38.399221] ehci_hcd 0000:00:13.2: port 8 reset error -110
[   38.399230] hub 3-0:1.0: hub_port_status failed (err = -32)
[   38.602590] ehci_hcd 0000:00:13.2: port 8 reset error -110
[   38.602599] hub 3-0:1.0: hub_port_status failed (err = -32)
[   38.805941] ehci_hcd 0000:00:13.2: port 8 reset error -110
[   38.805950] hub 3-0:1.0: hub_port_status failed (err = -32)
[   39.009336] ehci_hcd 0000:00:13.2: port 8 reset error -110
[   39.009345] hub 3-0:1.0: hub_port_status failed (err = -32)
[   39.009348] hub 3-0:1.0: Cannot enable port 8.  Maybe the USB cable is bad?
[   39.065163] ehci_hcd 0000:00:13.2: port 8 reset error -110
[   39.065172] hub 3-0:1.0: hub_port_status failed (err = -32)
[   39.268557] ehci_hcd 0000:00:13.2: port 8 reset error -110
[   39.268565] hub 3-0:1.0: hub_port_status failed (err = -32)
[   39.471923] ehci_hcd 0000:00:13.2: port 8 reset error -110
[   39.471932] hub 3-0:1.0: hub_port_status failed (err = -32)
[   39.675315] ehci_hcd 0000:00:13.2: port 8 reset error -110
[   39.675324] hub 3-0:1.0: hub_port_status failed (err = -32)
[   39.734555] NET: Registered protocol family 17
[   39.878688] ehci_hcd 0000:00:13.2: port 8 reset error -110
[   39.878697] hub 3-0:1.0: hub_port_status failed (err = -32)
[   39.878700] hub 3-0:1.0: Cannot enable port 8.  Maybe the USB cable is bad?
[   39.934516] ehci_hcd 0000:00:13.2: port 8 reset error -110
[   39.934525] hub 3-0:1.0: hub_port_status failed (err = -32)
[   40.118534] Linux agpgart interface v0.102 (c) Dave Jones
[   40.137908] ehci_hcd 0000:00:13.2: port 8 reset error -110
[   40.137918] hub 3-0:1.0: hub_port_status failed (err = -32)
[   40.147219] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
[   40.341282] ehci_hcd 0000:00:13.2: port 8 reset error -110
[   40.341291] hub 3-0:1.0: hub_port_status failed (err = -32)
[   40.418771] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   40.434693] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   40.478434] input: PC Speaker as /class/input/input2
[   40.544691] ehci_hcd 0000:00:13.2: port 8 reset error -110
[   40.544701] hub 3-0:1.0: hub_port_status failed (err = -32)
[   40.724004] parport: PnPBIOS parport detected.
[   40.724045] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[   40.748055] ehci_hcd 0000:00:13.2: port 8 reset error -110
[   40.748064] hub 3-0:1.0: hub_port_status failed (err = -32)
[   40.748067] hub 3-0:1.0: Cannot enable port 8.  Maybe the USB cable is bad?
[   40.924937] input: ImExPS/2 Generic Explorer Mouse as /class/input/input3
[   41.043919] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 19
[   41.237165] hda_codec: Unknown model for ALC861, trying auto-probe from BIOS...
[   41.451479] fuse init (API version 7.8)
[   41.636851] lp0: using parport0 (interrupt-driven).
[   41.668657] Adding 1116476k swap on /dev/disk/by-uuid/7f5fde64-2f28-45ac-8972-95a9f8a4f06d.  Priority:-1 extents:1 across:1116476k
[   41.781992] EXT3 FS on hda1, internal journal
[   41.914643] NET: Registered protocol family 10
[   41.914745] lo: Disabled Privacy Extensions
[   47.222781] Using specific hotkey driver
[   47.328585] input: Power Button (FF) as /class/input/input4
[   47.333340] ACPI: Power Button (FF) [PWRF]
[   47.363892] input: Power Button (CM) as /class/input/input5
[   47.368601] ACPI: Power Button (CM) [PWRB]
[   47.488297] No dock devices found.
[   47.504838] ibm_acpi: ec object not found
[   47.529548] pcc_acpi: loading...
[   51.805357] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   51.812847] [fglrx] Maximum main memory to use for locked dma buffers: 312 MBytes.
[   51.813388] [fglrx] module loaded - fglrx 8.34.8 [Feb 20 2007] on minor 0
[   51.901459] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 17 (level, low) -> IRQ 20
[   51.920666] ppdev: user-space parallel port driver
[   52.452530] [fglrx] total      GART = 130023424
[   52.452537] [fglrx] free       GART = 114032640
[   52.452540] [fglrx] max single GART = 114032640
[   52.452542] [fglrx] total      LFB  = 134217728
[   52.452543] [fglrx] free       LFB  = 122679296
[   52.452545] [fglrx] max single LFB  = 122679296
[   52.452547] [fglrx] total      Inv  = 0
[   52.452549] [fglrx] free       Inv  = 0
[   52.452550] [fglrx] max single Inv  = 0
[   52.452552] [fglrx] total      TIM  = 0
[   53.642058] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   53.642065] apm: overridden by ACPI.
[   56.766929] hda-intel: Invalid position buffer, using LPIB read method instead.
[   57.119030] Bluetooth: Core ver 2.11
[   57.119110] NET: Registered protocol family 31
[   57.119112] Bluetooth: HCI device and connection manager initialized
[   57.119116] Bluetooth: HCI socket layer initialized
[   57.186988] Bluetooth: L2CAP ver 2.8
[   57.186993] Bluetooth: L2CAP socket layer initialized
[   57.198306] ehci_hcd 0000:00:13.2: port 5 reset error -110
[   57.198404] hub 3-0:1.0: hub_port_status failed (err = -32)
[   57.401684] ehci_hcd 0000:00:13.2: port 5 reset error -110
[   57.401768] hub 3-0:1.0: hub_port_status failed (err = -32)
[   57.605082] ehci_hcd 0000:00:13.2: port 5 reset error -110
[   57.605092] hub 3-0:1.0: hub_port_status failed (err = -32)
[   57.808458] ehci_hcd 0000:00:13.2: port 5 reset error -110
[   57.808472] hub 3-0:1.0: hub_port_status failed (err = -32)
[   58.011837] ehci_hcd 0000:00:13.2: port 5 reset error -110
[   58.011847] hub 3-0:1.0: hub_port_status failed (err = -32)
[   58.011849] hub 3-0:1.0: Cannot enable port 5.  Maybe the USB cable is bad?
[   58.067670] ehci_hcd 0000:00:13.2: port 5 reset error -110
[   58.067678] hub 3-0:1.0: hub_port_status failed (err = -32)
[   58.271043] ehci_hcd 0000:00:13.2: port 5 reset error -110
[   58.271050] hub 3-0:1.0: hub_port_status failed (err = -32)
[   58.474433] ehci_hcd 0000:00:13.2: port 5 reset error -110
[   58.474440] hub 3-0:1.0: hub_port_status failed (err = -32)
[   58.677825] ehci_hcd 0000:00:13.2: port 5 reset error -110
[   58.677835] hub 3-0:1.0: hub_port_status failed (err = -32)
[   58.881205] ehci_hcd 0000:00:13.2: port 5 reset error -110
[   58.881216] hub 3-0:1.0: hub_port_status failed (err = -32)
[   58.881218] hub 3-0:1.0: Cannot enable port 5.  Maybe the USB cable is bad?
[   58.937027] ehci_hcd 0000:00:13.2: port 5 reset error -110
[   58.937033] hub 3-0:1.0: hub_port_status failed (err = -32)
[   59.140423] ehci_hcd 0000:00:13.2: port 5 reset error -110
[   59.140433] hub 3-0:1.0: hub_port_status failed (err = -32)
[   59.343808] ehci_hcd 0000:00:13.2: port 5 reset error -110
[   59.343816] hub 3-0:1.0: hub_port_status failed (err = -32)
[   59.547188] ehci_hcd 0000:00:13.2: port 5 reset error -110
[   59.547193] hub 3-0:1.0: hub_port_status failed (err = -32)
[   59.750588] ehci_hcd 0000:00:13.2: port 5 reset error -110
[   59.750613] hub 3-0:1.0: hub_port_status failed (err = -32)
[   59.750616] hub 3-0:1.0: Cannot enable port 5.  Maybe the USB cable is bad?
[   59.806410] ehci_hcd 0000:00:13.2: port 5 reset error -110
[   59.806419] hub 3-0:1.0: hub_port_status failed (err = -32)
[   60.009798] ehci_hcd 0000:00:13.2: port 5 reset error -110
[   60.009808] hub 3-0:1.0: hub_port_status failed (err = -32)
[   60.213176] ehci_hcd 0000:00:13.2: port 5 reset error -110
[   60.213184] hub 3-0:1.0: hub_port_status failed (err = -32)
[   60.416565] ehci_hcd 0000:00:13.2: port 5 reset error -110
[   60.416576] hub 3-0:1.0: hub_port_status failed (err = -32)
[   60.619955] ehci_hcd 0000:00:13.2: port 5 reset error -110
[   60.619964] hub 3-0:1.0: hub_port_status failed (err = -32)
[   60.619967] hub 3-0:1.0: Cannot enable port 5.  Maybe the USB cable is bad?
[   60.675772] ehci_hcd 0000:00:13.2: port 6 reset error -110
[   60.675778] hub 3-0:1.0: hub_port_status failed (err = -32)
[   60.879161] ehci_hcd 0000:00:13.2: port 6 reset error -110
[   60.879173] hub 3-0:1.0: hub_port_status failed (err = -32)
[   61.082556] ehci_hcd 0000:00:13.2: port 6 reset error -110
[   61.082566] hub 3-0:1.0: hub_port_status failed (err = -32)
[   61.285942] ehci_hcd 0000:00:13.2: port 6 reset error -110
[   61.285951] hub 3-0:1.0: hub_port_status failed (err = -32)
[   61.489324] ehci_hcd 0000:00:13.2: port 6 reset error -110
[   61.489338] hub 3-0:1.0: hub_port_status failed (err = -32)
[   61.489340] hub 3-0:1.0: Cannot enable port 6.  Maybe the USB cable is bad?
[   61.545151] ehci_hcd 0000:00:13.2: port 6 reset error -110
[   61.545160] hub 3-0:1.0: hub_port_status failed (err = -32)
[   61.748538] ehci_hcd 0000:00:13.2: port 6 reset error -110
[   61.748548] hub 3-0:1.0: hub_port_status failed (err = -32)
[   61.951923] ehci_hcd 0000:00:13.2: port 6 reset error -110
[   61.951933] hub 3-0:1.0: hub_port_status failed (err = -32)
[   62.155318] ehci_hcd 0000:00:13.2: port 6 reset error -110
[   62.155328] hub 3-0:1.0: hub_port_status failed (err = -32)
[   62.358687] ehci_hcd 0000:00:13.2: port 6 reset error -110
[   62.358696] hub 3-0:1.0: hub_port_status failed (err = -32)
[   62.358699] hub 3-0:1.0: Cannot enable port 6.  Maybe the USB cable is bad?
[   62.414514] ehci_hcd 0000:00:13.2: port 6 reset error -110
[   62.414521] hub 3-0:1.0: hub_port_status failed (err = -32)
[   62.617902] ehci_hcd 0000:00:13.2: port 6 reset error -110
[   62.617909] hub 3-0:1.0: hub_port_status failed (err = -32)
[   62.821296] ehci_hcd 0000:00:13.2: port 6 reset error -110
[   62.821306] hub 3-0:1.0: hub_port_status failed (err = -32)
[   63.024683] ehci_hcd 0000:00:13.2: port 6 reset error -110
[   63.024699] hub 3-0:1.0: hub_port_status failed (err = -32)
[   63.228063] ehci_hcd 0000:00:13.2: port 6 reset error -110
[   63.228079] hub 3-0:1.0: hub_port_status failed (err = -32)
[   63.228081] hub 3-0:1.0: Cannot enable port 6.  Maybe the USB cable is bad?
[   63.283895] ehci_hcd 0000:00:13.2: port 6 reset error -110
[   63.283908] hub 3-0:1.0: hub_port_status failed (err = -32)
[   63.487281] ehci_hcd 0000:00:13.2: port 6 reset error -110
[   63.487292] hub 3-0:1.0: hub_port_status failed (err = -32)
[   63.690679] ehci_hcd 0000:00:13.2: port 6 reset error -110
[   63.690689] hub 3-0:1.0: hub_port_status failed (err = -32)
[   63.894048] ehci_hcd 0000:00:13.2: port 6 reset error -110
[   63.894063] hub 3-0:1.0: hub_port_status failed (err = -32)
[   64.097436] ehci_hcd 0000:00:13.2: port 6 reset error -110
[   64.097445] hub 3-0:1.0: hub_port_status failed (err = -32)
[   64.097448] hub 3-0:1.0: Cannot enable port 6.  Maybe the USB cable is bad?
[   64.153263] ehci_hcd 0000:00:13.2: port 8 reset error -110
[   64.153272] hub 3-0:1.0: hub_port_status failed (err = -32)
[   64.356654] ehci_hcd 0000:00:13.2: port 8 reset error -110
[   64.356664] hub 3-0:1.0: hub_port_status failed (err = -32)
[   64.560033] ehci_hcd 0000:00:13.2: port 8 reset error -110
[   64.560041] hub 3-0:1.0: hub_port_status failed (err = -32)
[   64.763419] ehci_hcd 0000:00:13.2: port 8 reset error -110
[   64.763429] hub 3-0:1.0: hub_port_status failed (err = -32)
[   64.966825] ehci_hcd 0000:00:13.2: port 8 reset error -110
[   64.966836] hub 3-0:1.0: hub_port_status failed (err = -32)
[   64.966839] hub 3-0:1.0: Cannot enable port 8.  Maybe the USB cable is bad?
[   65.022634] ehci_hcd 0000:00:13.2: port 8 reset error -110
[   65.022644] hub 3-0:1.0: hub_port_status failed (err = -32)
[   65.226018] ehci_hcd 0000:00:13.2: port 8 reset error -110
[   65.226027] hub 3-0:1.0: hub_port_status failed (err = -32)
[   65.429426] ehci_hcd 0000:00:13.2: port 8 reset error -110
[   65.429436] hub 3-0:1.0: hub_port_status failed (err = -32)
[   65.632787] ehci_hcd 0000:00:13.2: port 8 reset error -110
[   65.632797] hub 3-0:1.0: hub_port_status failed (err = -32)
[   65.836180] ehci_hcd 0000:00:13.2: port 8 reset error -110
[   65.836198] hub 3-0:1.0: hub_port_status failed (err = -32)
[   65.836201] hub 3-0:1.0: Cannot enable port 8.  Maybe the USB cable is bad?
[   65.892008] ehci_hcd 0000:00:13.2: port 8 reset error -110
[   65.892024] hub 3-0:1.0: hub_port_status failed (err = -32)
[   65.894578] eth0: no IPv6 routers present
[   66.095387] ehci_hcd 0000:00:13.2: port 8 reset error -110
[   66.095395] hub 3-0:1.0: hub_port_status failed (err = -32)
[   66.298783] ehci_hcd 0000:00:13.2: port 8 reset error -110
[   66.298799] hub 3-0:1.0: hub_port_status failed (err = -32)
[   66.502162] ehci_hcd 0000:00:13.2: port 8 reset error -110
[   66.502172] hub 3-0:1.0: hub_port_status failed (err = -32)
[   66.705546] ehci_hcd 0000:00:13.2: port 8 reset error -110
[   66.705556] hub 3-0:1.0: hub_port_status failed (err = -32)
[   66.705559] hub 3-0:1.0: Cannot enable port 8.  Maybe the USB cable is bad?
[   66.761368] ehci_hcd 0000:00:13.2: port 8 reset error -110
[   66.761377] hub 3-0:1.0: hub_port_status failed (err = -32)
[   66.964754] ehci_hcd 0000:00:13.2: port 8 reset error -110
[   66.964760] hub 3-0:1.0: hub_port_status failed (err = -32)
[   67.168149] ehci_hcd 0000:00:13.2: port 8 reset error -110
[   67.168159] hub 3-0:1.0: hub_port_status failed (err = -32)
[   67.371522] ehci_hcd 0000:00:13.2: port 8 reset error -110
[   67.371530] hub 3-0:1.0: hub_port_status failed (err = -32)
[   67.574918] ehci_hcd 0000:00:13.2: port 8 reset error -110
[   67.574940] hub 3-0:1.0: hub_port_status failed (err = -32)
[   67.574943] hub 3-0:1.0: Cannot enable port 8.  Maybe the USB cable is bad?
[   67.839766] Bluetooth: RFCOMM socket layer initialized
[   67.839784] Bluetooth: RFCOMM TTY layer initialized
[   67.839786] Bluetooth: RFCOMM ver 1.8
[ 4235.376140] usb 3-2: new high speed USB device using ehci_hcd and address 26
[53944.135871] cdrom: hdc: mrw address space DMA selected
[53944.255959] cdrom: hdc: mrw address space DMA selected
[53944.324418] ISO 9660 Extensions: Microsoft Joliet Level 3
[53944.390237] ISO 9660 Extensions: RRIP_1991A
[109931.823739] eth0: link down
[109937.963387] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[109937.963566] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[109954.815544] eth0: no IPv6 routers present
[215652.474420] cdrom: hdc: mrw address space DMA selected
[215652.538909] cdrom: hdc: mrw address space DMA selected
[/HTML]

That's dmesg output, according to that maybe the cable is bad? lol I'll have lsusb -v output next, for some reason that command is just sitting there with no response.

---

### Post by geraldm on 2007-07-16
[   29.620473] hub 3-0:1.0: over-current change on port 5

You have device(s) that are demanding too much
power from the port.  Unplug every device that can be unplugged, then try
replugging just one USB 2.0 device and see if that works OK.  
If successful, you may then replug other devices, being careful not to 
exceed the port limits current.  That is usually 100mA, unless it is a powered
port, which usually are 500mA.  There is chance that the cable is bad.
The power management software for USB is not yet available as far as I know,
so the fallback is to the hardware, which is expected to shutdown the port(s).

Also the lsusb command in 6.06 LTS (possibly others) does not work.  It just hangs
on the app.  You need get lsusb, as that shows the power usage data.  It should be
in a usbutils package. I have not checked if there is an upgrade for lsusb, as I usually
compile from source. 

Gerald

---

### Post by ndogg1982 on 2007-07-16
Thanks for the suggestion gerald, but I have just the one 2.0 port, nothing else plugged in. Could it possibly be the connectors on the actual port itself shorting out and causing it to switch itself off? Maybe some kind of dust or moisture? I did check the cables and wires on the mobo, everything is plugged in securely no loose wires. I noticed just now that in order for my usb flash drive to get power from the port I have to pull it out a little ways, so now I'm thinking it's maybe a problem with the pins inside the port. I really don't know at this point.

---

### Post by mytwobears on 2007-07-17
> **fdrake said:**
> that's weird, all in 1 day. can u post here the output  of this commands on the terminal :

dmesg


lsusb -v

and make sure u plugin something


OMG!  Thank you so much!  I just killed my usb port and I came here looking for help and I saw this thread and went ahead and looked at my dmesg output and then I typed the second command and the drive I had plugged into the port came to life again. 

Gawd, thanks so much, it had like 40GB of music on there :popcorn:.  I love this forum and the helpful people on it :guitar:.

---

