---
title: "Internal USB 6 in 1 card reader don't works."
date: 2005-05-07
forum: Hardware &amp; Laptops
---

### Post by sksbir on 2005-05-07
Hi folks 

Sorry to begin here with my problems. i'm registered on french forum since several weeks, and posted [this problem there](http://forum.ubuntu-fr.org/viewtopic.php?pid=27873#p27873), but without any answer until now. I hope to get an answer here (even "no, it can't works" would be an acceptable answer.. :wink: )

The problem occurs with a [gericom cinema XXL](http://www.gericom.com/index.php?id=180&backPID=180&tt_products=113) (almost the same computer than [ECS G900](http://www.ecsusa.com/aboutUs/pr_031904.html) I think): I'm trying to get the internal 6 in 1 card reader working.

under windows XP, i had to install specific driver witch name is "C-media USB Mass storage controler" to get this reader recognized.

I known that this reader, almost an internal one, is on USB plugged.

under ubuntu, nothing appends when inserting a smartmedia card. ls /dev/sd* gives : no such device...

Just to proof the USB controlers, I used an USB memory stick like [this one](http://www.ldlc.fr/fiche/PB00025964.html): it works well when inserted (ls /dev/sd* --> /dev/sda  /dev/sda1)

here is what dmesg gives:

```
# dmesg|more
ages, LIFO batch:1
  Normal zone: 126928 pages, LIFO batch:16
  HighMem zone: 0 pages, LIFO batch:1
DMI 2.3 present.
ACPI: RSDP (v000 ACPIAM                                ) @ 0x000f6ae0
ACPI: RSDT (v001 A M I  OEMRSDT  0x05000427 MSFT 0x00000097) @ 0x1ffd0000
ACPI: FADT (v002 A M I  OEMFACP  0x05000427 MSFT 0x00000097) @ 0x1ffd0200
ACPI: MADT (v001 A M I  OEMAPIC  0x05000427 MSFT 0x00000097) @ 0x1ffd0390
ACPI: OEMB (v001 A M I  AMI_OEM  0x05000427 MSFT 0x00000097) @ 0x1ffdf040
ACPI: DSDT (v001  1ABMR 1ABMR000 0x00000000 INTL 0x02002026) @ 0x00000000
ACPI: PM-Timer IO Port: 0x808
ACPI: Local APIC address 0xfee00000
ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Processor #0 15:3 APIC version 20
ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Processor #1 15:3 APIC version 20
WARNING: NR_CPUS limit of 1 reached.  Processor ignored.
ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
IOAPIC[0]: apic_id 2, version 2, address 0xfec00000, GSI 0-23
ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
ACPI: IRQ0 used by override.
ACPI: IRQ2 used by override.
ACPI: IRQ9 used by override.
Enabling APIC mode:  Flat.  Using 1 I/O APICs
Using ACPI (MADT) for SMP configuration information
Built 1 zonelists
Kernel command line: root=/dev/hda2 ro quiet splash
mapped APIC to ffffd000 (fee00000)
mapped IOAPIC to ffffc000 (fec00000)
Initializing CPU#0
PID hash table entries: 2048 (order: 11, 32768 bytes)
Detected 3001.997 MHz processor.
Using pmtmr for high-res timesource
Console: colour VGA+ 80x25
Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Memory: 511312k/524096k available (1587k kernel code, 12156k reserved, 714k data, 164k init, 0k highmem)
Checking if this processor honours the WP bit even in supervisor mode... Ok.
Calibrating delay loop... 5947.39 BogoMIPS (lpj=2973696)
Security Framework v1.0.0 initialized
SELinux:  Disabled at boot.
Mount-cache hash table entries: 512 (order: 0, 4096 bytes)
CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000441d 00000000
CPU: After vendor identify, caps: bfebfbff 00000000 00000000 00000000 0000441d 00000000
monitor/mwait feature present.
using mwait in idle threads.
CPU: Trace cache: 12K uops, L1 D cache: 16K
CPU: L2 cache: 1024K
CPU: After all inits, caps: bfebfbff 00000000 00000000 00000080 0000441d 00000000
Intel machine check architecture supported.
Intel machine check reporting enabled on CPU#0.
CPU0: Intel P4/Xeon Extended MCE MSRs (12) available
CPU0: Thermal monitoring enabled
CPU: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 04
Enabling fast FPU save and restore... done.
Enabling unmasked SIMD FPU exception support... done.
Checking 'hlt' instruction... OK.
ACPI: Looking for DSDT in initrd... not found!
ENABLING IO-APIC IRQs
..TIMER: vector=0x31 pin1=2 pin2=-1
checking if image is initramfs...it isn't (bad gzip magic numbers); looks like an initrd
Freeing initrd memory: 4524k freed
NET: Registered protocol family 16
PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=1
PCI: Using configuration type 1
mtrr: v2.0 (20020519)
ACPI: Subsystem revision 20050211
ACPI: Interpreter enabled
ACPI: Using IOAPIC for interrupt routing
ACPI: PCI Root Bridge [PCI0] (00:00)
PCI: Probing PCI hardware (bus 00)
Uncovering SIS963 that hid as a SIS503 (compatible=1)
Enabling SiS 96x SMBus.
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
ACPI: Embedded Controller [EC] (gpe 16)
ACPI: PCI Interrupt Link [LNKA] (IRQs *10)
ACPI: PCI Interrupt Link [LNKB] (IRQs *10)
ACPI: PCI Interrupt Link [LNKC] (IRQs *10)
ACPI: PCI Interrupt Link [LNKD] (IRQs *5)
ACPI: PCI Interrupt Link [LNKE] (IRQs *11)
ACPI: PCI Interrupt Link [LNKF] (IRQs *11)
ACPI: PCI Interrupt Link [LNKG] (IRQs *11)
ACPI: PCI Interrupt Link [LNKH] (IRQs *11)
Linux Plug and Play Support v0.97 (c) Adam Belay
pnp: PnP ACPI init
pnp: PnP ACPI: found 9 devices
PnPBIOS: Disabled by ACPI PNP
PCI: Using ACPI for IRQ routing
** PCI interrupts are no longer routed automatically.  If this
** causes a device to stop working, it is probably because the
** driver failed to call pci_enable_device().  As a temporary
** workaround, the "pci=routeirq" argument restores the old
** behavior.  If this argument makes the device work again,
** please email the output of "lspci" to bjorn.helgaas@hp.com
** so I can fix the driver.
pnp: 00:07: ioport range 0x200-0x20f has been reserved
audit: initializing netlink socket (disabled)
audit(1115319723.792:0): initialized
VFS: Disk quotas dquot_6.5.1
Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
devfs: boot_options: 0x0
Initializing Cryptographic API
isapnp: Scanning for PnP cards...
isapnp: No Plug & Play device found
i8042.c: Detected active multiplexing controller, rev 1.1.
serio: i8042 AUX0 port at 0x60,0x64 irq 12
serio: i8042 AUX1 port at 0x60,0x64 irq 12
serio: i8042 AUX2 port at 0x60,0x64 irq 12
serio: i8042 AUX3 port at 0x60,0x64 irq 12
serio: i8042 KBD port at 0x60,0x64 irq 1
Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
ACPI: PCI interrupt 0000:00:02.6[C] -> GSI 18 (level, low) -> IRQ 18
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
EUSB  USB USB2 USB3 S139 AC97 MC97 MPC1 MPC2 GLAN  MAC CBUS
ACPI: (supports S0 S1 S3 S4 S5)
RAMDISK: cramfs filesystem found at block 0
RAMDISK: Loading 4524KiB [1 disk] into ram disk... /

done.
VFS: Mounted root (cramfs filesystem) readonly.
Freeing unused kernel memory: 164k freed
ACPI: Processor [CPU1] (supports 8 throttling states)
NET: Registered protocol family 1
Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
SIS5513: IDE controller at PCI slot 0000:00:02.5
SIS5513: chipset revision 0
SIS5513: not 100% native mode: will probe irqs later
SIS5513: SiS 962/963 MuTIOL IDE UDMA133 controller
    ide0: BM-DMA at 0xff00-0xff07, BIOS settings: hda:DMA, hdb:DMA
    ide1: BM-DMA at 0xff08-0xff0f, BIOS settings: hdc:DMA, hdd:DMA
Probing IDE interface ide0...
hda: TOSHIBA MK6022GAX, ATA DISK drive
elevator: using anticipatory as default io scheduler
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
hda: max request size: 128KiB
hda: 117210240 sectors (60011 MB), CHS=65535/16/63, UDMA(33)
hda: cache flushes supported
 /dev/ide/host0/bus0/target0/lun0: p1 p2 p3 < p5 >
Probing IDE interface ide1...
hdd: MATSHITADVD-RAM UJ-815A, ATAPI CD/DVD-ROM drive
ide1 at 0x170-0x177,0x376 on irq 15
Probing IDE interface ide2...
Probing IDE interface ide3...
Probing IDE interface ide4...
Probing IDE interface ide5...
Stopping tasks: ==|
Freeing memory... done (463 pages freed)
Restarting tasks... done
EXT3-fs: mounted filesystem with ordered data mode.
kjournald starting.  Commit interval 5 seconds
Adding 1164672k swap on /dev/hda5.  Priority:-1 extents:1
EXT3 FS on hda2, internal journal
Linux agpgart interface v0.100 (c) Dave Jones
agpgart: Detected SiS 648 chipset
agpgart: Maximum main memory to use for agp memory: 439M
agpgart: AGP aperture is 64M @ 0xe0000000
fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[fglrx] Maximum main memory to use for locked dma buffers: 432 MBytes.
ACPI: PCI interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[fglrx] module loaded - fglrx 8.8.25 [Jan 14 2005] on minor 0
hdd: ATAPI 24X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache
Uniform CD-ROM driver Revision: 3.20
lp: driver loaded but no devices found
mice: PS/2 mouse device common for all mice
Synaptics Touchpad, model: 1
 Firmware: 5.9
 Sensor: 18
 new absolute packet format
 Touchpad has extended capability bits
 -> 4 multi-buttons, i.e. besides standard buttons
 -> multifinger detection
 -> palm detection
input: SynPS/2 Synaptics TouchPad on isa0060/serio4
ieee1394: Initialized config rom entry `ip1394'
SCSI subsystem initialized
sbp2: $Rev: 1219 $ Ben Collins <bcollins@debian.org>
Capability LSM initialized
device-mapper: 4.3.0-ioctl (2004-09-30) initialised: dm-devel@redhat.com
ts: Compaq touchscreen protocol output
md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
cdrom: open failed.
NTFS driver 2.1.22 [Flags: R/O MODULE].
NTFS volume version 3.1.
Real Time Clock Driver v1.12
input: PC Speaker
cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
shpchp: shpc_init : shpc_cap_offset == 0
shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Evaluate _OSC Set fails. Status = 0x0005
pciehp: add_host_bridge: status 5
pciehp: Fails to gain control of native hot-plug
i2c-sis96x version 1.0.0
sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0x0c00
ohci1394: $Rev: 1223 $ Ben Collins <bcollins@debian.org>
ACPI: PCI interrupt 0000:00:02.3[b] -> GSI 17 (level, low) -> IRQ 17
ohci1394: fw-host0: Unexpected PCI resource length of 1000!
ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[17]  MMIO=[dfff6000-dfff67ff]  Max Packet=[2048]
ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00000ae6ff16bd52]
ACPI: PCI interrupt 0000:00:02.7[C] -> GSI 18 (level, low) -> IRQ 18
intel8x0_measure_ac97_clock: measured 49516 usecs
intel8x0: clocking to 48000
usbcore: registered new driver usbfs
usbcore: registered new driver hub
ohci_hcd: 2004 Nov 08 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
ACPI: PCI interrupt 0000:00:03.0[A] -> GSI 20 (level, low) -> IRQ 20
ohci_hcd 0000:00:03.0: Silicon Integrated Systems [SiS] USB 1.0 Controller
ohci_hcd 0000:00:03.0: irq 20, pci mem 0xdfff7000
ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:03.1[b] -> GSI 21 (level, low) -> IRQ 21
ohci_hcd 0000:00:03.1: Silicon Integrated Systems [SiS] USB 1.0 Controller (#2)
ohci_hcd 0000:00:03.1: irq 21, pci mem 0xdfff8000
ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 2
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:03.2[C] -> GSI 22 (level, low) -> IRQ 22
ohci_hcd 0000:00:03.2: Silicon Integrated Systems [SiS] USB 1.0 Controller (#3)
ohci_hcd 0000:00:03.2: irq 22, pci mem 0xdfff9000
ohci_hcd 0000:00:03.2: new USB bus registered, assigned bus number 3
hub 3-0:1.0: USB hub found
hub 3-0:1.0: 2 ports detected
usb 2-1: new full speed USB device using ohci_hcd and address 2
ACPI: PCI interrupt 0000:00:03.3[D] -> GSI 23 (level, low) -> IRQ 23
ehci_hcd 0000:00:03.3: Silicon Integrated Systems [SiS] USB 2.0 Controller
ehci_hcd 0000:00:03.3: irq 23, pci mem 0xdfffa000
ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus number 4
PCI: cache line size of 128 is not supported by device 0000:00:03.3
ehci_hcd 0000:00:03.3: USB 2.0 initialized, EHCI 1.00, driver 26 Oct 2004
hub 4-0:1.0: USB hub found
hub 4-0:1.0: 6 ports detected
Linux video capture interface: v1.00
saa7130/34: v4l2 driver version 0.2.12 loaded
ACPI: PCI interrupt 0000:00:08.0[A] -> GSI 17 (level, low) -> IRQ 17
saa7133[0]: found at 0000:00:08.0, rev: 240, irq: 17, latency: 64, mmio: 0xdfffb800
saa7133[0]: subsystem: 5168:0212, board: UNKNOWN/GENERIC [card=0,autodetected]
saa7133[0]: board init: gpio is 10400
saa7133[0]: dsp access wait timeout [bit=WRR]
saa7133[0]: dsp access wait timeout [bit=WRR]
usb 2-1: device not accepting address 2, error -110
saa7133[0]: i2c eeprom 00: 68 51 12 02 10 28 ff ff ff ff ff ff ff ff ff ff
saa7133[0]: i2c eeprom 10: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
saa7133[0]: i2c eeprom 20: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
saa7133[0]: registered device video0 [v4l2]
saa7133[0]: registered device vbi0
ACPI: PCI interrupt 0000:00:0c.0[A] -> GSI 19 (level, low) -> IRQ 19
ACPI: PCI interrupt 0000:00:0c.0[A] -> GSI 19 (level, low) -> IRQ 19
eth0: Yukon Gigabit Ethernet 10/100/1000Base-T Adapter
      PrefPort:A  RlmtMode:Check Link State
Linux Kernel Card Services
  options:  [pci] [cardbus] [pm]
PCI: Enabling device 0000:00:0d.0 (0000 -> 0002)
ACPI: PCI interrupt 0000:00:0d.0[A] -> GSI 16 (level, low) -> IRQ 16
Yenta: CardBus bridge found at 0000:00:0d.0 [1019:0f38]
Yenta: adjusting diagnostic: 40 -> 60
Yenta: Using CSCINT to route CSC interrupts to PCI
Yenta: Routing CardBus interrupts to PCI
Yenta TI: socket 0000:00:0d.0, mfunc 0x000c1002, devctl 0x44
Yenta: ISA IRQ mask 0x0008, PCI irq 16
Socket status: 30000006
usb 2-1: new full speed USB device using ohci_hcd and address 4
usb 3-2: new low speed USB device using ohci_hcd and address 2
usbcore: registered new driver hiddev
input: USB HID v1.00 Mouse [Microsoft Microsoft Wheel Mouse Optical\uffff] on usb-0000:00:03.2-2
usbcore: registered new driver usbhid
drivers/usb/input/hid-core.c: v2.0:USB HID core driver
NET: Registered protocol family 17
eth0: network connection up using port A
    speed:           100
    autonegotiation: yes
    duplex mode:     full
    flowctrl:        none
    irq moderation:  disabled
    scatter-gather:  enabled
NET: Registered protocol family 10
Disabled Privacy Extensions on device c0313ce0(lo)
IPv6 over IPv4 tunneling driver
ACPI: AC Adapter [ADP0] (on-line)
ACPI: Battery Slot [BAT0] (battery present)
ACPI: Power Button (FF) [PWRF]
ACPI: Lid Switch [LID0]
ibm_acpi: ec object not found
apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
apm: overridden by ACPI.
[fglrx] AGP detected, AgpState   = 0x1f004e0b (hardware caps of chipset)
agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
agpgart: SiS delay workaround: giving bridge time to recover.
agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[fglrx] AGP enabled,  AgpCommand = 0x1f004302 (selected caps)
[fglrx] free  AGP = 54800384
[fglrx] max   AGP = 54800384
[fglrx] free  LFB = 116002816
[fglrx] max   LFB = 116002816
[fglrx] free  Inv = 0
[fglrx] max   Inv = 0
[fglrx] total Inv = 0
[fglrx] total TIM = 0
[fglrx] total FB  = 0
[fglrx] total AGP = 16384
cs: IO port probe 0x0100-0x04ff: excluding 0x480-0x48f 0x4d0-0x4d7
cs: IO port probe 0x0800-0x08ff: excluding 0x818-0x87f
cs: IO port probe 0x0c00-0x0cff: clean.
cs: IO port probe 0x0a00-0x0aff: clean.
eth0: no IPv6 routers present
#
```

Here is what lsub gives:
```
$lsusb
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 004: ID 0d8c:5000 C-Media Electronics, Inc.
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
$
```
I found this on this forum: [http://www.ubuntuforums.org/showthread.php?t=3628](http://www.ubuntuforums.org/showthread.php?t=3628)
this helped me to find the good command to get some result : lshal
the device bus 2/device 4 seems to be the good one:

```
udi = '/org/freedesktop/Hal/devices/usb_usb_device_d8c_5000_100_-1_noserial_0'
  info.udi = '/org/freedesktop/Hal/devices/usb_usb_device_d8c_5000_100_-1_noserial_0'  (string)
  info.product = 'Vendor Specific Interface'  (string)
  usb.interface.subclass = 255  (0xff)  (int)
  usb.interface.protocol = 255  (0xff)  (int)
  usb.interface.number = 0  (0x0)  (int)
  usb.interface.class = 255  (0xff)  (int)
  usb.configuration_value = 1  (0x1)  (int)
  usb.device_class = 0  (0x0)  (int)
  usb.device_protocol = 0  (0x0)  (int)
  usb.device_subclass = 0  (0x0)  (int)
  usb.max_power = 500  (0x1f4)  (int)
  usb.num_configurations = 1  (0x1)  (int)
  usb.num_interfaces = 1  (0x1)  (int)
  usb.device_revision_bcd = 256  (0x100)  (int)
  usb.is_self_powered = false  (bool)
  usb.can_wake_up = false  (bool)
  usb.product_id = 20480  (0x5000)  (int)
  usb.vendor_id = 3468  (0xd8c)  (int)
  usb.vendor = 'C-Media Electronics, Inc.'  (string)
  usb.product = 'USB Card Reader'  (string)
  usb.bus_number = 2  (0x2)  (int)
  usb.port_number = 1  (0x1)  (int)
  usb.level_number = 1  (0x1)  (int)
  usb.linux.device_number = 4  (0x4)  (int)
  usb.linux.parent_number = 4  (0x4)  (int)
  usb.num_ports = 0  (0x0)  (int)
  usb.speed_bcd = 4608  (0x1200)  (int)
  usb.version_bcd = 272  (0x110)  (int)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_d8c_5000_100_-1_noserial'  (string)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:03.1/usb2/2-1/2-1:1.0'  (string)
  linux.sysfs_path_device = '/sys/devices/pci0000:00/0000:00:03.1/usb2/2-1/2-1:1.0'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:03.1/usb2/2-1/2-1:1.0'  (string)
  info.bus = 'usb'  (string)
```

I don't know what to do now  ](*,) , and if anybody have an idea, it would be great...

---

### Post by Gandalf on 2005-05-07
well i have the same problem plus i don't know how it is plugged to the computer, lsusb don't give anything usefull :(

//EDIT:using the device manager it is plugged using PCI
someone any clue please?

---

### Post by sksbir on 2005-05-07
[QUOTE=Gandalf]well i have the same problem plus i don't know how it is plugged to the computer, lsusb don't give anything usefull :(

//EDIT:using the device manager it is plugged using PCI
someone any clue please?[/QUOTE]

perhaps may "lspci" give some info if your card reader is on PCI plugged.

---

### Post by Gandalf on 2005-05-07
[QUOTE=sksbir]perhaps may "lspci" give some info if your card reader is on PCI plugged.[/QUOTE]
 well yes but don't know where to go from there
```

0000:00:00.0 Host bridge: Intel Corp. 82852/855GM Host Bridge (rev 02)
0000:00:00.1 System peripheral: Intel Corp. 855GM/GME GMCH Memory I/O Control Registers (rev 02)
0000:00:00.3 System peripheral: Intel Corp. 855GM/GME GMCH Configuration Process Registers (rev 02)
0000:00:02.0 VGA compatible controller: Intel Corp. 82852/855GM Integrated Graphics Device (rev 02)
0000:00:02.1 Display controller: Intel Corp. 82852/855GM Integrated Graphics Device (rev 02)
0000:00:1d.0 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
0000:00:1d.7 USB Controller: Intel Corp. 82801DB/DBM (ICH4/ICH4-M) USB 2.0 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 83)
0000:00:1f.0 ISA bridge: Intel Corp. 82801DBM LPC Interface Controller (rev 03)
0000:00:1f.1 IDE interface: Intel Corp. 82801DBM (ICH4) Ultra ATA Storage Controller (rev 03)
0000:00:1f.3 SMBus: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
0000:00:1f.6 Modem: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
0000:02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:02:06.0 Network controller: Intel Corp. PRO/Wireless 2200BG (rev 05)
0000:02:09.0 CardBus bridge: Texas Instruments: Unknown device 8031
0000:02:09.2 FireWire (IEEE 1394): Texas Instruments: Unknown device 8032
0000:02:09.3 Unknown mass storage controller: Texas Instruments: Unknown device 8033
0000:02:09.4 0805: Texas Instruments: Unknown device 8034

```

---

### Post by sksbir on 2005-05-07
here is the lspci from my computer :
```

0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] SiS 645xx (rev 51)
0000:00:01.0 PCI bridge: Silicon Integrated Systems [SiS]: Unknown device 0003
0000:00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 14)
0000:00:02.1 SMBus: Silicon Integrated Systems [SiS]: Unknown device 0016
0000:00:02.3 FireWire (IEEE 1394): Silicon Integrated Systems [SiS] FireWire Controller
0000:00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
0000:00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound Controller (rev a0)
0000:00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
0000:00:08.0 Multimedia controller: Philips Semiconductors SAA7133 Audio+video broadcast decoder (rev f0)
0000:00:0c.0 Ethernet controller: Marvell Technology Group Ltd. Yukon Gigabit Ethernet 10/100/1000Base-T Adapter (rev 13)
0000:00:0d.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]

```

You have a lot's of unknow devices on your computer : I think this a not a good new. Does your firewire external devices work ?

---

### Post by Gandalf on 2005-05-07
i don't have firewire device so can't try

---

### Post by sksbir on 2005-05-08
[QUOTE=Gandalf]i don't have firewire device so can't try[/QUOTE]

Sorry, i can't help you anymore. It seems your problem is more hardware than mine


About my problem, may anybody help me ?

---

### Post by Sav on 2005-05-09
I am a totally newbie (got ubuntu since 7 days), but I did some search, because I have a notebook with a built-in card reader.
What I discovery is that my reader is connected to the pcmca bus.
I didn't handle it already, but you can give it a look.

---

### Post by sksbir on 2005-05-13
[QUOTE=Sav]I am a totally newbie (got ubuntu since 7 days), but I did some search, because I have a notebook with a built-in card reader.
What I discovery is that my reader is connected to the pcmca bus.
I didn't handle it already, but you can give it a look.[/QUOTE]

I don't know how you get this information on your card-reader, but i'm sure that my card reader is on internal USB plugged: under windows, it's name is "C-media USB Mass storage controler".

---

### Post by Sav on 2005-05-14
[QUOTE=sksbir]I don't know how you get this information on your card-reader, but i'm sure that my card reader is on internal USB plugged: under windows, it's name is "C-media USB Mass storage controler".[/QUOTE]

I searched the datasheets of my notebook.
By the way, it's sure that your reader is different.

---

### Post by sksbir on 2005-05-16
[QUOTE=Sav]I searched the datasheets of my notebook.
By the way, it's sure that your reader is different.[/QUOTE]

ok, but this don't help me : I still have no idea to get my reader working...  ](*,)

---

### Post by LinxNew on 2005-05-16
I see this article :

 Memory Card Reader

Relevant hardware:

    * 0000:00:0a.0 CardBus bridge: ENE Technology Inc CB-720/2/4 Cardbus Controller (rev 01)
    * 0000:00:0a.1 CardBus bridge: ENE Technology Inc CB-720/2/4 Cardbus Controller (rev 01)
    * 0000:00:0a.2 FLASH memory: ENE Technology Inc CB710 Memory Card Reader Controller 

In the newer kernels this device by Ene Technology Inc ([http://www.ene.com.tw/](http://www.ene.com.tw/)) seems to be supported. If your lspci sais "unknown device" then you should upgrade your kernel. The above output is made with a 2.6.9 gentoo kernel.

I have not tested it yet though...


Code: Kernel settings

Device Drivers  --->
   SCSI device support  --->
      <*>   SCSI generic support
      [*]   Probe all LUNs on each SCSI device


I have Ene installed and Ubuntu Hoary, but I have unknown device.  :-?

---

### Post by LinxNew on 2005-05-16
I try this commands :

modprobe pcmcia_core
modprobe yenta_socket
modprobe ds
cardctl ident

but when I try to use cardctl, I have an error command (not found) so in my device manager, I see that CB710 Cardbus Controller is recognize  :wink:  but I have unknown device  :-?

---

### Post by a-v0id on 2006-08-25
Hello! 
  I have been trawling the web for an answer to the above problem (internal usb multi card-reader). It seems quite a frequent problem and there seems to be no answer. The relating articles regarding card-readers are 2+ years old and relate to back-dated kernels. 

I being a mere peon of the linux world cannot contribute to the solution. However, I'd love to know the answer to this problem, as I'm stuck in a window-less house with hardware that doesn't function... and data that is inaccessable.

HOWTO anyone??

Thanks,

a-v0id

---

### Post by hashimoto on 2006-08-25
The chipset you have in the reader (0d8c:5000) isn't supported:

[http://www.think-future.de/wiki/index.php?title=USB](http://www.think-future.de/wiki/index.php?title=USB)

Says "Sell"

---

### Post by a-v0id on 2006-08-25
I know plenty of windows users who would love this item... i'll find someone who has an external wanting to swap :D


Thanks by the way!

---

### Post by Rhubarb on 2006-08-25
I've heard somewhere around these forums that if it's a Ricoh chipset, you may never get it working.  However if it's a Texas Instruments chipset, (I think) you'll have it all working soon (by the end of the year?) in one of the newer kernels.

In the mean time if you need to get your SD / MMC / Memory stick / CF card working, invest in a typical USB reader, I've had no problems with these at all under the current linux kernel.

---

### Post by newen on 2006-08-25
I wanted to begin reverse-engineering the ENE driver (CB710) for windows, but I don´t know how to start. Any idea of howto gather data from such a device?

---

