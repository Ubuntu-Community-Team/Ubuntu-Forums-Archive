---
title: "DMA Troubles"
date: 2005-08-31
forum: Hardware &amp; Laptops
---

### Post by makisupa123 on 2005-08-31
Had Ubuntu on a laptop for awhile...trying to get everything working on a new desktop I built.  Mobo is a Gigabyte k8vm800m (k8 triton series) with a Sempron 2800.  I have a couple of drives in the machine -- Hoary on hda and XP on hdb.  Hdc is a DVDRW that's not quite right either.  Here is the dmesg right after boot:

```
makisupa@semprOn:~$ sudo dmesg
Password:
0000 (reserved)
0MB HIGHMEM available.
447MB LOWMEM available.
found SMP MP-table at 000f5300
On node 0 totalpages: 114672
  DMA zone: 4096 pages, LIFO batch:1
  Normal zone: 110576 pages, LIFO batch:16
  HighMem zone: 0 pages, LIFO batch:1
DMI 2.3 present.
ACPI: RSDP (v000 VIAK8                                 ) @ 0x000f6ce0
ACPI: RSDT (v001 VIAK8  AWRDACPI 0x42302e31 AWRD 0x01010101) @ 0x1bff3000
ACPI: FADT (v001 VIAK8  AWRDACPI 0x42302e31 AWRD 0x01010101) @ 0x1bff3040
ACPI: MADT (v001 VIAK8  AWRDACPI 0x42302e31 AWRD 0x01010101) @ 0x1bff7900
ACPI: DSDT (v001 VIAK8  AWRDACPI 0x00001000 MSFT 0x0100000c) @ 0x00000000
ACPI: PM-Timer IO Port: 0x4008
ACPI: Local APIC address 0xfee00000
ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Processor #0 15:12 APIC version 16
ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
ACPI: IRQ0 used by override.
ACPI: IRQ2 used by override.
ACPI: IRQ9 used by override.
Enabling APIC mode:  Flat.  Using 1 I/O APICs
Using ACPI (MADT) for SMP configuration information
Built 1 zonelists
Kernel command line: root=/dev/hda1 ro quiet splash
mapped APIC to ffffd000 (fee00000)
mapped IOAPIC to ffffc000 (fec00000)
Initializing CPU#0
PID hash table entries: 2048 (order: 11, 32768 bytes)
Detected 1607.379 MHz processor.
Using pmtmr for high-res timesource
Console: colour VGA+ 80x25
Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
Memory: 446784k/458688k available (1595k kernel code, 11292k reserved, 721k data, 164k init, 0k highmem)
Checking if this processor honours the WP bit even in supervisor mode... Ok.
Calibrating delay loop... 3178.49 BogoMIPS (lpj=1589248)
Security Framework v1.0.0 initialized
SELinux:  Disabled at boot.
Mount-cache hash table entries: 512 (order: 0, 4096 bytes)
CPU: After generic identify, caps: 078bfbff c3d3fbff 00000000 00000000 00000000 00000000
CPU: After vendor identify, caps: 078bfbff c3d3fbff 00000000 00000000 00000000 00000000
CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
CPU: L2 Cache: 256K (64 bytes/line)
CPU: After all inits, caps: 078bfbff c3d3fbff 00000000 00000010 00000000 00000000
Intel machine check architecture supported.
Intel machine check reporting enabled on CPU#0.
CPU: AMD Sempron(tm) Processor 2800+ stepping 00
Enabling fast FPU save and restore... done.
Enabling unmasked SIMD FPU exception support... done.
Checking 'hlt' instruction... OK.
ACPI: Looking for DSDT in initrd... not found!
ENABLING IO-APIC IRQs
..TIMER: vector=0x31 pin1=2 pin2=-1
checking if image is initramfs...it isn't (bad gzip magic numbers); looks like an initrd
Freeing initrd memory: 4540k freed
NET: Registered protocol family 16
PCI: PCI BIOS revision 2.10 entry at 0xfb410, last bus=1
PCI: Using configuration type 1
mtrr: v2.0 (20020519)
ACPI: Subsystem revision 20050211
ACPI: Interpreter enabled
ACPI: Using IOAPIC for interrupt routing
ACPI: PCI Root Bridge [PCI0] (00:00)
PCI: Probing PCI hardware (bus 00)
PCI: Via IRQ fixup
PCI: Via IRQ fixup
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 *10 11 12)
ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 6 7 10 *11 12)
ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 10 *11 12)
ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 11 12) *5
ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12) *0, disabled.
ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12) *0, disabled.
ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 6 7 10 11 12) *0, disabled.
ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 6 7 10 11 12) *0, disabled.
ACPI: PCI Interrupt Link [ALKA] (IRQs 20) *0, disabled.
ACPI: PCI Interrupt Link [ALKB] (IRQs 21) *0, disabled.
ACPI: PCI Interrupt Link [ALKC] (IRQs 22) *0, disabled.
ACPI: PCI Interrupt Link [ALKD] (IRQs 23) *0, disabled.
Linux Plug and Play Support v0.97 (c) Adam Belay
pnp: PnP ACPI init
pnp: PnP ACPI: found 14 devices
PnPBIOS: Disabled by ACPI PNP
PCI: Using ACPI for IRQ routing
** PCI interrupts are no longer routed automatically.  If this
** causes a device to stop working, it is probably because the
** driver failed to call pci_enable_device().  As a temporary
** workaround, the "pci=routeirq" argument restores the old
** behavior.  If this argument makes the device work again,
** please email the output of "lspci" to bjorn.helgaas@hp.com
** so I can fix the driver.
pnp: 00:01: ioport range 0x4000-0x407f could not be reserved
pnp: 00:01: ioport range 0x40f0-0x40ff could not be reserved
pnp: 00:01: ioport range 0x5000-0x500f has been reserved
audit: initializing netlink socket (disabled)
audit(1125436300.131:0): initialized
VFS: Disk quotas dquot_6.5.1
Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
devfs: boot_options: 0x0
Initializing Cryptographic API
isapnp: Scanning for PnP cards...
isapnp: No Plug & Play device found
serio: i8042 AUX port at 0x60,0x64 irq 12
serio: i8042 KBD port at 0x60,0x64 irq 1
Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
io scheduler noop registered
io scheduler anticipatory registered
io scheduler deadline registered
io scheduler cfq registered
RAMDISK driver initialized: 16 RAM disks of 8192K size 1024 blocksize
input: AT Translated Set 2 keyboard on isa0060/serio0
NET: Registered protocol family 2
IP: routing cache hash table of 4096 buckets, 32Kbytes
TCP: Hash tables configured (established 32768 bind 65536)
NET: Registered protocol family 8
NET: Registered protocol family 20
Restarting tasks...<6> Strange, kswapd0 not stopped
 Strange, kseriod not stopped
 done
ACPI wakeup devices:
PCI0 USB0 USB1 USB2 USB6 USB7 USB8 USB9 UAR1 LPT1
ACPI: (supports S0 S1 S4 S5)
RAMDISK: cramfs filesystem found at block 0
RAMDISK: Loading 4540KiB [1 disk] into ram disk... done.
VFS: Mounted root (cramfs filesystem) readonly.
Freeing unused kernel memory: 164k freed
NET: Registered protocol family 1
Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
VP_IDE: IDE controller at PCI slot 0000:00:0f.1
ACPI: PCI Interrupt Link [ALKA] BIOS reported IRQ 0, using IRQ 20
ACPI: PCI Interrupt Link [ALKA] enabled at IRQ 20
ACPI: PCI interrupt 0000:00:0f.1[A] -> GSI 20 (level, low) -> IRQ 20
VP_IDE: chipset revision 6
VP_IDE: not 100% native mode: will probe irqs later
VP_IDE: VIA vt8237 (rev 00) IDE UDMA133 controller on pci0000:00:0f.1
    ide0: BM-DMA at 0xcc00-0xcc07, BIOS settings: hda:pio, hdb:pio
    ide1: BM-DMA at 0xcc08-0xcc0f, BIOS settings: hdc:pio, hdd:pio
Probing IDE interface ide0...
hda: ST320413A, ATA DISK drive
hdb: WDC WD153AA-53BAA0, ATA DISK drive
elevator: using anticipatory as default io scheduler
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
hda: max request size: 128KiB
hda: Host Protected Area detected.
        current capacity is 39102336 sectors (20020 MB)
        native  capacity is 39102337 sectors (20020 MB)
hda: Host Protected Area disabled.
hda: 39102337 sectors (20020 MB) w/512KiB Cache, CHS=38792/16/63, UDMA(100)
hda: cache flushes not supported
 /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >
hdb: max request size: 128KiB
hdb: 30064608 sectors (15393 MB) w/2048KiB Cache, CHS=29826/16/63, UDMA(66)
hdb: cache flushes not supported
 /dev/ide/host0/bus0/target1/lun0: p1
Probing IDE interface ide1...
hdc: AOPEN DUW1616/ARR, ATAPI CD/DVD-ROM drive
ide1 at 0x170-0x177,0x376 on irq 15
Probing IDE interface ide2...
Probing IDE interface ide3...
Probing IDE interface ide4...
Probing IDE interface ide5...
Stopping tasks: ==|
Freeing memory... done (463 pages freed)
Restarting tasks... done
EXT3-fs: hda1: orphan cleanup on readonly fs
kjournald starting.  Commit interval 5 seconds
ext3_orphan_cleanup: deleting unreferenced inode 2146360
EXT3-fs: hda1: 1 orphan inode deleted
EXT3-fs: recovery complete.
EXT3-fs: mounted filesystem with ordered data mode.
Adding 835340k swap on /dev/hda5.  Priority:-1 extents:1
EXT3 FS on hda1, internal journal
hdc: ATAPI 126X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache
Uniform CD-ROM driver Revision: 3.20
parport: PnPBIOS parport detected.
parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
lp0: using parport0 (interrupt-driven).
mice: PS/2 mouse device common for all mice
input: ImPS/2 Logitech Wheel Mouse on isa0060/serio1
Capability LSM initialized
device-mapper: 4.3.0-ioctl (2004-09-30) initialised: dm-devel@redhat.com
ts: Compaq touchscreen protocol output
md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[B]hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
hda: dma_intr: error=0x10 { SectorIdNotFound }, LBAsect=39102336, sector=39102336
ide: failed opcode was: unknown
hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
hda: dma_intr: error=0x10 { SectorIdNotFound }, LBAsect=39102336, sector=39102336
ide: failed opcode was: unknown
hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
hda: dma_intr: error=0x10 { SectorIdNotFound }, LBAsect=39102336, sector=39102336
ide: failed opcode was: unknown
hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
hda: dma_intr: error=0x10 { SectorIdNotFound }, LBAsect=39102336, sector=39102336
ide: failed opcode was: unknown
hda: DMA disabled
hdb: DMA disabled
ide0: reset: success
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x10 { SectorIdNotFound }, LBAsect=39167615, sector=39102336
ide: failed opcode was: unknown
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x10 { SectorIdNotFound }, LBAsect=39167615, sector=39102336
ide: failed opcode was: unknown
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x10 { SectorIdNotFound }, LBAsect=39167615, sector=39102336
ide: failed opcode was: unknown
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x10 { SectorIdNotFound }, LBAsect=39167615, sector=39102336
ide: failed opcode was: unknown
ide0: reset: success
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x10 { SectorIdNotFound }, LBAsect=39167615, sector=39102336
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 39102336[/B]
Real Time Clock Driver v1.12
input: PC Speaker
inserting floppy driver for 2.6.10-5-k7
Floppy drive(s): fd0 is 1.44M
FDC 0 is a post-1991 82077
Linux agpgart interface v0.100 (c) Dave Jones
agpgart: Detected AGP bridge 0
agpgart: Maximum main memory to use for agp memory: 380M
agpgart: AGP aperture is 64M @ 0xe0000000
cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
shpchp: shpc_init : shpc_cap_offset == 0
shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Evaluate _OSC Set fails. Status = 0x0005
pciehp: add_host_bridge: status 5
pciehp: Fails to gain control of native hot-plug
8139too Fast Ethernet driver 0.9.27
ACPI: PCI interrupt 0000:00:0a.0[A] -> GSI 18 (level, low) -> IRQ 18
eth0: RealTek RTL8139 at 0xa000, 00:08:a1:55:80:f4, IRQ 18
eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
ACPI: PCI interrupt 0000:00:13.0[A] -> GSI 18 (level, low) -> IRQ 18
eth1: RealTek RTL8139 at 0xe400, 00:0f:ea:27:f1:54, IRQ 18
eth1:  Identified 8139 chip type 'RTL-8100B/8139D'
8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
ACPI: PCI interrupt 0000:00:0b.0[A] -> GSI 19 (level, low) -> IRQ 19
SCSI subsystem initialized
libata version 1.10 loaded.
sata_via version 1.1
ACPI: PCI interrupt 0000:00:0f.0[B] -> GSI 20 (level, low) -> IRQ 20
sata_via(0000:00:0f.0): routed to hard irq line 4
ata1: SATA max UDMA/133 cmd 0xB400 ctl 0xB802 bmdma 0xC400 irq 20
ata2: SATA max UDMA/133 cmd 0xBC00 ctl 0xC002 bmdma 0xC408 irq 20
ata1: no device found (phy stat 00000000)
scsi0 : sata_via
ata2: no device found (phy stat 00000000)
scsi1 : sata_via
NET: Registered protocol family 17
usbcore: registered new driver usbfs
usbcore: registered new driver hub
USB Universal Host Controller Interface driver v2.2
ACPI: PCI Interrupt Link [ALKB] BIOS reported IRQ 0, using IRQ 21
ACPI: PCI Interrupt Link [ALKB] enabled at IRQ 21
ACPI: PCI interrupt 0000:00:10.0[A] -> GSI 21 (level, low) -> IRQ 21
uhci_hcd 0000:00:10.0: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
uhci_hcd 0000:00:10.0: irq 21, io base 0xd000
uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:10.1[A] -> GSI 21 (level, low) -> IRQ 21
uhci_hcd 0000:00:10.1: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#2)
uhci_hcd 0000:00:10.1: irq 21, io base 0xd400
uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:10.2[B] -> GSI 21 (level, low) -> IRQ 21
uhci_hcd 0000:00:10.2: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#3)
uhci_hcd 0000:00:10.2: irq 21, io base 0xd800
uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
hub 3-0:1.0: USB hub found
hub 3-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:10.3[B] -> GSI 21 (level, low) -> IRQ 21
uhci_hcd 0000:00:10.3: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#4)
uhci_hcd 0000:00:10.3: irq 21, io base 0xdc00
uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
hub 4-0:1.0: USB hub found
hub 4-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:10.4[C] -> GSI 21 (level, low) -> IRQ 21
ehci_hcd 0000:00:10.4: VIA Technologies, Inc. USB 2.0
ehci_hcd 0000:00:10.4: irq 21, pci mem 0xea001000
ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
ehci_hcd 0000:00:10.4: USB 2.0 initialized, EHCI 1.00, driver 26 Oct 2004
hub 5-0:1.0: USB hub found
hub 5-0:1.0: 8 ports detected
ACPI: PCI Interrupt Link [ALKC] BIOS reported IRQ 0, using IRQ 22
ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
ACPI: PCI interrupt 0000:00:11.5[C] -> GSI 22 (level, low) -> IRQ 22
PCI: Setting latency timer of device 0000:00:11.5 to 64
NET: Registered protocol family 10
Disabled Privacy Extensions on device c0315d40(lo)
IPv6 over IPv4 tunneling driver
ACPI: Power Button (FF) [PWRF]
ibm_acpi: ec object not found
eth0: no IPv6 routers present
UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'EMPIRE_STRIKES_BACK', timestamp 2004/05/13 01:26 (1ed4)

```

Notice the way DMA is enabled and then disabled along with the Seekcomplete Errors.  My /etc/modules is standard...is there a module i need to pass here (I've seen posts of people doing a AMD74XX -- but does nothing).  Is there someting I'm missing here?

I've resorted to making a specific entry in hdparm,config.  As follows:

```
/dev/hda {
	write_cache = on
	io32_support = 3
	dma = on
	interrupt_unmask = on
	mult_sect_io = 16
}
```

And according to hdparm -I its running in UDMA5.  But hdparm -Tt is giving me crap speeds:
```
/dev/hda:
 Timing cached reads:   1884 MB in  2.00 seconds = 941.20 MB/sec
 Timing buffered disk reads:   70 MB in  3.03 seconds =  23.14 MB/sec
makisupa@semprOn:~$
```




Another problem...which is probably related..what is difference in the way VLC plays a dvd from Totem (xine).  I can play a dvd in totem-xine, and it seems fairly stable (not choppy, fluid motion).  But when I try to play in vlc i get a series of cdda errors -- cant read sector.  There is no video. Libdvdcss2 is installed and assumed working due to successful playing in totem -- is this a correct assumption?   Both the drive and disk are new and function fine in Winbloze.

In conclusion.....seems like there should be some ide module that needs to be called in /etc/modules.  Does anyone know my options?  Does anyone have an other ideas?

Thanks for your time and help,

/mak

---

### Post by makisupa123 on 2005-08-31
Looking through that "complie your own kernel" thread -- while messing with it...I discovered something interesting.  There is a compilation option that says use this if your getting the errors I talked about above .. the option is to enable multimode by default.  Does anyone know how i can pass this command to the kernel as a module/command (ie. no recompiling).  Thanks!

/mak

---

### Post by Forge on 2005-09-01
I believe you'd need to recompile, not sure.

I've most often gotten that error on disks, controllers, and cables that were dying/dead.

Do you hear any strange noises? Grinding, clicking, pops? If so, your disk might be dying.

Try switching out the IDE cable for one that's seen less use. The newer 80wire cables are pretty fragile, IME, especially if you fold them over or let them crumple.

You might also want to check for and/or update to the latest BIOS for that motherboard. I was running one of the nForce3 K8 Tritons back when Athlon64s first came out, and it was painfully buggy and broken for 3 or 4 BIOS updates.

---

