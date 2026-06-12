---
title: "Dell 1350 wireless lan card assistance"
date: 2005-08-11
forum: Hardware &amp; Laptops
---

### Post by dizbah on 2005-08-11
Hello everyone.

I am completely new to linux and am trying despertely to get my dell wireless 1350 card to work.  I know there is a way to make it work using the windows driver.  I down loaded the driver and tried to run it in terminal but it is not working.  Can someone please assist me and tell me what to do?  Screen shots would be great but I'll take whatever I can get.  

Thank you

---

### Post by fxalpha on 2005-08-12
insert the card and type "dmesg" at a command line / in a terminal. it'lll feed you loads of details of what's happened lately and at the bottom it should tell you what it knows about your card. as long as it doesn't say anything bad you should be cool to follow the steps below.

you need the win drivers and the ndiswrapper package. There are guides in these forums that will show you the exact details. I don't have a link so you'll need to look for them. Check for a proper guide, here's a quickie:

* install ndiswrapper (on hoary cd / downloadable)
* unzip windows drivers to a folder (remember where)
* open console
 - "cd /where/youput/driver"
 - "sudo ndiswrapper -i *driver*" ( my driver is called net12220.inf so i typed "ndiswrapper -i neti2220.inf")
 - "sudo ndiswrapper -l" (should tell you driver name and say driver and hardware are present)
 - "sudo modprobe ndiswrapper" (tell kernel to use ndiswrapper as a module)
 - "sudo iwlist wlan0 scan" (iwlist will scan for networks using wlan0 and display any found)

if all goes well (no errors, good feedback) then
 - "sudo ndiswrapper -m" will add it to startup

you can then go to system -> administration -> networking and enter the details requested. you'll see a dropdown at the bottom of the dialog box that appears - set this to what you want default connection to use. I was so into getting ndiswrapper to work i left this set at eth0 and nearly bust a vein over wlan) not working!

---

### Post by dizbah on 2005-08-12
I downloaded the windows driver and am stuck on the following point:

when entering the sudo ndiswrapper -l command:

Installed ndis drivers:
bcmw15a invalid driver!
bcmwl5  invalid driver!
bcmwl5a invalid driver!
desktop invalid driver!


The card is showing under device manager though but not in network properties.  Please help!

---

### Post by fxalpha on 2005-08-13
Are you using hoary? in 386/amd64? did you install ndiswrapper from source or using synaptic/apt?

---

### Post by dizbah on 2005-08-13
yes to all

---

### Post by fxalpha on 2005-08-14
so you got hoary, is it 32bit or 64bit version? Did you download the source code and compile ndiswrapper yourself or did you download and install using the package manager program in gnome? When you got the windows drivers were they 32 bit only or did it have versions for both?
Am I right in thinking its a PCMCIA card? Do you know PCMCIA is working?
If so, plug in the card and open a terminal/command line and type "dmesg" look and see at the bottom what it has to say.

---

### Post by dizbah on 2005-08-19
Linux version 2.6.10-5-686-smp (buildd@vernadsky) (gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)) #1 SMP Fri Jun 24 18:12:58 UTC 2005
BIOS-provided physical RAM map:
 BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
 BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
 BIOS-e820: 0000000000100000 - 000000001f7d3800 (usable)
 BIOS-e820: 000000001f7d3800 - 0000000020000000 (reserved)
 BIOS-e820: 00000000e0000000 - 00000000f0007000 (reserved)
 BIOS-e820: 00000000f0008000 - 00000000f000c000 (reserved)
 BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
 BIOS-e820: 00000000fed20000 - 00000000fee10000 (reserved)
 BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
0MB HIGHMEM available.
503MB LOWMEM available.
On node 0 totalpages: 128979
  DMA zone: 4096 pages, LIFO batch:1
  Normal zone: 124883 pages, LIFO batch:16
  HighMem zone: 0 pages, LIFO batch:1
DMI 2.3 present.
ACPI: RSDP (v000 DELL                                  ) @ 0x000fc9b0
ACPI: RSDT (v001 DELL    CPi R   0x27d50217 ASL  0x00000061) @ 0x1f7d3fd3
ACPI: FADT (v001 DELL    CPi R   0x27d50217 ASL  0x00000061) @ 0x1f7d4c00
ACPI: MADT (v001 DELL    CPi R   0x27d50217 ASL  0x00000047) @ 0x1f7d5400
ACPI: MCFG (v016 DELL    CPi R   0x27d50217 ASL  0x00000061) @ 0x1f7d53c0
ACPI: BOOT (v001 DELL    CPi R   0x27d50217 ASL  0x00000061) @ 0x1f7d4fc0
ACPI: SSDT (v001  PmRef  Cpu0Ist 0x00003000 INTL 0x20030522) @ 0x1f7d43e6
ACPI: SSDT (v001  PmRef  Cpu0Cst 0x00003001 INTL 0x20030522) @ 0x1f7d420e
ACPI: SSDT (v001  PmRef    CpuPm 0x00003000 INTL 0x20030522) @ 0x1f7d4013
ACPI: DSDT (v001 INT430 SYSFexxx 0x00001001 MSFT 0x0100000e) @ 0x00000000
ACPI: PM-Timer IO Port: 0x1008
ACPI: Local APIC address 0xfee00000
ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Processor #0 6:13 APIC version 20
ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
ACPI: IRQ0 used by override.
ACPI: IRQ2 used by override.
ACPI: IRQ9 used by override.
Enabling APIC mode:  Flat.  Using 1 I/O APICs
Using ACPI (MADT) for SMP configuration information
Built 1 zonelists
Kernel command line: root=/dev/sda2 ro quiet splash
mapped APIC to ffffd000 (fee00000)
mapped IOAPIC to ffffc000 (fec00000)
Initializing CPU#0
PID hash table entries: 2048 (order: 11, 32768 bytes)
Detected 1496.352 MHz processor.
Using pmtmr for high-res timesource
Console: colour VGA+ 80x25
Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
Memory: 503304k/515916k available (1604k kernel code, 12072k reserved, 719k data, 192k init, 0k highmem)
Checking if this processor honours the WP bit even in supervisor mode... Ok.
Calibrating delay loop... 2949.12 BogoMIPS (lpj=1474560)
Security Framework v1.0.0 initialized
SELinux:  Disabled at boot.
Mount-cache hash table entries: 512 (order: 0, 4096 bytes)
CPU: After generic identify, caps: afe9fbff 00100000 00000000 00000000 00000180 00000000
CPU: After vendor identify, caps: afe9fbff 00100000 00000000 00000000 00000180 00000000
CPU: L1 I cache: 32K, L1 D cache: 32K
CPU: L2 cache: 2048K
CPU: After all inits, caps: afe9fbff 00100000 00000000 00000040 00000180 00000000
Intel machine check architecture supported.
Intel machine check reporting enabled on CPU#0.
Enabling fast FPU save and restore... done.
Enabling unmasked SIMD FPU exception support... done.
Checking 'hlt' instruction... OK.
ACPI: Looking for DSDT in initrd... not found!
CPU0: Intel(R) Pentium(R) M processor 1.50GHz stepping 08
per-CPU timeslice cutoff: 5851.67 usecs.
task migration cache decay timeout: 6 msecs.
Total of 1 processors activated (2949.12 BogoMIPS).
ENABLING IO-APIC IRQs
..TIMER: vector=0x31 pin1=2 pin2=-1
Brought up 1 CPUs
CPU0:
 domain 0: span 01
  groups: 01
  domain 1: span 01
   groups: 01
checking if image is initramfs...it isn't (bad gzip magic numbers); looks like an initrd
Freeing initrd memory: 4556k freed
NET: Registered protocol family 16
PCI: PCI BIOS revision 2.10 entry at 0xfbaae, last bus=4
PCI: Using MMCONFIG
mtrr: v2.0 (20020519)
ACPI: Subsystem revision 20050211
ACPI: Interpreter enabled
ACPI: Using IOAPIC for interrupt routing
ACPI: PCI Root Bridge [PCI0] (00:00)
PCI: Probing PCI hardware (bus 00)
PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.2
PCI: Transparent bridge - 0000:00:1e.0
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *10
ACPI: PCI Interrupt Link [LNKC] (IRQs *9 10 11)
ACPI: PCI Interrupt Link [LNKD] (IRQs 5 *7 9 10 11)
ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
Linux Plug and Play Support v0.97 (c) Adam Belay
pnp: PnP ACPI init
pnp: PnP ACPI: found 11 devices
PnPBIOS: Disabled by ACPI PNP
PCI: Using ACPI for IRQ routing
** PCI interrupts are no longer routed automatically.  If this
** causes a device to stop working, it is probably because the
** driver failed to call pci_enable_device().  As a temporary
** workaround, the "pci=routeirq" argument restores the old
** behavior.  If this argument makes the device work again,
** please email the output of "lspci" to [email]bjorn.helgaas@hp.com[/email]
** so I can fix the driver.
pnp: 00:01: ioport range 0x4d0-0x4d1 has been reserved
pnp: 00:01: ioport range 0x1000-0x1005 could not be reserved
pnp: 00:01: ioport range 0x1008-0x100f could not be reserved
pnp: 00:02: ioport range 0xf400-0xf4fe has been reserved
pnp: 00:02: ioport range 0x1006-0x1007 has been reserved
pnp: 00:02: ioport range 0x100a-0x1059 could not be reserved
pnp: 00:02: ioport range 0x1060-0x107f has been reserved
pnp: 00:02: ioport range 0x1080-0x10bf has been reserved
pnp: 00:02: ioport range 0x10c0-0x10df has been reserved
pnp: 00:07: ioport range 0x900-0x90f has been reserved
pnp: 00:07: ioport range 0x910-0x91f has been reserved
pnp: 00:07: ioport range 0x920-0x92f has been reserved
pnp: 00:07: ioport range 0x930-0x93f has been reserved
pnp: 00:07: ioport range 0x940-0x97f has been reserved
pnp: 00:0a: ioport range 0x7b0-0x7bb has been reserved
pnp: 00:0a: ioport range 0x7c0-0x7df has been reserved
pnp: 00:0a: ioport range 0xbb0-0xbbb has been reserved
pnp: 00:0a: ioport range 0xbc0-0xbdf has been reserved
pnp: 00:0a: ioport range 0xfb0-0xfbb has been reserved
pnp: 00:0a: ioport range 0xfc0-0xfdf has been reserved
pnp: 00:0a: ioport range 0x13b0-0x13bb has been reserved
pnp: 00:0a: ioport range 0x13c0-0x13df has been reserved
Simple Boot Flag at 0x79 set to 0x1
audit: initializing netlink socket (disabled)
audit(1124474785.388:0): initialized
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
ACPI: PCI interrupt 0000:00:1e.3[B] -> GSI 17 (level, low) -> IRQ 17
io scheduler noop registered
io scheduler anticipatory registered
io scheduler deadline registered
io scheduler cfq registered
RAMDISK driver initialized: 16 RAM disks of 8192K size 1024 blocksize
input: AT Translated Set 2 keyboard on isa0060/serio0
NET: Registered protocol family 2
IP: routing cache hash table of 4096 buckets, 32Kbytes
TCP: Hash tables configured (established 32768 bind 32768)
NET: Registered protocol family 8
NET: Registered protocol family 20
Restarting tasks...<6> Strange, kswapd0 not stopped
 Strange, kseriod not stopped
 done
ACPI wakeup devices:
 LID PBTN PCI0 USB0 USB1 USB2 USB4 USB3 MODM PCIE
ACPI: (supports S0 S3 S4 S4bios S5)
RAMDISK: cramfs filesystem found at block 0
RAMDISK: Loading 4556KiB [1 disk] into ram disk... done.
VFS: Mounted root (cramfs filesystem) readonly.
Freeing unused kernel memory: 192k freed
ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3] C4[C3])
ACPI: Processor [CPU0] (supports 8 throttling states)
ACPI: Thermal Zone [THM] (42 C)
NET: Registered protocol family 1
SCSI subsystem initialized
libata version 1.10 loaded.
ata_piix version 1.03
ACPI: PCI interrupt 0000:00:1f.2[B] -> GSI 17 (level, low) -> IRQ 17
PCI: Setting latency timer of device 0000:00:1f.2 to 64
ata1: SATA max UDMA/133 cmd 0x1F0 ctl 0x3F6 bmdma 0xBFA0 irq 14
ata1: dev 0 cfg 49:0f00 82:746b 83:7fe8 84:4023 85:f469 86:3c48 87:4023 88:203f
ata1: dev 0 ATA, max UDMA/100, 58605120 sectors: lba48
ata1(0): applying bridge limits
ata1: dev 0 configured for UDMA/100
scsi0 : ata_piix
elevator: using anticipatory as default io scheduler
  Vendor: ATA       Model: Hitachi HTS42403  Rev: MAAO
  Type:   Direct-Access                      ANSI SCSI revision: 05
ata2: SATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xBFA8 irq 15
ata2: dev 0 cfg 49:0b00 82:0000 83:0000 84:0000 85:0000 86:0000 87:0000 88:0407
ata2: dev 0 ATAPI, max UDMA/33
ata2: dev 0 configured for UDMA/33
scsi1 : ata_piix
  Vendor: _NEC      Model: DVD+-RW ND-6500A  Rev: 202C
  Type:   CD-ROM                             ANSI SCSI revision: 05
Attached scsi generic sg0 at scsi0, channel 0, id 0, lun 0,  type 0
Attached scsi generic sg1 at scsi1, channel 0, id 0, lun 0,  type 5
SCSI device sda: 58605120 512-byte hdwr sectors (30006 MB)
SCSI device sda: drive cache: write back
SCSI device sda: 58605120 512-byte hdwr sectors (30006 MB)
SCSI device sda: drive cache: write back
 /dev/scsi/host0/bus0/target0/lun0: p1 p2 p3 < p5 >
Attached scsi disk sda at scsi0, channel 0, id 0, lun 0
sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
Uniform CD-ROM driver Revision: 3.20
Attached scsi CD-ROM sr0 at scsi1, channel 0, id 0, lun 0
Stopping tasks: ==|
Freeing memory... done (435 pages freed)
Restarting tasks... done
EXT3-fs: mounted filesystem with ordered data mode.
kjournald starting.  Commit interval 5 seconds
Adding 1004020k swap on /dev/sda5.  Priority:-1 extents:1
EXT3 FS on sda2, internal journal
lp: driver loaded but no devices found
mice: PS/2 mouse device common for all mice
input: PS/2 Generic Mouse on isa0060/serio1
ieee1394: Initialized config rom entry `ip1394'
sbp2: $Rev: 1219 $ Ben Collins <bcollins@debian.org>
Capability LSM initialized
device-mapper: 4.3.0-ioctl (2004-09-30) initialised: [email]dm-devel@redhat.com[/email]
md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
ts: Compaq touchscreen protocol output
cdrom: open failed.
Real Time Clock Driver v1.12
input: PC Speaker
Linux agpgart interface v0.100 (c) Dave Jones
agpgart: Detected an Intel 915GM Chipset.
agpgart: Maximum main memory to use for agp memory: 431M
agpgart: Detected 7932K stolen memory.
agpgart: AGP aperture is 256M @ 0xc0000000
usbcore: registered new driver usbfs
usbcore: registered new driver hub
USB Universal Host Controller Interface driver v2.2
ACPI: PCI interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
uhci_hcd 0000:00:1d.0: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1
PCI: Setting latency timer of device 0000:00:1d.0 to 64
uhci_hcd 0000:00:1d.0: irq 16, io base 0xbf80
uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:1d.1[B] -> GSI 17 (level, low) -> IRQ 17
uhci_hcd 0000:00:1d.1: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2
PCI: Setting latency timer of device 0000:00:1d.1 to 64
uhci_hcd 0000:00:1d.1: irq 17, io base 0xbf60
uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
uhci_hcd 0000:00:1d.2: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3
PCI: Setting latency timer of device 0000:00:1d.2 to 64
uhci_hcd 0000:00:1d.2: irq 18, io base 0xbf40
uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
hub 3-0:1.0: USB hub found
hub 3-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:1d.3[D] -> GSI 19 (level, low) -> IRQ 19
uhci_hcd 0000:00:1d.3: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4
PCI: Setting latency timer of device 0000:00:1d.3 to 64
uhci_hcd 0000:00:1d.3: irq 19, io base 0xbf20
uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
hub 4-0:1.0: USB hub found
hub 4-0:1.0: 2 ports detected
usb 4-2: new low speed USB device using uhci_hcd and address 2
ACPI: PCI interrupt 0000:00:1d.7[A] -> GSI 16 (level, low) -> IRQ 16
ehci_hcd 0000:00:1d.7: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller
PCI: Setting latency timer of device 0000:00:1d.7 to 64
ehci_hcd 0000:00:1d.7: irq 16, pci mem 0xffa80800
ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
PCI: cache line size of 32 is not supported by device 0000:00:1d.7
ehci_hcd 0000:00:1d.7: USB 2.0 initialized, EHCI 1.00, driver 26 Oct 2004
hub 5-0:1.0: USB hub found
hub 5-0:1.0: 8 ports detected
hw_random: cannot enable RNG, aborting
usbcore: registered new driver hiddev
usbhid: probe of 4-2:1.0 failed with error -5
usbcore: registered new driver usbhid
drivers/usb/input/hid-core.c: v2.0:USB HID core driver
usb 4-2: USB disconnect, address 2
usb 4-2: new low speed USB device using uhci_hcd and address 3
input: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:1d.3-2
ACPI: PCI interrupt 0000:00:1e.2[A] -> GSI 16 (level, low) -> IRQ 16
PCI: Setting latency timer of device 0000:00:1e.2 to 64
intel8x0_measure_ac97_clock: measured 54470 usecs
intel8x0: clocking to 48000
b44.c:v0.95 (Aug 3, 2004)
ACPI: PCI interrupt 0000:03:00.0[A] -> GSI 18 (level, low) -> IRQ 18
eth0: Broadcom 4400 10/100BaseT Ethernet 00:11:43:72:68:53
Linux Kernel Card Services
  options:  [pci] [cardbus] [pm]
PCI: Enabling device 0000:03:01.0 (0000 -> 0002)
ACPI: PCI interrupt 0000:03:01.0[A] -> GSI 19 (level, low) -> IRQ 19
Yenta: CardBus bridge found at 0000:03:01.0 [1028:0188]
Yenta: ISA IRQ mask 0x04b8, PCI irq 19
Socket status: 30000006
ohci1394: $Rev: 1223 $ Ben Collins <bcollins@debian.org>
ACPI: PCI interrupt 0000:03:01.1[B] -> GSI 18 (level, low) -> IRQ 18
ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[dfdfb800-dfdfbfff]  Max Packet=[2048]
b44: eth0: Link is down.
NET: Registered protocol family 17
ieee1394: Host added: ID:BUS[0-00:1023]  GUID[364fc0001e2df8c1]
b44: eth0: Link is up at 100 Mbps, full duplex.
b44: eth0: Flow control is on for TX and on for RX.
NET: Registered protocol family 10
Disabled Privacy Extensions on device c0317e40(lo)
IPv6 over IPv4 tunneling driver
ACPI: AC Adapter [AC] (on-line)
ACPI: Battery Slot [BAT0] (battery present)
ACPI: Lid Switch [LID]
ACPI: Power Button (CM) [PBTN]
ACPI: Sleep Button (CM) [SBTN]
ibm_acpi: ec object not found
ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)
[drm] Initialized drm 1.0.0 20040925
ACPI: PCI interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[drm] Initialized i915 1.2.0 20040405 on minor 0: Intel Corp. Mobile Graphics Controller
mtrr: base(0xc0020000) is not aligned on a size(0x834000) boundary
apm: BIOS not found.
cs: IO port probe 0x0100-0x04ff: excluding 0x370-0x377 0x3f0-0x3f7
cs: IO port probe 0x0800-0x08ff: clean.
cs: IO port probe 0x0c00-0x0cff: excluding 0xcf8-0xcff
cs: IO port probe 0x0a00-0x0aff: clean.
eth0: no IPv6 routers present
atkbd.c: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
atkbd.c: Use 'setkeycodes e008 <keycode>' to make it known.
atkbd.c: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
atkbd.c: Use 'setkeycodes e008 <keycode>' to make it known.
ndiswrapper version 1.0rc2 loaded (preempt=yes,smp=yes)
ndiswrapper (wrapper_init:1494): loadndiswrapper failed (1792); check system log for messages from 'loadndisdriver'
ndiswrapper version 1.0rc2 loaded (preempt=yes,smp=yes)
ndiswrapper (wrapper_init:1494): loadndiswrapper failed (1792); check system log for messages from 'loadndisdriver'

---

### Post by jasongrieves on 2005-09-17
just had to say THANKS for this quick install method.  Had not used ndiswrappers for about 5 years.  What a joy it is to see progress on so many levels on Linux.  I am on a laptop, i hot unplugged from my port replicaator to get a hard wire connection for updates and to see this post, my battery icon starts.  I then grab my win driver from dell, grab ndiswrapper, wrap the sucker, run the gui, and bam, I have wirleess internet with linux.  throw my computer back into the replicator, my power goes fine, my usb mouse gets auto detected and loads up.  Scrolling works with it also.  Thanks again for the great post

---

### Post by tackleberry61 on 2007-09-24
I  am completely new to linux, and also cannot get my wireless card to work, and when I type "dmesg" i get this message:

[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   131017
[    0.000000]   HighMem    131017 ->   131017
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   131017
[    0.000000] On node 0 totalpages: 131017
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 991 pages used for memmap
[    0.000000]   Normal zone: 125930 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v000 DELL                                  ) @ 0x000fdf00
[    0.000000] ACPI: RSDT (v001 DELL    CPi R   0x27d30813 ASL  0x00000061) @ 0x1fff0000
[    0.000000] ACPI: FADT (v001 DELL    CPi R   0x27d30813 ASL  0x00000061) @ 0x1fff0400
[    0.000000] ACPI: DSDT (v001 INT430 SYSFexxx 0x00001001 MSFT 0x0100000e) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:deda0000)
[    0.000000] Detected 2392.208 MHz processor.
[    7.340179] Built 1 zonelists.  Total pages: 129994
[    7.340186] Kernel command line: root=UUID=80283bbc-8ea7-4930-a9a1-7952a8b6d3f0 ro quiet splash
[    7.340368] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    7.340381] mapped APIC to ffffd000 (0140b000)
[    7.340385] Enabling fast FPU save and restore... done.
[    7.340388] Enabling unmasked SIMD FPU exception support... done.
[    7.340406] Initializing CPU#0
[    7.340512] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    7.341906] Console: colour VGA+ 80x25
[    7.342415] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[    7.342833] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[    7.355290] Memory: 508472k/524068k available (1993k kernel code, 14984k reserved, 900k data, 328k init, 0k highmem)
[    7.355301] virtual kernel memory layout:
[    7.355303]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[    7.355304]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    7.355305]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
[    7.355306]     lowmem  : 0xc0000000 - 0xdffc9000   ( 511 MB)
[    7.355308]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[    7.355309]       .data : 0xc02f2434 - 0xc03d36d4   ( 900 kB)
[    7.355310]       .text : 0xc0100000 - 0xc02f2434   (1993 kB)
[    7.355314] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    7.432505] Calibrating delay using timer specific routine.. 4788.20 BogoMIPS (lpj=9576407)
[    7.432555] Security Framework v1.0.0 initialized
[    7.432563] SELinux:  Disabled at boot.
[    7.432582] Mount-cache hash table entries: 512
[    7.432752] CPU: After generic identify, caps: bfebf9ff 00000000 00000000 00000000 00004400 00000000 00000000
[    7.432766] CPU: Trace cache: 12K uops, L1 D cache: 8K
[    7.432769] CPU: L2 cache: 512K
[    7.432772] CPU: Hyper-Threading is disabled
[    7.432775] CPU: After all inits, caps: bfebf9ff 00000000 00000000 00003080 00004400 00000000 00000000
[    7.432788] Compat vDSO mapped to ffffe000.
[    7.432792] Remapping vsyscall page to ffffe000
[    7.432806] Checking 'hlt' instruction... OK.
[    7.448610] SMP alternatives: switching to UP code
[    7.448841] Freeing SMP alternatives: 11k freed
[    7.449085] Early unpacking initramfs... done
[    7.772313] ACPI: Core revision 20060707
[    7.781097] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[    7.782343] ACPI: setting ELCR to 0200 (from 0800)
[    7.783770] CPU0: Intel(R) Pentium(R) 4 CPU 2.40GHz stepping 09
[    7.783777] SMP motherboard not detected.
[    7.783780] Local APIC not detected. Using dummy APIC emulation.
[    7.783823] Brought up 1 CPUs
[    7.784121] Booting paravirtualized kernel on bare hardware
[    7.784192] Time: 21:00:38  Date: 08/24/107
[    7.784232] NET: Registered protocol family 16
[    7.784344] EISA bus registered
[    7.784350] ACPI: bus type pci registered
[    7.835887] PCI: PCI BIOS revision 2.10 entry at 0xfcfae, last bus=2
[    7.835890] PCI: Using configuration type 1
[    7.835892] Setting up standard PCI resources
[    7.849463] ACPI: Interpreter enabled
[    7.849467] ACPI: Using PIC for interrupt routing
[    7.850156] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    7.850166] PCI: Probing PCI hardware (bus 00)
[    7.850255] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[    7.855849] * The chipset may have PM-Timer Bug. Due to workarounds for a bug,
[    7.855851] * this clock source is slow. If you are sure your timer does not have
[    7.855853] * this bug, please use "acpi_pm_good" to disable the workaround
[    7.855901] PCI quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
[    7.855905] PCI quirk: region 0880-08bf claimed by ICH4 GPIO
[    7.856161] Boot video device is 0000:01:00.0
[    7.856415] PCI: Transparent bridge - 0000:00:1e.0
[    7.856520] PCI: Bus #03 (-#06) is hidden behind transparent bridge #02 (-#02) (try 'pci=assign-busses')
[    7.856522] Please report the result to linux-kernel to fix this permanently
[    7.856546] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    7.865917] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
[    7.866191] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *11
[    7.866460] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 *11)
[    7.866728] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 *11)
[    7.867000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    7.867274] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    7.867730] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    7.868774] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[    7.869134] Linux Plug and Play Support v0.97 (c) Adam Belay
[    7.869149] pnp: PnP ACPI init
[    7.881049] pnp: PnP ACPI: found 11 devices
[    7.881056] PnPBIOS: Disabled by ACPI PNP
[    7.881128] PCI: Using ACPI for IRQ routing
[    7.881132] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    7.888543] NET: Registered protocol family 8
[    7.888546] NET: Registered protocol family 20
[    7.893993] pnp: 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    7.893997] pnp: 00:02: ioport range 0x800-0x805 could not be reserved
[    7.894000] pnp: 00:02: ioport range 0x808-0x80f could not be reserved
[    7.894006] pnp: 00:03: ioport range 0xf400-0xf4fe has been reserved
[    7.894009] pnp: 00:03: ioport range 0x806-0x807 has been reserved
[    7.894012] pnp: 00:03: ioport range 0x810-0x85f could not be reserved
[    7.894015] pnp: 00:03: ioport range 0x860-0x87f has been reserved
[    7.894017] pnp: 00:03: ioport range 0x880-0x8bf has been reserved
[    7.894020] pnp: 00:03: ioport range 0x8c0-0x8df has been reserved
[    7.894029] pnp: 00:08: ioport range 0x900-0x97f has been reserved
[    7.894382] PCI: Bridge: 0000:00:01.0
[    7.894386]   IO window: c000-cfff
[    7.894392]   MEM window: fc000000-fdffffff
[    7.894396]   PREFETCH window: e8000000-efffffff
[    7.894407] PCI: Bus 3, cardbus bridge: 0000:02:04.0
[    7.894409]   IO window: 0000d000-0000d0ff
[    7.894414]   IO window: 0000d400-0000d4ff
[    7.894418]   PREFETCH window: 30000000-33ffffff
[    7.894423]   MEM window: 38000000-3bffffff
[    7.894427] PCI: Bridge: 0000:00:1e.0
[    7.894430]   IO window: d000-efff
[    7.894436]   MEM window: f6000000-fbffffff
[    7.894441]   PREFETCH window: 30000000-33ffffff
[    7.894461] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    7.894477] PCI: Enabling device 0000:02:04.0 (0000 -> 0003)
[    7.894683] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[    7.894687] PCI: setting IRQ 11 as level-triggered
[    7.894690] ACPI: PCI Interrupt 0000:02:04.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[    7.894734] NET: Registered protocol family 2
[    7.928533] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    7.928647] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    7.928769] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    7.928829] TCP: Hash tables configured (established 16384 bind 8192)
[    7.928832] TCP reno registered
[    7.940574] checking if image is initramfs... it is
[    8.577430] Freeing initrd memory: 6782k freed
[    8.577949] audit: initializing netlink socket (disabled)
[    8.577969] audit(1190667638.424:1): initialized
[    8.578144] VFS: Disk quotas dquot_6.5.1
[    8.578170] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    8.578237] io scheduler noop registered
[    8.578241] io scheduler anticipatory registered
[    8.578243] io scheduler deadline registered
[    8.578254] io scheduler cfq registered (default)
[    8.578602] isapnp: Scanning for PnP cards...
[    8.931586] isapnp: No Plug & Play device found
[    8.962132] Real Time Clock Driver v1.12ac
[    8.962199] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    8.963193] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 7
[    8.963198] PCI: setting IRQ 7 as level-triggered
[    8.963202] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 7 (level, low) -> IRQ 7
[    8.963211] ACPI: PCI interrupt for device 0000:00:1f.6 disabled
[    8.963305] mice: PS/2 mouse device common for all mice
[    8.964003] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    8.964192] input: Macintosh mouse button emulation as /class/input/input0
[    8.964242] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    8.964246] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    8.964492] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    8.964645] i8042.c: Warning: Keylock active.
[    8.967163] serio: i8042 KBD port at 0x60,0x64 irq 1
[    8.967168] serio: i8042 AUX port at 0x60,0x64 irq 12
[    8.967306] EISA: Probing bus 0 at eisa.0
[    8.967337] EISA: Detected 0 cards.
[    8.997455] TCP cubic registered
[    8.997465] NET: Registered protocol family 1
[    8.997494] Using IPI No-Shortcut mode
[    8.997599] ACPI: (supports S0 S1 S3 S4 S5)
[    8.997660]   Magic number: 7:13:46
[    8.997667]   hash matches device ttyef
[    8.998341] Freeing unused kernel memory: 328k freed
[    8.999077] input: AT Translated Set 2 keyboard as /class/input/input1
[    9.000274] Time: tsc clocksource has been installed.
[   10.247841] Capability LSM initialized
[   10.292012] ACPI: Processor [CPU0] (supports 8 throttling states)
[   10.295918] ACPI: Thermal Zone [THM] (37 C)
[   10.971655] usbcore: registered new interface driver usbfs
[   10.971687] usbcore: registered new interface driver hub
[   10.971714] usbcore: registered new device driver usb
[   10.972849] USB Universal Host Controller Interface driver v3.0
[   10.972918] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   10.972932] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   10.972937] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   10.973098] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   10.973126] uhci_hcd 0000:00:1d.0: irq 11, io base 0x0000bf80
[   10.973249] usb usb1: configuration #1 chosen from 1 choice
[   10.973280] hub 1-0:1.0: USB hub found
[   10.973288] hub 1-0:1.0: 2 ports detected
[   11.076446] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[   11.076452] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[   11.076466] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   11.076470] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   11.076503] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   11.076530] uhci_hcd 0000:00:1d.1: irq 11, io base 0x0000bf40
[   11.076638] usb usb2: configuration #1 chosen from 1 choice
[   11.076671] hub 2-0:1.0: USB hub found
[   11.076683] hub 2-0:1.0: 2 ports detected
[   11.092207] ieee1394: Initialized config rom entry `ip1394'
[   11.180407] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[   11.180413] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[   11.180426] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   11.180431] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   11.180466] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   11.180493] uhci_hcd 0000:00:1d.2: irq 11, io base 0x0000bf20
[   11.180596] usb usb3: configuration #1 chosen from 1 choice
[   11.180624] hub 3-0:1.0: USB hub found
[   11.180632] hub 3-0:1.0: 2 ports detected
[   11.286484] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
[   11.286491] ACPI: PCI Interrupt 0000:00:1d.7[D] -> Link [LNKH] -> GSI 11 (level, low) -> IRQ 11
[   11.286510] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   11.286515] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   11.286572] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[   11.286622] ehci_hcd 0000:00:1d.7: debug port 1
[   11.286630] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[   11.286641] ehci_hcd 0000:00:1d.7: irq 11, io mem 0xf4fffc00
[   11.290514] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   11.290622] usb usb4: configuration #1 chosen from 1 choice
[   11.290654] hub 4-0:1.0: USB hub found
[   11.290665] hub 4-0:1.0: 6 ports detected
[   11.398869] SCSI subsystem initialized
[   11.405345] libata version 2.20 loaded.
[   11.406908] b44.c:v1.01 (Jun 16, 2006)
[   11.406934] ACPI: PCI Interrupt 0000:02:01.0[A] -> Link [LNKB] -> GSI 7 (level, low) -> IRQ 7
[   11.410402] eth0: Broadcom 4400 10/100BaseT Ethernet 00:0d:56:38:1c:b2
[   11.412932] ata_piix 0000:00:1f.1: version 2.10ac1
[   11.412950] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[   11.412960] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   11.412981] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   11.413299] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001bfa0 irq 14
[   11.417561] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001bfa8 irq 15
[   11.417600] scsi0 : ata_piix
[   11.736082] ata1.00: ATAPI, max UDMA/33
[   11.900056] ata1.00: configured for UDMA/33
[   11.900073] scsi1 : ata_piix
[   12.064281] ata2.00: ata_hpa_resize 1: sectors = 117210240, hpa_sectors = 117210240
[   12.064286] ata2.00: ATA-6: Hitachi HTS541060G9AT00, MB3OA61A, max UDMA/100
[   12.064290] ata2.00: 117210240 sectors, multi 8: LBA48 
[   12.072273] ata2.00: ata_hpa_resize 1: sectors = 117210240, hpa_sectors = 117210240
[   12.072276] ata2.00: configured for UDMA/100
[   12.072853] scsi 0:0:0:0: CD-ROM            QSI      CDRW/DVD SBW-242 UD22 PQ: 0 ANSI: 5
[   12.073526] scsi 1:0:0:0: Direct-Access     ATA      Hitachi HTS54106 MB3O PQ: 0 ANSI: 5
[   12.074120] ACPI: PCI Interrupt 0000:02:04.1[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   12.124297] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[11]  MMIO=[faffd800-faffdfff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   12.148791] sr0: scsi3-mmc drive: 4x/24x writer cd/rw xa/form2 cdda tray
[   12.148798] Uniform CD-ROM driver Revision: 3.20
[   12.149062] sr 0:0:0:0: Attached scsi CD-ROM sr0
[   12.154070] sr 0:0:0:0: Attached scsi generic sg0 type 5
[   12.154093] scsi 1:0:0:0: Attached scsi generic sg1 type 0
[   12.162417] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB)
[   12.162529] sda: Write Protect is off
[   12.162532] sda: Mode Sense: 00 3a 00 00
[   12.162553] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   12.162748] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB)
[   12.162760] sda: Write Protect is off
[   12.162763] sda: Mode Sense: 00 3a 00 00
[   12.162783] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   12.162787]  sda: sda1 sda2 < sda5 >
[   12.219998] sd 1:0:0:0: Attached scsi disk sda
[   12.380879] Attempting manual resume
[   12.380884] swsusp: Resume From Partition 8:5
[   12.380886] PM: Checking swsusp image.
[   12.381130] PM: Resume from disk failed.
[   12.440323] kjournald starting.  Commit interval 5 seconds
[   12.440337] EXT3-fs: mounted filesystem with ordered data mode.
[   13.395830] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[394fc00015e0c861]
[   24.156069] NET: Registered protocol family 17
[   24.507584] intel_rng: FWH not detected
[   24.546814] iTCO_vendor_support: vendor-support=0
[   24.548170] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   24.548273] iTCO_wdt: Found a ICH4 TCO device (Version=1, TCOBASE=0x0860)
[   24.548319] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   24.591564] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   24.595628] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   24.719180] Linux agpgart interface v0.102 (c) Dave Jones
[   24.830686] agpgart: Detected an Intel 845G Chipset.
[   24.836608] agpgart: AGP aperture is 128M @ 0xe0000000
[   25.268995] input: PC Speaker as /class/input/input2
[   25.424669] Yenta: CardBus bridge found at 0000:02:04.0 [1028:0149]
[   25.424690] Yenta: Using CSCINT to route CSC interrupts to PCI
[   25.424692] Yenta: Routing CardBus interrupts to PCI
[   25.424698] Yenta TI: socket 0000:02:04.0, mfunc 0x00001002, devctl 0x64
[   25.694394] Yenta: ISA IRQ mask 0x0478, PCI irq 11
[   25.694400] Socket status: 30000020
[   25.694403] Yenta: Raising subordinate bus# of parent bus (#02) from #02 to #06
[   25.694411] pcmcia: parent PCI bridge I/O window: 0xd000 - 0xefff
[   25.694415] cs: IO port probe 0xd000-0xefff: clean.
[   25.694965] pcmcia: parent PCI bridge Memory window: 0xf6000000 - 0xfbffffff
[   25.694969] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x33ffffff
[   25.695211] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 7 (level, low) -> IRQ 7
[   25.695250] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   25.829925] b44: eth0: Link is up at 100 Mbps, full duplex.
[   25.829929] b44: eth0: Flow control is off for TX and off for RX.
[   25.839644] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x254ab1, caps: 0x804713/0x0
[   25.884022] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[   26.329708] pccard: CardBus card inserted into slot 0
[   26.376607] cs: IO port probe 0x100-0x3af: clean.
[   26.377983] cs: IO port probe 0x3e0-0x4ff: clean.
[   26.378436] cs: IO port probe 0x820-0x8ff: clean.
[   26.378513] cs: IO port probe 0xc00-0xcf7: clean.
[   26.379007] cs: IO port probe 0xa00-0xaff: clean.
[   26.405926] ieee80211_crypt: registered algorithm 'NULL'
[   26.409313] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   26.409318] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   26.438303] bcm43xx driver
[   26.513682] intel8x0_measure_ac97_clock: measured 55327 usecs
[   26.513686] intel8x0: clocking to 48000
[   26.517832] PCI: Enabling device 0000:03:00.0 (0000 -> 0002)
[   26.517849] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   26.517864] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   26.800931] bcm43xx: Error: Microcode "bcm43xx_microcode4.fw" not available or load failed.
[   26.984894] bcm43xx: Error: Microcode "bcm43xx_microcode4.fw" not available or load failed.
[   27.146172] bcm43xx: Error: Microcode "bcm43xx_microcode4.fw" not available or load failed.
[   27.154959] fuse init (API version 7.8)
[   27.217639] lp: driver loaded but no devices found
[   27.277882] Adding 1510068k swap on /dev/disk/by-uuid/57fc74b6-6695-4e4f-bdf2-ac663afc1af8.  Priority:-1 extents:1 across:1510068k
[   27.413858] EXT3 FS on sda1, internal journal
[   28.783792] NET: Registered protocol family 10
[   28.783914] lo: Disabled Privacy Extensions
[   32.002606] input: Lid Switch as /class/input/input4
[   32.007681] ACPI: Lid Switch [LID]
[   32.044577] input: Power Button (CM) as /class/input/input5
[   32.049618] ACPI: Power Button (CM) [PBTN]
[   32.086913] input: Sleep Button (CM) as /class/input/input6
[   32.091918] ACPI: Sleep Button (CM) [SBTN]
[   32.376825] ACPI: Battery Slot [BAT0] (battery present)
[   32.393704] ACPI: AC Adapter [AC] (off-line)
[   32.466550] ibm_acpi: ec object not found
[   32.513053] No dock devices found.
[   32.655702] Using specific hotkey driver
[   32.685732] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   32.686052] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   32.686108] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)
[   32.756943] pcc_acpi: loading...
[   36.549703] bcm43xx: Error: Microcode "bcm43xx_microcode4.fw" not available or load failed.
[   37.319717] [drm] Initialized drm 1.1.0 20060810
[   37.340543] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 11
[   37.340551] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKE] -> GSI 11 (level, low) -> IRQ 11
[   37.344181] [drm] Initialized radeon 1.25.0 20060524 on minor 0
[   38.675299] ppdev: user-space parallel port driver
[   38.676748] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[   38.676895] agpgart: Putting AGP V2 device at 0000:00:00.0 into 1x mode
[   38.677037] agpgart: Putting AGP V2 device at 0000:01:00.0 into 1x mode
[   38.914993] [drm] Setting GART location based on new memory map
[   38.915047] [drm] writeback test succeeded in 1 usecs
[   39.695401] apm: BIOS not found.
[   40.107678] bcm43xx: Error: Microcode "bcm43xx_microcode4.fw" not available or load failed.
[   40.279840] Bluetooth: Core ver 2.11
[   40.279957] NET: Registered protocol family 31
[   40.279959] Bluetooth: HCI device and connection manager initialized
[   40.279964] Bluetooth: HCI socket layer initialized
[   40.341614] Bluetooth: L2CAP ver 2.8
[   40.341620] Bluetooth: L2CAP socket layer initialized
[   40.539096] Bluetooth: RFCOMM socket layer initialized
[   40.539115] Bluetooth: RFCOMM TTY layer initialized
[   40.539117] Bluetooth: RFCOMM ver 1.8
[   62.363640] bcm43xx: Error: Microcode "bcm43xx_microcode4.fw" not available or load failed.
[   64.113822] bcm43xx: Error: Microcode "bcm43xx_microcode4.fw" not available or load failed.
[   89.087519] bcm43xx: Error: Microcode "bcm43xx_microcode4.fw" not available or load failed.
[  112.470413] bcm43xx: Error: Microcode "bcm43xx_microcode4.fw" not available or load failed.
[  136.294168] bcm43xx: Error: Microcode "bcm43xx_microcode4.fw" not available or load failed.
[  159.687479] bcm43xx: Error: Microcode "bcm43xx_microcode4.fw" not available or load failed.
[  283.042385] bcm43xx: Error: Microcode "bcm43xx_microcode4.fw" not available or load failed.
[  367.322458] bcm43xx: Error: Microcode "bcm43xx_microcode4.fw" not available or load failed.
[  408.059228] bcm43xx: Error: Microcode "bcm43xx_microcode4.fw" not available or load failed.
[  531.530585] bcm43xx: Error: Microcode "bcm43xx_microcode4.fw" not available or load failed.
[  584.291354] bcm43xx: Error: Microcode "bcm43xx_microcode4.fw" not available or load failed.
[  654.910334] bcm43xx: Error: Microcode "bcm43xx_microcode4.fw" not available or load failed.
[  778.270495] bcm43xx: Error: Microcode "bcm43xx_microcode4.fw" not available or load failed.
[  903.231182] bcm43xx: Error: Microcode "bcm43xx_microcode4.fw" not available or load failed.
[  997.405085] bcm43xx: Error: Microcode "bcm43xx_microcode4.fw" not available or load failed.
[ 1026.618376] bcm43xx: Error: Microcode "bcm43xx_microcode4.fw" not available or load failed.
[ 1150.059184] bcm43xx: Error: Microcode "bcm43xx_microcode4.fw" not available or load failed.
[ 1274.994554] bcm43xx: Error: Microcode "bcm43xx_microcode4.fw" not available or load failed.
[ 1398.596533] bcm43xx: Error: Microcode "bcm43xx_microcode4.fw" not available or load failed.
[ 1423.191969] bcm43xx: Error: Microcode "bcm43xx_microcode4.fw" not available or load failed.
[ 1521.989433] bcm43xx: Error: Microcode "bcm43xx_microcode4.fw" not available or load failed.
[ 1645.346466] bcm43xx: Error: Microcode "bcm43xx_microcode4.fw" not available or load failed.
[ 1770.310953] bcm43xx: Error: Microcode "bcm43xx_microcode4.fw" not available or load failed.
[ 1785.345248] bcm43xx: Error: Microcode "bcm43xx_microcode4.fw" not available or load failed.
[ 1893.697303] bcm43xx: Error: Microcode "bcm43xx_microcode4.fw" not available or load failed.
[ 2017.071306] bcm43xx: Error: Microcode "bcm43xx_microcode4.fw" not available or load failed.
[ 2072.095514] bcm43xx: Error: Microcode "bcm43xx_microcode4.fw" not available or load failed.
[ 2140.725090] bcm43xx: Error: Microcode "bcm43xx_microcode4.fw" not available or load failed.
[ 2264.650783] bcm43xx: Error: Microcode "bcm43xx_microcode4.fw" not available or load failed.
[ 2388.368721] bcm43xx: Error: Microcode "bcm43xx_microcode4.fw" not available or load failed.
[ 2407.182877] bcm43xx: Error: Microcode "bcm43xx_microcode4.fw" not available or load failed.
[ 2513.286010] bcm43xx: Error: Microcode "bcm43xx_microcode4.fw" not available or load failed.
[ 2638.269945] bcm43xx: Error: Microcode "bcm43xx_microcode4.fw" not available or load failed.
[ 2743.024328] bcm43xx: Error: Microcode "bcm43xx_microcode4.fw" not available or load failed.
[ 2761.842681] bcm43xx: Error: Microcode "bcm43xx_microcode4.fw" not available or load failed.
[ 2885.231525] bcm43xx: Error: Microcode "bcm43xx_microcode4.fw" not available or load failed.
[ 2950.805149] ISO 9660 Extensions: Microsoft Joliet Level 3
[ 2950.835517] ISOFS: changing to secondary root
[ 3008.608989] bcm43xx: Error: Microcode "bcm43xx_microcode4.fw" not available or load failed.
[ 3095.005553] bcm43xx: Error: Microcode "bcm43xx_microcode4.fw" not available or load failed.
[ 3133.322921] bcm43xx: Error: Microcode "bcm43xx_microcode4.fw" not available or load failed.
[ 3256.788242] bcm43xx: Error: Microcode "bcm43xx_microcode4.fw" not available or load failed.
[ 3333.929738] bcm43xx: Error: Microcode "bcm43xx_microcode4.fw" not available or load failed.

---

