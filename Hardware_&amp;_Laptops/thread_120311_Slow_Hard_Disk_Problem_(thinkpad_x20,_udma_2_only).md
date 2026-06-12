---
title: "Slow Hard Disk Problem (thinkpad x20, udma 2 only)"
date: 2006-01-21
forum: Hardware &amp; Laptops
---

### Post by oceanhippie on 2006-01-21
I've got a bit of a problem, after many hours of trolling the net i still can't get my ATA hard drive up to speed.

PROBLEM (I think)

hdparm reports that I have udma modes available. But setting higher than udma mode 2 produces 

 ide0: Speed warnings UDMA 3/4/5 is not functional.

in dmesg.

The on board system is intel piix4, I think this is the problem. The other thing that might be a problem is that the 12c smbus module

dmesg says 

piix4_smbus 0000:00:07.3: IBM Laptop detected; this module may corrupt your serial eeprom! Refusing to load module!

Apparently this is not just a warning and can trash your main board!

I've tried a  idebus=66 and ide0=ata66 and ide66 on boot.

I admit to not knowing too much about linux hardware? pii4x driver si handling the drive, heres the drive info:

 Model=IBM-DJSA-220, FwRev=JS4IAC1A, SerialNo=44V44N41552
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs }
 RawCHS=16383/15/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=DualPortCache, BuffSize=1874kB, MaxMultSect=16, MultSect=16
 CurCHS=16383/15/63, CurSects=15481935, LBA=yes, LBAsects=39070080
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 *udma2 udma3 udma4
 AdvancedPM=yes: mode=0x9F (159) WriteCache=enabled
 Drive conforms to: ATA/ATAPI-5 T13 1321D revision 1:

 * signifies the current active mode

Can anyone shed any light? - Will write up and publish a full answer if I find one!

Tom

full dmesg output:
tom@rodent:~$ sudo hdparm -X68 /dev/hda
Password:

/dev/hda:
 setting xfermode to 68 (UltraDMA mode4)
tom@rodent:~$ dmesg
(order: 11, 32768 bytes)
[4294667.296000] Detected 597.619 MHz processor.
[4294667.296000] Using pmtmr for high-res timesource
[4294667.296000] Console: colour dummy device 80x25
[4294669.249000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[4294669.251000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[4294669.293000] Memory: 315660k/327616k available (1622k kernel code, 11276k reserved, 731k data, 168k init, 0k highmem)
[4294669.293000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[4294669.293000] Calibrating delay loop... 1183.74 BogoMIPS (lpj=591872)
[4294669.317000] Security Framework v1.0.0 initialized
[4294669.317000] SELinux:  Disabled at boot.
[4294669.317000] Mount-cache hash table entries: 512
[4294669.317000] CPU: After generic identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[4294669.317000] CPU: After vendor identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[4294669.317000] CPU: L1 I cache: 16K, L1 D cache: 16K
[4294669.317000] CPU: L2 cache: 256K
[4294669.317000] CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 00000000 00000000 00000000
[4294669.317000] Intel machine check architecture supported.
[4294669.317000] Intel machine check reporting enabled on CPU#0.
[4294669.317000] CPU: Intel Pentium III (Coppermine) stepping 03
[4294669.317000] Enabling fast FPU save and restore... done.
[4294669.317000] Enabling unmasked SIMD FPU exception support... done.
[4294669.317000] Checking 'hlt' instruction... OK.
[4294669.321000] checking if image is initramfs... it is
[4294670.803000] Freeing initrd memory: 5505k freed
[4294670.805000] ACPI: Looking for DSDT in initrd... not found!
[4294671.036000]  not found!
[4294671.108000] ACPI: setting ELCR to 0200 (from 0800)
[4294671.288000] NET: Registered protocol family 16
[4294671.288000] ACPI: bus type pci registered
[4294671.288000] PCI: PCI BIOS revision 2.10 entry at 0xfd94f, last bus=7
[4294671.288000] PCI: Using configuration type 1
[4294671.288000] mtrr: v2.0 (20020519)
[4294671.289000] ACPI: Subsystem revision 20050729
[4294671.514000] ACPI: Interpreter enabled
[4294671.514000] ACPI: Using PIC for interrupt routing
[4294671.516000] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 *11)
[4294671.518000] ACPI: PCI Interrupt Link [LNKB] (IRQs 9 *11)
[4294671.520000] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 *11)
[4294671.522000] ACPI: PCI Interrupt Link [LNKD] (IRQs 9 *11)
[4294671.523000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[4294671.523000] PCI: Probing PCI hardware (bus 00)
[4294671.525000] ACPI: Assume root bridge [\_SB_.PCI0] segment is 0
[4294671.525000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[4294671.530000] Boot video device is 0000:01:00.0
[4294671.547000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[4294671.549000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[4294671.551000] ACPI: Power Resource [PSIO] (on)
[4294671.552000] ACPI: Power Resource [PSER] (on)
[4294671.553000] burst-mode-ec-10-Aug
[4294671.553000] ACPI: Embedded Controller [EC] (gpe 9)
[4294671.558000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294671.558000] pnp: PnP ACPI init
[4294671.568000] pnp: PnP ACPI: found 13 devices
[4294671.568000] PnPBIOS: Disabled by ACPI PNP
[4294671.568000] PCI: Using ACPI for IRQ routing
[4294671.568000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[4294671.576000] pnp: 00:01: ioport range 0x1000-0x103f could not be reserved
[4294671.576000] pnp: 00:01: ioport range 0x1040-0x104f has been reserved
[4294671.576000] pnp: 00:01: ioport range 0xfe00-0xfe0f has been reserved
[4294671.577000] Simple Boot Flag at 0x35 set to 0x1
[4294671.577000] audit: initializing netlink socket (disabled)
[4294671.577000] audit: initialized
[4294671.578000] VFS: Disk quotas dquot_6.5.1
[4294671.578000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294671.578000] devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
[4294671.578000] devfs: boot_options: 0x0
[4294671.578000] Initializing Cryptographic API
[4294671.578000] Limiting direct PCI/PCI transfers.
[4294671.578000] isapnp: Scanning for PnP cards...
[4294671.932000] isapnp: No Plug & Play device found
[4294671.980000] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[4294671.981000] serio: i8042 AUX port at 0x60,0x64 irq 12
[4294671.981000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294671.981000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[4294671.981000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294671.987000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294671.987000] io scheduler noop registered
[4294671.987000] io scheduler anticipatory registered
[4294671.987000] io scheduler deadline registered
[4294671.987000] io scheduler cfq registered
[4294671.988000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294671.989000] NET: Registered protocol family 2
[4294671.995000] input: AT Translated Set 2 keyboard on isa0060/serio0
[4294671.998000] IP: routing cache hash table of 2048 buckets, 16Kbytes
[4294671.998000] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[4294671.999000] TCP bind hash table entries: 16384 (order: 4, 65536 bytes)
[4294671.999000] TCP: Hash tables configured (established 16384 bind 16384)
[4294671.999000] NET: Registered protocol family 8
[4294671.999000] NET: Registered protocol family 20
[4294672.000000] ACPI wakeup devices:
[4294672.000000]  LID SLPB PCI0  USB UART
[4294672.000000] ACPI: (supports S0 S1 S3 S4 S5)
[4294672.000000] Freeing unused kernel memory: 168k freed
[4294672.229000] request_module: runaway loop modprobe net-pf-1
[4294673.154000] Capability LSM initialized
[4294673.167000] vesafb: framebuffer at 0xf5000000, mapped to 0xd4880000, using 1536k, total 4096k
[4294673.167000] vesafb: mode is 1024x768x8, linelength=1024, pages=4
[4294673.167000] vesafb: protected mode interface info at c000:57aa
[4294673.167000] vesafb: scrolling: redraw
[4294673.167000] vesafb: Pseudocolor: size=6:6:6:6, shift=0:0:0:0
[4294673.183000] Console: switching to colour frame buffer device 128x48
[4294673.183000] fb0: VESA VGA frame buffer device
[4294673.204000] NET: Registered protocol family 1
[4294673.243000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294673.243000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294673.243000] ACPI: bus type ide registered
[4294673.264000] PIIX4: IDE controller at PCI slot 0000:00:07.1
[4294673.264000] PIIX4: chipset revision 1
[4294673.264000] PIIX4: not 100% native mode: will probe irqs later
[4294673.264000]     ide0: BM-DMA at 0x1800-0x1807, BIOS settings: hda:DMA, hdb:pio
[4294673.264000]     ide1: BM-DMA at 0x1808-0x180f, BIOS settings: hdc:pio, hdd:pio
[4294673.264000] Probing IDE interface ide0...
[4294673.528000] hda: IBM-DJSA-220, ATA DISK drive
[4294674.144000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294674.144000] Probing IDE interface ide1...
[4294674.663000] Probing IDE interface ide1...
[4294675.182000] Probing IDE interface ide2...
[4294675.695000] Probing IDE interface ide3...
[4294676.208000] Probing IDE interface ide4...
[4294676.721000] Probing IDE interface ide5...
[4294677.246000] hda: max request size: 128KiB
[4294677.287000] hda: 39070080 sectors (20003 MB) w/1874KiB Cache, CHS=41344/15/63, UDMA(33)
[4294677.287000] hda: cache flushes not supported
[4294677.287000]  /dev/ide/host0/bus0/target0/lun0: p1 p2 p3 p4
[4294677.897000] Attempting manual resume
[4294677.909000] swsusp: Suspend partition has wrong signature?
[4294678.036000] usbcore: registered new driver usbfs
[4294678.036000] usbcore: registered new driver hub
[4294678.040000] USB Universal Host Controller Interface driver v2.2
[4294678.042000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[4294678.042000] PCI: setting IRQ 11 as level-triggered
[4294678.042000] ACPI: PCI Interrupt 0000:00:07.2[D] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[4294678.042000] uhci_hcd 0000:00:07.2: Intel Corporation 82371AB/EB/MB PIIX4 USB
[4294678.104000] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
[4294678.104000] uhci_hcd 0000:00:07.2: irq 11, io base 0x00001820
[4294678.104000] hub 1-0:1.0: USB hub found
[4294678.104000] hub 1-0:1.0: 2 ports detected
[4294678.205000] PCI: Enabling device 0000:00:0a.0 (0000 -> 0003)
[4294678.207000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[4294678.207000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[4294678.207000] 3c59x: Donald Becker and others. [www.scyld.com/network/vortex.html](www.scyld.com/network/vortex.html)
[4294678.207000] 0000:00:0a.0: 3Com PCI 3c556B Laptop Hurricane at 0x2000. Vers LK1.1.19
[4294678.207000] PCI: Setting latency timer of device 0000:00:0a.0 to 64
[4294678.320000] *** EEPROM MAC address is invalid.
[4294678.320000] 3c59x: vortex_probe1 fails.  Returns -22
[4294678.321000] ACPI: PCI interrupt for device 0000:00:0a.0 disabled
[4294678.321000] 3c59x: probe of 0000:00:0a.0 failed with error -22
[4294681.021000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[4294681.021000] ACPI: Processor [CPU] (supports 8 throttling states)
[4294681.027000] ACPI: Thermal Zone [THM0] (47 C)
[4294681.214000] Attempting manual resume
[4294681.214000] swsusp: Suspend partition has wrong signature?
[4294681.235000] ReiserFS: hda2: found reiserfs format "3.6" with standard journal
[4294681.494000] ReiserFS: hda2: using ordered data mode
[4294681.510000] ReiserFS: hda2: journal params: device hda2, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[4294681.517000] ReiserFS: hda2: checking transaction log (hda2)
[4294681.578000] ReiserFS: hda2: Using r5 hash to sort names
[4294683.949000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294689.477000] Adding 385552k swap on /dev/hda4.  Priority:-1 extents:1
[4294710.357000] piix4_smbus 0000:00:07.3: Found 0000:00:07.3 device
[4294710.357000] piix4_smbus 0000:00:07.3: IBM Laptop detected; this module may corrupt your serial eeprom! Refusing to load module!
[4294710.358000] piix4_smbus: probe of 0000:00:07.3 failed with error -1
[4294710.688000] mice: PS/2 mouse device common for all mice
[4294710.845000] parport: PnPBIOS parport detected.
[4294710.845000] parport0: PC-style at 0x3bc (0x7bc), irq 7, dma 0 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[4294710.966000] lp0: using parport0 (interrupt-driven).
[4294711.144000] input: PS/2 Generic Mouse on isa0060/serio1
[4294711.870000] ts: Compaq touchscreen protocol output
[4294715.575000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[4294718.629000] ReiserFS: hda3: found reiserfs format "3.6" with standard journal
[4294718.629000] ReiserFS: hda3: using ordered data mode
[4294718.641000] ReiserFS: hda3: journal params: device hda3, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[4294718.648000] ReiserFS: hda3: checking transaction log (hda3)
[4294718.664000] ReiserFS: hda3: Using r5 hash to sort names
[4294720.332000] Linux agpgart interface v0.101 (c) Dave Jones
[4294720.362000] agpgart: Detected an Intel 440BX Chipset.
[4294720.419000] agpgart: AGP aperture is 64M @ 0xf8000000
[4294720.675000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294720.695000] shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
[4294720.695000] shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
[4294721.522000] Linux Kernel Card Services
[4294721.522000]   options:  [pci] [cardbus] [pm]
[4294721.569000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[4294721.569000] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[4294721.569000] Yenta: CardBus bridge found at 0000:00:08.0 [1014:0185]
[4294721.689000] Yenta: ISA IRQ mask 0x0438, PCI irq 11
[4294721.689000] Socket status: 30000410
[4294721.739000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[4294721.739000] ACPI: PCI Interrupt 0000:00:08.1[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[4294721.739000] Yenta: CardBus bridge found at 0000:00:08.1 [1014:0185]
[4294721.859000] Yenta: ISA IRQ mask 0x0438, PCI irq 11
[4294721.859000] Socket status: 30000006
[4294723.311000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[4294723.864000] gameport: CS4281 Gameport is pci0000:00:0b.0/gameport0, speed 2386kHz
[4294726.222000] input: PC Speaker
[4294726.556000] Real Time Clock Driver v1.12
[4294727.032000] Floppy drive(s): fd0 is 1.44M
[4294727.046000] FDC 0 is a National Semiconductor PC87306
[4294731.593000] NET: Registered protocol family 17
[4294735.856000] ACPI: AC Adapter [AC] (on-line)
[4294736.112000] ACPI: Power Button (FF) [PWRF]
[4294736.112000] ACPI: Lid Switch [LID]
[4294736.112000] ACPI: Sleep Button (CM) [SLPB]
[4294736.297000] ibm_acpi: IBM ThinkPad ACPI Extras v0.8
[4294736.297000] ibm_acpi: [http://ibm-acpi.sf.net/](http://ibm-acpi.sf.net/)
[4294736.297000] ibm_acpi: dock device not present
[4294736.298000] ibm_acpi: bay device not present
[4294736.385000] ACPI: Battery Slot [BAT0] (battery present)
[4294736.439000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[4294741.497000] cs: IO port probe 0x100-0x4ff: excluding 0x170-0x177 0x370-0x377 0x4d0-0x4d7
[4294741.498000] cs: IO port probe 0x100-0x4ff: excluding 0x170-0x177 0x370-0x377 0x4d0-0x4d7
[4294741.500000] cs: IO port probe 0xc00-0xcf7: clean.
[4294741.501000] cs: IO port probe 0xc00-0xcf7: clean.
[4294741.502000] cs: IO port probe 0xa00-0xaff: clean.
[4294741.502000] cs: IO port probe 0xa00-0xaff: clean.
[4294741.504000] cs: memory probe 0xa0000000-0xa0ffffff: clean.
[4294741.725000] orinoco 0.14alpha2 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[4294741.747000] orinoco_cs 0.14alpha2 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[4294741.857000] eth0: Hardware identity 0001:0001:0004:0000
[4294741.857000] eth0: Station identity  001f:0001:0008:0048
[4294741.857000] eth0: Firmware determined as Lucent/Agere 8.72
[4294741.857000] eth0: Ad-hoc demo mode supported
[4294741.857000] eth0: IEEE standard IBSS ad-hoc mode supported
[4294741.857000] eth0: WEP supported, 104-bit key
[4294741.857000] eth0: MAC address 00:02:2D:09:63:E6
[4294741.857000] eth0: Station name "HERMES I"
[4294741.857000] eth0: ready
[4294741.866000] eth0: index 0x01: Vcc 5.0, irq 3, io 0x0100-0x013f
[4294742.461000] eth0: New link status: Connected (0001)
[4294753.658000] IBM machine detected. Enabling interrupts during APM calls.
[4294753.658000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[4294753.658000] apm: overridden by ACPI.
[4294756.780000] Bluetooth: Core ver 2.7
[4294756.780000] NET: Registered protocol family 31
[4294756.780000] Bluetooth: HCI device and connection manager initialized
[4294756.780000] Bluetooth: HCI socket layer initialized
[4294756.856000] Bluetooth: L2CAP ver 2.7
[4294756.856000] Bluetooth: L2CAP socket layer initialized
[4294756.930000] Bluetooth: RFCOMM ver 1.5
[4294756.930000] Bluetooth: RFCOMM socket layer initialized
[4294756.930000] Bluetooth: RFCOMM TTY layer initialized
[4294759.359000] Non-volatile memory driver v1.2
[4294766.833000] NET: Registered protocol family 10
[4294766.833000] Disabled Privacy Extensions on device c031eb40(lo)
[4294766.834000] IPv6 over IPv4 tunneling driver
[4294777.803000] eth0: no IPv6 routers present
[4294874.041000] ide0: Speed warnings UDMA 3/4/5 is not functional.

---

### Post by John Dooley on 2006-01-23
I don't have the full answer but I can supply the best source of information that I have found and a guess. I'm running a ThinkPad A21M and I recently speeded up the harddrive to with sudo hdparm -c3 -X66 /dev/hda. The sudo hdparm -i /dev/hda listed udma up to 4 but udma2 had the asterix.

According to Christopher Negus's Linux Troubleshooting Bible, udma is 33.3 MB per second. udma3 is 44.4 and udma4 is 66.7. I guess these are the IDE bus speeds of some function of them.    

My guess:

Since my ThinkPad runs at 700MHZ and yours at 600MZ, the higher modes available to the harddrive may not be supported for this slow laptop mother boards.

My sudo hdparm -I /dev/hda gives the harddrive a capability which ranges up to udma4 but the kernel may decide that udma 2 is all that can be supported my he motherboard.

This might be tested by sticking the harddrive in a faster laptop, say, running at 1.4 GHZ - then udma4 might be used.

 I really don't know for sure and haven't found a good source of this type if information, yet.

---

### Post by oceanhippie on 2006-01-29
Thanks, pretty sure that the baord can do it. Its fine in windows. Sounds clunky. I've had a IBM 20g from and older PC in linux box doing fine. Just the thinkpad. Pretty sure its the motherboard not the Disk, or mor to the point the drivers. for the Chipset.

Oh well Steam power it is.

Tom

---

### Post by Haim on 2006-09-14
Seems to be a new firmware release for t20 at the lenovo site.  Not sure if really any change for the t20 or for other models as release notes dont' say much, but still might be worth a try.  

I've got a t20 as well, but eeprom corruption problem on my network card :(  So if you hear anything about that give me a bell!!

---

