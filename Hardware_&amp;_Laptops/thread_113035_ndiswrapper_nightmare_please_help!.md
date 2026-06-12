---
title: "ndiswrapper nightmare please help!"
date: 2006-01-05
forum: Hardware &amp; Laptops
---

### Post by zahidism on 2006-01-05
following a guide i did make distclean, then in the directory i unpacked ndiswrapper i did make and i got error code 1 and 2 (highlighted in bold)

> root@ubuntu:/usr/src/ndiswrapper-1.7# make distclean
make -C driver clean
make[1]: Entering directory `/usr/src/ndiswrapper-1.7/driver'
rm -rf ndiswrapper.ko ndiswrapper.o hal.o iw_ndis.o loader.o misc_funcs.o ndis.o ntoskernel.o ntoskernel_io.o pe_linker.o pnp.o proc.o wrapndis.o wrapper.o divdi3.o usb.o x86_64_stubs.o \
   divdi3.o .*.ko.cmd .*.o.cmd ndiswrapper.mod.[oc] *~ .tmp_versions
make[1]: Leaving directory `/usr/src/ndiswrapper-1.7/driver'
make -C utils clean
make[1]: Entering directory `/usr/src/ndiswrapper-1.7/utils'
rm -f *~ *.o loadndisdriver
make[1]: Leaving directory `/usr/src/ndiswrapper-1.7/utils'
rm -f *~
rm -fr ndiswrapper-1.7 ndiswrapper-1.7.tar.gz *.deb patch-stamp
make -C driver distclean
make[1]: Entering directory `/usr/src/ndiswrapper-1.7/driver'
rm -rf ndiswrapper.ko ndiswrapper.o hal.o iw_ndis.o loader.o misc_funcs.o ndis.o ntoskernel.o ntoskernel_io.o pe_linker.o pnp.o proc.o wrapndis.o wrapper.o divdi3.o usb.o x86_64_stubs.o \
   divdi3.o .*.ko.cmd .*.o.cmd ndiswrapper.mod.[oc] *~ .tmp_versions
rm -f *_exports.h .\#* x86_64_stubs.h
make[1]: Leaving directory `/usr/src/ndiswrapper-1.7/driver'
make -C utils distclean
make[1]: Entering directory `/usr/src/ndiswrapper-1.7/utils'
rm -f *~ *.o loadndisdriver
rm -f .\#*
make[1]: Leaving directory `/usr/src/ndiswrapper-1.7/utils'
rm -f .\#*
**root@ubuntu:/usr/src/ndiswrapper-1.7# make**
make -C driver
make[1]: Entering directory `/usr/src/ndiswrapper-1.7/driver'
[B]Can't find kernel sources in /lib/modules/2.6.12-9-386/build;
  give the path to kernel sources with KSRC=<path> argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/usr/src/ndiswrapper-1.7/driver'
make: *** [all] Error 2[/B]
root@ubuntu:/usr/src/ndiswrapper-1.7# make install
make -C driver install
make[1]: Entering directory `/usr/src/ndiswrapper-1.7/driver'
Can't find kernel sources in /lib/modules/2.6.12-9-386/build;
  give the path to kernel sources with KSRC=<path> argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/usr/src/ndiswrapper-1.7/driver'
make: *** [install] Error 2
root@ubuntu:/usr/src/ndiswrapper-1.7# ndiswrapper
bash: ndiswrapper: command not found
root@ubuntu:/usr/src/ndiswrapper-1.7# ndiswrapper -i
bash: ndiswrapper: command not found
root@ubuntu:/usr/src/ndiswrapper-1.7# ndis
bash: ndis: command not found
root@ubuntu:/usr/src/ndiswrapper-1.7#

pleeeaaase help this newb who really wants to enjoy ubuntu wirelessly :)

---

### Post by Zelut on 2006-01-05
sounds like you might be doing things the hard way.  I've got wireless working on many a laptop and I never compiled from source.

try 'sudo apt-get install ndiswrapper-utils'
then: 'dmesg' post the output as per your wireless card.

I'll get you working :)

---

### Post by zahidism on 2006-01-05
72.116000] Freeing initrd memory: 4821k freed
[4294672.124000] ACPI: Looking for DSDT in initrd... not found!
[4294672.250000]  not found!
[4294672.268000] ACPI: setting ELCR to 0200 (from 0800)
[4294672.271000] NET: Registered protocol family 16
[4294672.271000] EISA bus registered
[4294672.271000] ACPI: bus type pci registered
[4294672.288000] PCI: PCI BIOS revision 2.10 entry at 0xfc96e, last bus=2
[4294672.288000] PCI: Using configuration type 1
[4294672.288000] mtrr: v2.0 (20020519)
[4294672.289000] ACPI: Subsystem revision 20050729
[4294672.318000] ACPI: Interpreter enabled
[4294672.318000] ACPI: Using PIC for interrupt routing
[4294672.320000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[4294672.320000] PCI: Probing PCI hardware (bus 00)
[4294672.321000] ACPI: Assume root bridge [\_SB_.PCI0] segment is 0
[4294672.321000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[4294672.348000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[4294672.348000] Boot video device is 0000:01:00.0
[4294672.348000] PCI: Transparent bridge - 0000:00:1e.0
[4294672.383000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[4294672.405000] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
[4294672.405000] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *11
[4294672.406000] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 *11)
[4294672.407000] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 *11)
[4294672.407000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[4294672.408000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[4294672.410000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[4294672.412000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[4294672.414000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294672.414000] pnp: PnP ACPI init
[4294672.473000] pnp: PnP ACPI: found 12 devices
[4294672.473000] PnPBIOS: Disabled by ACPI PNP
[4294672.473000] PCI: Using ACPI for IRQ routing
[4294672.473000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[4294672.495000] pnp: 00:01: ioport range 0x4d0-0x4d1 has been reserved
[4294672.495000] pnp: 00:01: ioport range 0x800-0x805 could not be reserved
[4294672.495000] pnp: 00:01: ioport range 0x808-0x80f could not be reserved
[4294672.495000] pnp: 00:02: ioport range 0xf400-0xf4fe has been reserved
[4294672.495000] pnp: 00:02: ioport range 0x806-0x807 has been reserved
[4294672.495000] pnp: 00:02: ioport range 0x810-0x85f could not be reserved
[4294672.495000] pnp: 00:02: ioport range 0x860-0x87f has been reserved
[4294672.495000] pnp: 00:02: ioport range 0x880-0x8bf has been reserved
[4294672.495000] pnp: 00:02: ioport range 0x8c0-0x8df has been reserved
[4294672.495000] pnp: 00:07: ioport range 0x900-0x97f has been reserved
[4294672.496000] audit: initializing netlink socket (disabled)
[4294672.496000] audit: initialized
[4294672.496000] highmem bounce pool size: 64 pages
[4294672.496000] VFS: Disk quotas dquot_6.5.1
[4294672.496000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294672.496000] devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
[4294672.496000] devfs: boot_options: 0x0
[4294672.496000] Initializing Cryptographic API
[4294672.496000] isapnp: Scanning for PnP cards...
[4294672.847000] isapnp: No Plug & Play device found
[4294672.885000] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[4294672.888000] serio: i8042 AUX port at 0x60,0x64 irq 12
[4294672.889000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294672.889000] Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
[4294672.889000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294672.893000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294672.894000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 5
[4294672.894000] PCI: setting IRQ 5 as level-triggered
[4294672.894000] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
[4294672.894000] ACPI: PCI interrupt for device 0000:00:1f.6 disabled
[4294672.894000] io scheduler noop registered
[4294672.894000] io scheduler anticipatory registered
[4294672.894000] io scheduler deadline registered
[4294672.894000] io scheduler cfq registered
[4294672.895000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294672.895000] EISA: Probing bus 0 at eisa.0
[4294672.895000] EISA: Detected 0 cards.
[4294672.895000] NET: Registered protocol family 2
[4294672.905000] IP: routing cache hash table of 8192 buckets, 64Kbytes
[4294672.905000] TCP established hash table entries: 262144 (order: 9, 2097152 bytes)
[4294672.908000] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[4294672.908000] TCP: Hash tables configured (established 262144 bind 65536)
[4294672.909000] NET: Registered protocol family 8
[4294672.909000] NET: Registered protocol family 20
[4294672.909000] ACPI wakeup devices:
[4294672.909000]  LID PBTN PCI0 USB0 USB1 USB2 USB3 MODM PCIE
[4294672.909000] ACPI: (supports S0 S1 S3 S4 S4bios S5)
[4294672.909000] Freeing unused kernel memory: 224k freed
[4294672.928000] input: AT Translated Set 2 keyboard on isa0060/serio0
[4294672.940000] vga16fb: initializing
[4294672.940000] vga16fb: mapped to 0xc00a0000
[4294673.062000] Console: switching to colour frame buffer device 80x30
[4294673.062000] fb0: VGA16 VGA frame buffer device
[4294674.275000] Capability LSM initialized
[4294674.299000] NET: Registered protocol family 1
[4294674.330000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294674.330000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294674.330000] ACPI: bus type ide registered
[4294674.342000] ICH4: IDE controller at PCI slot 0000:00:1f.1
[4294674.342000] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[4294674.342000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[4294674.342000] PCI: setting IRQ 11 as level-triggered
[4294674.342000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[4294674.342000] ICH4: chipset revision 1
[4294674.342000] ICH4: not 100% native mode: will probe irqs later
[4294674.343000]     ide0: BM-DMA at 0xbfa0-0xbfa7, BIOS settings: hda:DMA, hdb:pio
[4294674.343000]     ide1: BM-DMA at 0xbfa8-0xbfaf, BIOS settings: hdc:DMA, hdd:pio
[4294674.343000] Probing IDE interface ide0...
[4294674.606000] hda: HTS548040M9AT00, ATA DISK drive
[4294675.218000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294675.218000] Probing IDE interface ide1...
[4294675.890000] hdc: HL-DT-STCD-RW/DVD-ROM GCC-4244N, ATAPI CD/DVD-ROM drive
[4294676.196000] ide1 at 0x170-0x177,0x376 on irq 15
[4294676.196000] Probing IDE interface ide2...
[4294676.709000] Probing IDE interface ide3...
[4294677.221000] Probing IDE interface ide4...
[4294677.733000] Probing IDE interface ide5...
[4294678.252000] hda: max request size: 1024KiB
[4294678.274000] hda: 78140160 sectors (40007 MB) w/7877KiB Cache, CHS=16383/255/63, UDMA(100)
[4294678.274000] hda: cache flushes supported
[4294678.274000]  /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 p6 > p3
[4294678.322000] hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache
[4294678.322000] Uniform CD-ROM driver Revision: 3.20
[4294678.851000] Attempting manual resume
[4294678.875000] swsusp: Suspend partition has wrong signature?
[4294678.944000] usbcore: registered new driver usbfs
[4294678.944000] usbcore: registered new driver hub
[4294678.946000] USB Universal Host Controller Interface driver v2.2
[4294678.946000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[4294678.946000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[4294678.946000] uhci_hcd 0000:00:1d.0: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
[4294679.009000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[4294679.009000] uhci_hcd 0000:00:1d.0: irq 11, io base 0x0000bf80
[4294679.009000] hub 1-0:1.0: USB hub found
[4294679.009000] hub 1-0:1.0: 2 ports detected
[4294679.012000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[4294679.012000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[4294679.012000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[4294679.012000] uhci_hcd 0000:00:1d.1: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
[4294679.074000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[4294679.074000] uhci_hcd 0000:00:1d.1: irq 11, io base 0x0000bf40
[4294679.074000] hub 2-0:1.0: USB hub found
[4294679.074000] hub 2-0:1.0: 2 ports detected
[4294679.077000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[4294679.077000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[4294679.077000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[4294679.077000] uhci_hcd 0000:00:1d.2: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
[4294679.139000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[4294679.139000] uhci_hcd 0000:00:1d.2: irq 11, io base 0x0000bf20
[4294679.139000] hub 3-0:1.0: USB hub found
[4294679.139000] hub 3-0:1.0: 2 ports detected
[4294679.198000] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
[4294679.198000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> Link [LNKH] -> GSI 11 (level, low) -> IRQ 11
[4294679.198000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[4294679.198000] ehci_hcd 0000:00:1d.7: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
[4294679.198000] ehci_hcd 0000:00:1d.7: debug port 1
[4294679.199000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[4294679.199000] ehci_hcd 0000:00:1d.7: irq 11, io mem 0xf4fffc00
[4294679.202000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[4294679.203000] ehci_hcd 0000:00:1d.7: USB 2.0 initialized, EHCI 1.00, driver 10 Dec 2004
[4294679.203000] hub 4-0:1.0: USB hub found
[4294679.203000] hub 4-0:1.0: 6 ports detected
[4294679.351000] b44.c:v0.95 (Aug 3, 2004)
[4294679.351000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[4294679.355000] eth0: Broadcom 4400 10/100BaseT Ethernet 00:12:3f:0d:98:7d
[4294681.728000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3] C4[C3])
[4294681.728000] ACPI: Processor [CPU0] (supports 8 throttling states)
[4294681.732000] ACPI: Thermal Zone [THM] (41 C)
[4294682.014000] Attempting manual resume
[4294682.028000] swsusp: Suspend partition has wrong signature?
[4294682.077000] kjournald starting.  Commit interval 5 seconds
[4294682.077000] EXT3-fs: mounted filesystem with ordered data mode.
[4294683.312000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294685.953000] Adding 433684k swap on /dev/hda6.  Priority:-1 extents:1
[4294686.246000] EXT3 FS on hda3, internal journal
[4294692.785000] parport: PnPBIOS parport detected.
[4294692.785000] parport0: PC-style at 0x378 (0x778), irq 7, dma 1 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[4294692.867000] lp0: using parport0 (interrupt-driven).
[4294692.888000] mice: PS/2 mouse device common for all mice
[4294693.191000] alps.c: Enabling hardware tapping
[4294693.256000] input: PS/2 Mouse on isa0060/serio1
[4294693.258000] input: AlpsPS/2 ALPS GlidePoint on isa0060/serio1
[4294693.506000] ts: Compaq touchscreen protocol output
[4294696.370000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[4294697.370000] cdrom: open failed.
[4294699.764000] Linux agpgart interface v0.101 (c) Dave Jones
[4294699.769000] agpgart: Detected an Intel 855PM Chipset.
[4294699.786000] agpgart: AGP aperture is 128M @ 0xe0000000
[4294699.858000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294699.861000] shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
[4294699.861000] shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
[4294700.038000] shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
[4294700.038000] shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
[4294700.082000] hw_random: cannot enable RNG, aborting
[4294700.347000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
[4294700.347000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[4294701.156000] intel8x0_measure_ac97_clock: measured 49491 usecs
[4294701.156000] intel8x0: clocking to 48000
[4294701.888000] Linux Kernel Card Services
[4294701.888000]   options:  [pci] [cardbus] [pm]
[4294701.896000] PCI: Enabling device 0000:02:01.0 (0000 -> 0002)
[4294701.896000] ACPI: PCI Interrupt 0000:02:01.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[4294701.896000] Yenta: CardBus bridge found at 0000:02:01.0 [1028:01be]
[4294701.896000] Yenta O2: res at 0x94/0xD4: 00/ea
[4294701.896000] Yenta O2: enabling read prefetch/write burst
[4294702.016000] Yenta: ISA IRQ mask 0x0418, PCI irq 11
[4294702.016000] Socket status: 30000006
[4294702.019000] PCI: Enabling device 0000:02:01.1 (0000 -> 0002)
[4294702.019000] ACPI: PCI Interrupt 0000:02:01.1[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[4294702.019000] Yenta: CardBus bridge found at 0000:02:01.1 [1028:01be]
[4294702.139000] Yenta: ISA IRQ mask 0x0418, PCI irq 11
[4294702.139000] Socket status: 30000006
[4294703.426000] Real Time Clock Driver v1.12
[4294703.487000] input: PC Speaker
[4294704.177000] NET: Registered protocol family 17
[4294705.168000] b44: eth0: Link is down.
[4294707.168000] b44: eth0: Link is up at 100 Mbps, full duplex.
[4294707.168000] b44: eth0: Flow control is off for TX and off for RX.
[4294712.554000] NET: Registered protocol family 10
[4294712.555000] Disabled Privacy Extensions on device c02eb280(lo)
[4294712.555000] IPv6 over IPv4 tunneling driver
[4294714.351000] ACPI: AC Adapter [AC] (off-line)
[4294714.654000] ACPI: Battery Slot [BAT0] (battery present)
[4294714.654000] ACPI: Battery Slot [BAT1] (battery absent)
[4294714.668000] ACPI: Lid Switch [LID]
[4294714.668000] ACPI: Power Button (CM) [PBTN]
[4294714.668000] ACPI: Sleep Button (CM) [SBTN]
[4294714.744000] ibm_acpi: ec object not found
[4294714.830000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[4294721.808000] [drm] Initialized drm 1.0.0 20040925
[4294721.809000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[4294721.811000] [drm] Initialized radeon 1.16.0 20050311 on minor 0: ATI Technologies Inc Radeon R250 Lf [FireGL 9000]
[4294721.811000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[4294721.811000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 1x mode
[4294721.811000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 1x mode
[4294722.036000] [drm] Loading R200 Microcode
[4294723.102000] eth0: no IPv6 routers present
[4294723.334000] apm: BIOS not found.
[4294724.080000] cs: IO port probe 0x100-0x4ff: clean.
[4294724.082000] cs: IO port probe 0x100-0x4ff: clean.
[4294724.083000] cs: IO port probe 0xc00-0xcf7: clean.
[4294724.083000] cs: IO port probe 0xc00-0xcf7: clean.
[4294724.084000] cs: IO port probe 0xa00-0xaff: clean.
[4294724.084000] cs: IO port probe 0xa00-0xaff: clean.
[4294724.587000] Bluetooth: Core ver 2.7
[4294724.587000] NET: Registered protocol family 31
[4294724.587000] Bluetooth: HCI device and connection manager initialized
[4294724.587000] Bluetooth: HCI socket layer initialized
[4294724.649000] Bluetooth: L2CAP ver 2.7
[4294724.649000] Bluetooth: L2CAP socket layer initialized
[4294724.673000] Bluetooth: RFCOMM ver 1.5
[4294724.673000] Bluetooth: RFCOMM socket layer initialized
[4294724.673000] Bluetooth: RFCOMM TTY layer initialized

---

### Post by Zelut on 2006-01-05
Ok, next if you could do: *lspci*, find the wireless card listed & make note of the 000 previous to the listing.  Compare that # with *lspci -n*.  See if you can find something similar to '104c:8400'

Let me know if/when you can find that number and I'll point you to some drivers.  I know wireless can be tricky but with how often I've succeeded I say 'bring 'em on!'

---

### Post by zahidism on 2006-01-05
my wireless card isnt listed :(  im following through this build process for ndiswrapper 1.7 and im stuck here

root@ubuntu:/usr/src/ndiswrapper-1.7# make
make -C driver
make[1]: Entering directory `/usr/src/ndiswrapper-1.7/driver'
make -C /lib/modules/2.6.12-9-386/build SUBDIRS=/usr/src/ndiswrapper-1.7/driver \
        DRIVER_VERSION=1.7
make[2]: Entering directory `/usr/src/linux-headers-2.6.12-9-386'
  Building modules, stage 2.
  MODPOST
make[2]: Leaving directory `/usr/src/linux-headers-2.6.12-9-386'
make[1]: Leaving directory `/usr/src/ndiswrapper-1.7/driver'
make -C utils[B]
make[1]: Entering directory `/usr/src/ndiswrapper-1.7/utils'
gcc -g -Wall -DUTILS_VERSION=\"1.7\"  -o loadndisdriver loadndisdriver.c
make[1]: gcc: Command not found
make[1]: *** [loadndisdriver] Error 127
make[1]: Leaving directory `/usr/src/ndiswrapper-1.7/utils'
make: *** [all] Error 2[/B]
root@ubuntu:/usr/src/ndiswrapper-1.7#

the bold is where stuff goes to hell

---

### Post by zahidism on 2006-01-05
found it

0000:02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

14e4:4320  from lspci -n

---

### Post by Zelut on 2006-01-05
It should be listed.. it was included in the dmesg output above so the computer is recognizing it.  Is it a built-in card? pcmcia? is this on a desktop?

---

### Post by zahidism on 2006-01-05
i've installed ndiswrapper-utils using synaptic but i dont think it really did anything

---

### Post by zahidism on 2006-01-05
[QUOTE=kuyaedz]It should be listed.. it was included in the dmesg output above so the computer is recognizing it.  Is it a built-in card? pcmcia? is this on a desktop?[/QUOTE]


0000:02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

14e4:4320 from lspci -n

---

### Post by Zelut on 2006-01-05
Ok, we're going to try a few drivers for this (the drivers are tricky).

[ftp://ftp.support.acer-euro.com/notebook/aspire_1500/drivers/80211g.zip](ftp://ftp.support.acer-euro.com/notebook/aspire_1500/drivers/80211g.zip)

unzip the bcmxx.inf & .sys files to your home folder(driver folder) & try these commands:

sudo ndiswrapper -i bcmxx.inf
sudo ndiswrapper -l

let me know the output of that. (hopefully 'hardware present, driver present')

---

### Post by zahidism on 2006-01-05
root@ubuntu:~# ndiswrapper -i bcmwl5.inf
bash: ndiswrapper: command not found

---

### Post by Zelut on 2006-01-05
ohh, I'm sorry.

sudo apt-get install ndiswrapper-utils
sudo ndiswrapper -i bcmwl5.inf
sudo ndiswrapper -l

---

### Post by zahidism on 2006-01-05
root@ubuntu:/home# ndiswrapper -l
Installed ndis drivers:
bcmwl5  invalid driver!

---

### Post by Zelut on 2006-01-05
ok, we'll try another.. it is very particular about the drivers.

try the same method with this driver.. 
[http://www.silfreed.net/download/hpzt3000cto/SP23107A.tar.gz](http://www.silfreed.net/download/hpzt3000cto/SP23107A.tar.gz)

---

### Post by zahidism on 2006-01-05
maybe this will help, its an 802.11 b/g wireless by dell (dell wlan miniPCI 1350)

---

### Post by zahidism on 2006-01-05
progress!!! now it says the hardware present thing

---

### Post by Zelut on 2006-01-05
Thats what we want to see :)

Now do:
sudo modprobe ndiswrapper
sudo ndiswrapper -m
(those auto-load the module at boot)

Now head to System > Admin > Networking > Configure & see if you've got a listed wireless card.  Activate it, enter your SSID & see if it works.

---

### Post by zahidism on 2006-01-05
root@ubuntu:~# sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.12-9-386/misc/ndiswrapper.ko): Invalid argument

---

### Post by zahidism on 2006-01-05
root@ubuntu:~# ndiswrapper -m
Adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper

---

### Post by Zelut on 2006-01-05
seen that before.. uhm, it does look like you aren't using the latest available kernel.

sudo apt-get update && sudo apt-get upgrade
does that offer you some updates?

---

### Post by zahidism on 2006-01-05
root@ubuntu:~# sudo apt-get update
Reading package lists... Done
root@ubuntu:~# apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by Zelut on 2006-01-05
Ok, that makes me wonder about my theory then.. (from previous experience I thought that 'error inserting ndiswrapper' was kernel related.  May not be.

Lets try a few more things.. 
can you retry the *sudo modprobe ndiswrapper* after a reboot?
Also, we may need to try another driver..  If no luck after a reboot lets try this:

sudo ndiswrapper -e bcmwl5 (or ndiswrapper -l, -e listed driver)
[URL="ftp://ftp.support.acer-euro.com/notebook/aspire_1500/drivers/80211g.zip"]this
[/URL]

[or this]("ftp://ftp.inexq.com/Drivers/MR054g(R01).zip")

---

### Post by zahidism on 2006-01-05
i read somehwere that it doesnt jive if i tried to compile it and use the deb package from synaptic, how exaclty do i remove all the crap i did trying to install it myself...maybe thats the problem?

---

### Post by zahidism on 2006-01-05
ok the last one when i installed it it installed it w/o doing  a force install thing it just said installed.  but when i mod probe it still doesnt work

---

### Post by zahidism on 2006-01-05
i think the problem is with my install of ndiswrapper, it says it cant find some ndiswrapper.ko or w/e

---

### Post by zahidism on 2006-01-06
i feel as though i should update, i installed module-assistant (search how to add repositories and search ubuntu for module-assistant) and it worked!

---

### Post by randomnote1 on 2006-01-07
Thank you so much for this information.  This is the only place I've found any useful info about installing wireless cards.  Thanks!

---

### Post by bikeboy on 2006-01-07
Just to let you know I'm successfully using the same Broadcom chipset, in the pcmcia variety.

Can't remember how I got it going but I think I followed a wiki entry to install ndiswrapper then used the Windows driver  for my wireless card from it's website.

After that I had to manually configure my /etc/network/interfaces a bit...but since then I have been able to configure via the gui.

Try this site for the drivers if you don't have them already on cd or something
[http://www.minitar.com/index.php?maincat=download](http://www.minitar.com/index.php?maincat=download)
You are looking for the 802.11G Broadcom driver. Ndis needs 2 files, ms68bm.inf and ms68bm.sys

---

### Post by ajaustin on 2006-01-24
I am desperate also having spent days/weeks trying to get ndiswrapper
working with Intel Wireless 2200BG.  Where I am so far:-

I started off by trying a compile from source install because that was
what the HOWTO I was following suggested but that ended me up with
"modprobe -i ndiswrapper" failing with "invalid argument" error.

I then discovered that it should all work with ndiswrapper module
installed by the linux-image-2.6.12-9-386 package, so I removed all the
source code compiled attempt and re-installed the linux-image-2.6.12-9-386
package.  A new
/lib/modules/2.6.12-9-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko
showed up. 

I followed the instructions at [https://wiki.ubuntu.com/HowToSetUpNdiswrapper?highlight=%28ndiswrapper%29](https://wiki.ubuntu.com/HowToSetUpNdiswrapper?highlight=%28ndiswrapper%29)
to use lspci to determine exactly my network card and downloaded the latest
 driver files which are w22n51.INF and w22n51.sys.  I have done 
"ndiswrapper -i /path/to/my/w22n51.INF", "ndiswrapper -m" to create 
the alias for wlan0 and "ndiswrapper -hotplug"; "ndiswrapper -l" 
shows the driver loaded and hardware present.

I am now able to "modprobe -i ndiswrapper" and the module
loads OK and shows up with "lsmod".  Module ipw2200 also shows in "lsmod" 
and I am not sure if this is OK.

I have edited /etc/network/interfaces to contain the following:-

> 

#auto eth0
#iface eth0 inet static
#address 10.0.0.10
#netmask 255.255.255.0
#gateway 10.0.0.138
#wireless-essid belkin54g
#wireless-key AAAAA00000

auto wlan0
iface wlan0 inet static
address 10.0.0.10
netmask 255.255.255.0
gateway 10.0.0.138
wireless-essid belkin54g
wireless-key AAAAA00000

I expected to see wlan0 in the Networking GUI, but it's not there, eth0 still is however even though I have taken it out of /etc/network/interfaces.

If I try to start wlan0 with "ifup wlan0" I get:-
> root@ubuntu:~# ifup wlan0
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan0 ; No such device.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; No such device.
SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
SIOCSIFNETMASK: No such device
wlan0: ERROR while getting interface flags: No such device
Failed to bring up wlan0.


It seems to be saying that wlan0 does not exist.  There is an alias for it in 
/etc/modprobe.d/ndiswrapper:-

> alias wlan0 ndiswrapper


Not sure what to try next.  Any help would be most appreciated.

Tony

---

