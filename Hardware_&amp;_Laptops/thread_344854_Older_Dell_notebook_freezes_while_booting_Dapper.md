---
title: "Older Dell notebook freezes while booting Dapper"
date: 2007-01-23
forum: Hardware &amp; Laptops
---

### Post by giosetti on 2007-01-23
Hallo,

on a Dell LAtitude CPi A366XT I have installed xubuntu dapper.

On booting the computer freezes frequently - but not always - at this point:
```

17179605.896000  ts: Compaq touchscreen protocol output
 17179605.952000  PCI: Enabling device 0000:01:00.1 (0000 -> 0002)
 17179605.952000  PCI: Found IRQ 5 for device 0000:01:00.1
 17179605.952000  nm256: found card signature in video RAM: 0x27ec00
 17179605.952000  nm256: Mapping port 1 from 0x2709a0 - 0x27ec00
 17179606.208000  cs: IO port probe 0x100-0x3af: excluding 0x170-0x177
0x370-0x37f
```

The Wiki recommends to boot with the parameters noapm or pci=noacpi, sometimes that helps, sometimes not. Sometimes it helps to boot with the CD drive not mounted, sometimes it helps to boot without pcmcia cards. At one point when all that didn't help I started from battery and that helped, but the next time it didn't help.

In other words - I don't see any rule in this behaviour. The install CD starts nicely, also Windows does not cause any of this freezing.

I hope someone will have the solution for this. Below you find the whole dmesg.

Thanx,
Jost

============

```
17179569.184000  Linux version 2.6.15-26-386 (buildd@terranova) (gcc
version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Thu Aug 3 02:52:00
UTC 2006
 17179569.184000  BIOS-provided physical RAM map:
 17179569.184000   BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
 17179569.184000   BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
 17179569.184000   BIOS-e820: 00000000000c0000 - 00000000000cc000 (reserved)
 17179569.184000   BIOS-e820: 0000000000100000 - 0000000007fec000 (usable)
 17179569.184000   BIOS-e820: 0000000007fec000 - 0000000007ff0000 (reserved)
 17179569.184000   BIOS-e820: 00000000100a0000 - 0000000010100000 (reserved)
 17179569.184000   BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
 17179569.184000  0MB HIGHMEM available.
 17179569.184000  127MB LOWMEM available.
 17179569.184000  On node 0 totalpages: 32748
 17179569.184000    DMA zone: 4096 pages, LIFO batch:0
 17179569.184000    DMA32 zone: 0 pages, LIFO batch:0
 17179569.184000    Normal zone: 28652 pages, LIFO batch:7
 17179569.184000    HighMem zone: 0 pages, LIFO batch:0
 17179569.184000  DMI 2.3 present.
 17179569.184000  ACPI: RSDP (v000 DELL
 ) @ 0x000f38f0
 17179569.184000  ACPI: RSDT (v001 DELL    CPi A   0x27d10b07 ASL
0x00000061) @ 0x07ff0000
 17179569.184000  ACPI: FADT (v001 DELL    CPi A   0x27d10b07 ASL
0x00000061) @ 0x07ff0400
 17179569.184000  ACPI: BOOT (v001 DELL    CPi A   0x27d10b07 ASL
0x00000061) @ 0x07ff07c0
 17179569.184000  ACPI: DSDT (v001 INT430 SYSFexxx 0x00001001 MSFT
0x0100000c) @ 0x00000000
 17179569.184000  ACPI: PM-Timer IO Port: 0x808
 17179569.184000  Allocating PCI resources starting at 20000000 (gap:
10100000:efd00000)
 17179569.184000  Built 1 zonelists
 17179569.184000  Kernel command line: root=/dev/hda2 ro pci=noacpi
 17179569.184000  Local APIC disabled by BIOS (or by default) -- you
can enable it with "lapic"
 17179569.184000  mapped APIC to ffffd000 (01101000)
 17179569.184000  Initializing CPU#0
 17179569.184000  PID hash table entries: 512 (order: 9, 8192 bytes)
 17179569.184000  Detected 364.038 MHz processor.
 17179569.184000  Using pmtmr for high-res timesource
 17179569.184000  Console: colour VGA+ 80x25
 17179571.324000  Dentry cache hash table entries: 32768 (order: 5,
131072 bytes)
 17179571.324000  Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
 17179571.348000  Memory: 119348k/130992k available (1976k kernel
code, 11132k reserved, 606k data, 288k init, 0k highmem)
 17179571.348000  Checking if this processor honours the WP bit even
in supervisor mode... Ok.
 17179571.428000  Calibrating delay using timer specific routine..
728.76 BogoMIPS (lpj=1457530)
 17179571.428000  Security Framework v1.0.0 initialized
 17179571.428000  SELinux:  Disabled at boot.
 17179571.428000  Mount-cache hash table entries: 512
 17179571.428000  CPU: After generic identify, caps: 0183f9ff 00000000
00000000 00000000 00000000 00000000 00000000
 17179571.428000  CPU: After vendor identify, caps: 0183f9ff 00000000
00000000 00000000 00000000 00000000 00000000
 17179571.428000  CPU: L1 I cache: 16K, L1 D cache: 16K
 17179571.428000  CPU: L2 cache: 256K
 17179571.428000  CPU: After all inits, caps: 0183f9ff 00000000
00000000 00000040 00000000 00000000 00000000
 17179571.428000  mtrr: v2.0 (20020519)
 17179571.428000  CPU: Intel Mobile Pentium II stepping 0a
 17179571.428000  Enabling fast FPU save and restore... done.
 17179571.428000  Checking 'hlt' instruction... OK.
 17179571.444000  checking if image is initramfs... it is
 17179575.572000  Freeing initrd memory: 6617k freed
 17179575.632000  ACPI: Looking for DSDT ... not found!
 17179575.640000  ACPI: setting ELCR to 0a20 (from 0820)
 17179575.644000  NET: Registered protocol family 16
 17179575.644000  EISA bus registered
 17179575.644000  ACPI: bus type pci registered
 17179575.644000  PCI: PCI BIOS revision 2.10 entry at 0xfc0ee, last bus=1
 17179575.644000  PCI: Using configuration type 1
 17179575.648000  ACPI: Subsystem revision 20051216
 17179575.692000  ACPI: Interpreter enabled
 17179575.692000  ACPI: Using PIC for interrupt routing
 17179575.764000  ACPI: Power Resource  PADA  (on)
 17179575.764000  Linux Plug and Play Support v0.97 (c) Adam Belay
 17179575.764000  pnp: PnP ACPI init
 17179575.928000  pnp: PnP ACPI: found 14 devices
 17179575.928000  PnPBIOS: Disabled by ACPI PNP
 17179575.928000  PCI: Probing PCI hardware
 17179575.928000  PCI: Probing PCI hardware (bus 00)
 17179575.928000  ACPI: Assume root bridge  \_SB_.PCI0  bus is 0
 17179575.992000  PCI quirk: region 0800-083f claimed by PIIX4 ACPI
 17179575.992000  PCI quirk: region 0840-084f claimed by PIIX4 SMB
 17179575.992000  PIIX4 devres B PIO at 00e0-00e7
 17179575.992000  PIIX4 devres C PIO at 0850-085f
 17179575.992000  Boot video device is 0000:01:00.0
 17179576.112000  PCI: Using IRQ router PIIX/ICH  8086/7110  at 0000:00:07.0
 17179576.112000  PCI: IRQ 0 for device 0000:00:03.0 doesn't match
PIRQ mask - try pci=usepirqmask
 17179576.112000  PCI: Found IRQ 11 for device 0000:00:03.0
 17179576.112000  PCI: Sharing IRQ 11 with 0000:00:03.1
 17179576.112000  PCI: Sharing IRQ 11 with 0000:00:07.2
 17179576.144000  pnp: 00:01: ioport range 0x4d0-0x4d1 has been reserved
 17179576.144000  pnp: 00:01: ioport range 0x800-0x805 could not be reserved
 17179576.144000  pnp: 00:01: ioport range 0x808-0x80f could not be reserved
 17179576.144000  pnp: 00:02: ioport range 0x806-0x807 has been reserved
 17179576.144000  pnp: 00:02: ioport range 0x850-0x853 has been reserved
 17179576.144000  pnp: 00:02: ioport range 0x856-0x85f has been reserved
 17179576.144000  pnp: 00:02: ioport range 0x810-0x83f has been reserved
 17179576.144000  pnp: 00:02: ioport range 0x840-0x84f has been reserved
 17179576.144000  pnp: 00:03: ioport range 0xf400-0xf4fe has been reserved
 17179576.144000  pnp: 00:08: ioport range 0x3f0-0x3f1 has been reserved
 17179576.144000  PCI: Ignore bogus resource 6  0:0  of 0000:01:00.0
 17179576.144000  PCI: Bridge: 0000:00:01.0
 17179576.144000    IO window: c000-cfff
 17179576.144000    MEM window: fd000000-feffffff
 17179576.144000    PREFETCH window: f8000000-f9ffffff
 17179576.144000  PCI: Bus 2, cardbus bridge: 0000:00:03.0
 17179576.144000    IO window: 00001000-000010ff
 17179576.144000    IO window: 00001400-000014ff
 17179576.144000    PREFETCH window: 20000000-21ffffff
 17179576.144000    MEM window: 22000000-23ffffff
 17179576.144000  PCI: Bus 6, cardbus bridge: 0000:00:03.1
 17179576.144000    IO window: 00001800-000018ff
 17179576.144000    IO window: 00001c00-00001cff
 17179576.144000    PREFETCH window: 24000000-25ffffff
 17179576.148000    MEM window: 26000000-27ffffff
 17179576.148000  PCI: Enabling device 0000:00:03.0 (0000 -> 0003)
 17179576.148000  PCI: Found IRQ 11 for device 0000:00:03.0
 17179576.148000  PCI: Sharing IRQ 11 with 0000:00:03.1
 17179576.148000  PCI: Sharing IRQ 11 with 0000:00:07.2
 17179576.148000  PCI: Enabling device 0000:00:03.1 (0000 -> 0003)
 17179576.148000  PCI: Found IRQ 11 for device 0000:00:03.1
 17179576.148000  PCI: Sharing IRQ 11 with 0000:00:03.0
 17179576.148000  PCI: Sharing IRQ 11 with 0000:00:07.2
 17179576.148000  Simple Boot Flag at 0x79 set to 0x1
 17179576.148000  audit: initializing netlink socket (disabled)
 17179576.148000  audit(1169538190.148:1): initialized
 17179576.148000  VFS: Disk quotas dquot_6.5.1
 17179576.148000  Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
 17179576.152000  Initializing Cryptographic API
 17179576.152000  io scheduler noop registered
 17179576.152000  io scheduler anticipatory registered
 17179576.152000  io scheduler deadline registered
 17179576.152000  io scheduler cfq registered
 17179576.152000  Limiting direct PCI/PCI transfers.
 17179576.152000  isapnp: Scanning for PnP cards...
 17179576.504000  isapnp: No Plug & Play device found
 17179576.580000  PNP: PS/2 Controller  PNP0303:KBC,PNP0f13:PS2M  at
0x60,0x64 irq 1,12
 17179576.588000  serio: i8042 AUX port at 0x60,0x64 irq 12
 17179576.592000  serio: i8042 KBD port at 0x60,0x64 irq 1
 17179576.592000  Serial: 8250/16550 driver $Revision: 1.90 $ 48
ports, IRQ sharing enabled
 17179576.592000  serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
 17179576.600000  00:0c: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
 17179576.604000  RAMDISK driver initialized: 16 RAM disks of 65536K
size 1024 blocksize
 17179576.604000  Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
 17179576.604000  ide: Assuming 33MHz system bus speed for PIO modes;
override with idebus=xx
 17179576.604000  mice: PS/2 mouse device common for all mice
 17179576.604000  EISA: Probing bus 0 at eisa.0
 17179576.604000  Cannot allocate resource for EISA slot 1
 17179576.608000  EISA: Detected 0 cards.
 17179576.608000  NET: Registered protocol family 2
 17179576.620000  input: AT Translated Set 2 keyboard as /class/input/input0
 17179576.644000  IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
 17179576.644000  TCP established hash table entries: 8192 (order: 3,
32768 bytes)
 17179576.644000  TCP bind hash table entries: 8192 (order: 3, 32768 bytes)
 17179576.644000  TCP: Hash tables configured (established 8192 bind 8192)
 17179576.644000  TCP reno registered
 17179576.644000  TCP bic registered
 17179576.644000  NET: Registered protocol family 1
 17179576.644000  NET: Registered protocol family 8
 17179576.644000  NET: Registered protocol family 20
 17179576.644000  Using IPI Shortcut mode
 17179576.644000  ACPI wakeup devices:
 17179576.644000   LID PBTN PCI0 UAR1 MPCI
 17179576.644000  ACPI: (supports S0 S1 S3 S4 S5)
 17179576.644000  Freeing unused kernel memory: 288k freed
 17179576.896000  Capability LSM initialized
 17179577.080000  ACPI: CPU0 (power states: C1 C1  C2 C2 )
 17179577.116000  ACPI: Thermal Zone  THM  (26 C)
 17179579.208000  PIIX4: IDE controller at PCI slot 0000:00:07.1
 17179579.208000  PIIX4: chipset revision 1
 17179579.208000  PIIX4: not 100% native mode: will probe irqs later
 17179579.208000      ide0: BM-DMA at 0x0860-0x0867, BIOS settings:
hda:DMA, hdb:pio
 17179579.208000      ide1: BM-DMA at 0x0868-0x086f, BIOS settings:
hdc:pio, hdd:pio
 17179579.208000  Probing IDE interface ide0...
 17179579.500000  hda: TOSHIBA MK2018GAS, ATA DISK drive
 17179580.172000  ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
 17179580.652000  Probing IDE interface ide1...
 17179581.248000  hda: max request size: 128KiB
 17179581.252000  hda: 39070080 sectors (20003 MB), CHS=38760/16/63, UDMA(33)
 17179581.252000  hda: cache flushes supported
 17179581.252000   hda: hda1 hda2 hda3 < hda5 >
 17179582.040000  usbcore: registered new driver usbfs
 17179582.040000  usbcore: registered new driver hub
 17179582.052000  USB Universal Host Controller Interface driver v2.3
 17179582.052000  PCI: Found IRQ 11 for device 0000:00:07.2
 17179582.052000  PCI: Sharing IRQ 11 with 0000:00:03.0
 17179582.052000  PCI: Sharing IRQ 11 with 0000:00:03.1
 17179582.052000  uhci_hcd 0000:00:07.2: UHCI Host Controller
 17179582.052000  uhci_hcd 0000:00:07.2: new USB bus registered,
assigned bus number 1
 17179582.052000  uhci_hcd 0000:00:07.2: irq 11, io base 0x0000ece0
 17179582.056000  hub 1-0:1.0: USB hub found
 17179582.056000  hub 1-0:1.0: 2 ports detected
 17179582.236000  Probing IDE interface ide1...
 17179583.020000  Attempting manual resume
 17179583.136000  EXT3-fs: mounted filesystem with ordered data mode.
 17179583.140000  kjournald starting.  Commit interval 5 seconds
 17179601.856000  pci_hotplug: PCI Hot Plug PCI Core version: 0.5
 17179601.944000  shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
 17179601.980000  PCI: Found IRQ 11 for device 0000:00:03.0
 17179601.980000  PCI: Sharing IRQ 11 with 0000:00:03.1
 17179601.980000  PCI: Sharing IRQ 11 with 0000:00:07.2
 17179601.980000  Yenta: CardBus bridge found at 0000:00:03.0  1028:0088 
 17179601.980000  Yenta: Using CSCINT to route CSC interrupts to PCI
 17179601.980000  Yenta: Routing CardBus interrupts to PCI
 17179601.980000  Yenta TI: socket 0000:00:03.0, mfunc 0x01261222, devctl 0x66
 17179601.988000  Linux agpgart interface v0.101 (c) Dave Jones
 17179602.008000  agpgart: Detected an Intel 440BX Chipset.
 17179602.016000  agpgart: AGP aperture is 64M @ 0xf4000000
 17179602.212000  Yenta: ISA IRQ mask 0x0498, PCI irq 11
 17179602.212000  Socket status: 30000006
 17179602.232000  PCI: Found IRQ 11 for device 0000:00:03.1
 17179602.232000  PCI: Sharing IRQ 11 with 0000:00:03.0
 17179602.232000  PCI: Sharing IRQ 11 with 0000:00:07.2
 17179602.232000  Yenta: CardBus bridge found at 0000:00:03.1  1028:0088 
 17179602.232000  Yenta: Using CSCINT to route CSC interrupts to PCI
 17179602.232000  Yenta: Routing CardBus interrupts to PCI
 17179602.232000  Yenta TI: socket 0000:00:03.1, mfunc 0x01261222, devctl 0x66
 17179602.464000  Yenta: ISA IRQ mask 0x0498, PCI irq 11
 17179602.464000  Socket status: 30000006
 17179603.228000  piix4_smbus 0000:00:07.3: Found 0000:00:07.3 device
 17179603.356000  input: PC Speaker as /class/input/input1
 17179604.088000  Synaptics Touchpad, model: 1, fw: 4.2, id: 0x844a1,
caps: 0x0/0x0
 17179604.148000  input: SynPS/2 Synaptics TouchPad as /class/input/input2
 17179605.432000  Floppy drive(s): fd0 is 1.44M
 17179605.448000  FDC 0 is a post-1991 82077
 17179605.596000  cs: IO port probe 0x100-0x3af: excluding 0x170-0x177
0x370-0x37f
 17179605.596000  cs: IO port probe 0x3e0-0x4ff: clean.
 17179605.596000  cs: IO port probe 0x820-0x8ff: clean.
 17179605.596000  cs: IO port probe 0xc00-0xcf7: clean.
 17179605.600000  cs: IO port probe 0xa00-0xaff: clean.
 17179605.776000  Real Time Clock Driver v1.12
 17179605.896000  ts: Compaq touchscreen protocol output
 17179605.952000  PCI: Enabling device 0000:01:00.1 (0000 -> 0002)
 17179605.952000  PCI: Found IRQ 5 for device 0000:01:00.1
 17179605.952000  nm256: found card signature in video RAM: 0x27ec00
 17179605.952000  nm256: Mapping port 1 from 0x2709a0 - 0x27ec00
 17179606.208000  cs: IO port probe 0x100-0x3af: excluding 0x170-0x177
0x370-0x37f
 17179606.212000  cs: IO port probe 0x3e0-0x4ff: clean.
 17179606.212000  cs: IO port probe 0x820-0x8ff: clean.
 17179606.212000  cs: IO port probe 0xc00-0xcf7: clean.
 17179606.212000  cs: IO port probe 0xa00-0xaff: clean.
 17179606.244000  parport: PnPBIOS parport detected.
 17179606.244000  parport0: PC-style at 0x378 (0x778), irq 7, dma 3
 PCSPP,TRISTATE,COMPAT,ECP,DMA 
 17179608.800000  lp0: using parport0 (interrupt-driven).
 17179609.072000  Adding 489940k swap on /dev/hda5.  Priority:-1
extents:1 across:489940k
 17179609.196000  EXT3 FS on hda2, internal journal
 17179609.760000  md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
 17179609.760000  md: bitmap version 4.39
 17179610.944000  device-mapper: 4.4.0-ioctl (2005-01-12) initialised:
dm-devel@redhat.com
 17179612.692000  NTFS driver 2.1.25  Flags: R/O MODULE .
 17179612.820000  NTFS volume version 3.1.
 17179614.552000  NET: Registered protocol family 17
```

---

