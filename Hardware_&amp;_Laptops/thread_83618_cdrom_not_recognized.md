---
title: "cdrom not recognized"
date: 2005-10-29
forum: Hardware &amp; Laptops
---

### Post by Eremit on 2005-10-29
Hallo I have an IBM Intellistation M Pro 6889 here with hoary running
[http://www-306.ibm.com/pc/support/site.wss/document.do?lndocid=JBAR-3TMKQ2](http://www-306.ibm.com/pc/support/site.wss/document.do?lndocid=JBAR-3TMKQ2)

I want to update it to breezy from cdrom but it's not recognized.
(Although it's recognized in bios)

> mount: special device /dev/cdrom does not exist
same with hdc

dmesg:
> Linux version 2.6.10-5-686-smp (buildd@terranova) (gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)) #1 SMP Tue Apr 5 12:41:40 UTC 2005
BIOS-provided physical RAM map:
 BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
 BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
 BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
 BIOS-e820: 0000000000100000 - 000000000fffdc00 (usable)
 BIOS-e820: 000000000fffdc00 - 000000000fffff00 (ACPI data)
 BIOS-e820: 000000000fffff00 - 0000000010000000 (reserved)
 BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
 BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
 BIOS-e820: 00000000fffc0000 - 0000000100000000 (reserved)
0MB HIGHMEM available.
255MB LOWMEM available.
found SMP MP-table at 0009fe00
On node 0 totalpages: 65533
  DMA zone: 4096 pages, LIFO batch:1
  Normal zone: 61437 pages, LIFO batch:14
  HighMem zone: 0 pages, LIFO batch:1
DMI 2.1 present.
ACPI: RSDP (v000 IBM                                   ) @ 0x000fdfe0
ACPI: RSDT (v001 IBM    CDTPWSNU 0x00001000 IBM  0x00000000) @ 0x0ffffe80
ACPI: FADT (v001 IBM    CDTPWSNU 0x00001000 IBM  0x00000000) @ 0x0ffffe00
ACPI: MADT (v001 IBM    CDTPWSNU 0x00001000 IBM  0x00000000) @ 0x0ffffd80
ACPI: DSDT (v001 IBM    CDTPWSNU 0x00001000 MSFT 0x01000007) @ 0x00000000
ACPI: PM-Timer IO Port: 0xfd08
ACPI: Local APIC address 0xfee00000
ACPI: LAPIC (acpi_id[0x00] lapic_id[0x01] enabled)
Processor #1 6:7 APIC version 17
ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Processor #0 6:7 APIC version 17
ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
ACPI: IRQ0 used by override.
ACPI: IRQ2 used by override.
ACPI: IRQ9 used by override.
ACPI: NMI_SRC (dfl dfl global_irq 0)
Enabling APIC mode:  Flat.  Using 1 I/O APICs
Using ACPI (MADT) for SMP configuration information
Built 1 zonelists
Kernel command line: root=/dev/sda3 ro 
mapped APIC to ffffd000 (fee00000)
mapped IOAPIC to ffffc000 (fec00000)
Initializing CPU#0
PID hash table entries: 1024 (order: 10, 16384 bytes)
Detected 449.387 MHz processor.
Using pmtmr for high-res timesource
Console: colour VGA+ 80x25
Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
Memory: 251528k/262132k available (1604k kernel code, 9988k reserved, 719k data, 192k init, 0k highmem)
Checking if this processor honours the WP bit even in supervisor mode... Ok.
Calibrating delay loop... 888.83 BogoMIPS (lpj=444416)
Security Framework v1.0.0 initialized
SELinux:  Disabled at boot.
Mount-cache hash table entries: 512 (order: 0, 4096 bytes)
CPU: After generic identify, caps: 0383fbff 00000000 00000000 00000000 00000000 00000000
CPU: After vendor identify, caps: 0383fbff 00000000 00000000 00000000 00000000 00000000
CPU: L1 I cache: 16K, L1 D cache: 16K
CPU: L2 cache: 512K
CPU: After all inits, caps: 0383fbff 00000000 00000000 00000040 00000000 00000000
Intel machine check architecture supported.
Intel machine check reporting enabled on CPU#0.
Enabling fast FPU save and restore... done.
Enabling unmasked SIMD FPU exception support... done.
Checking 'hlt' instruction... OK.
ACPI: Looking for DSDT in initrd... not found!
CPU0: Intel Pentium III (Katmai) stepping 03
per-CPU timeslice cutoff: 1461.26 usecs.
task migration cache decay timeout: 2 msecs.
Booting processor 1/0 eip 3000
Initializing CPU#1
Calibrating delay loop... 894.97 BogoMIPS (lpj=447488)
CPU: After generic identify, caps: 0383fbff 00000000 00000000 00000000 00000000 00000000
CPU: After vendor identify, caps: 0383fbff 00000000 00000000 00000000 00000000 00000000
CPU: L1 I cache: 16K, L1 D cache: 16K
CPU: L2 cache: 512K
CPU: After all inits, caps: 0383fbff 00000000 00000000 00000040 00000000 00000000
Intel machine check architecture supported.
Intel machine check reporting enabled on CPU#1.
CPU1: Intel Pentium III (Katmai) stepping 03
Total of 2 processors activated (1783.80 BogoMIPS).
ENABLING IO-APIC IRQs
..TIMER: vector=0x31 pin1=2 pin2=-1
checking TSC synchronization across 2 CPUs: passed.
Brought up 2 CPUs
CPU0:
 domain 0: span 01
  groups: 01
  domain 1: span 03
   groups: 01 02
CPU1:
 domain 0: span 02
  groups: 02
  domain 1: span 03
   groups: 02 01
checking if image is initramfs...it isn't (bad gzip magic numbers); looks like an initrd
Freeing initrd memory: 4484k freed
NET: Registered protocol family 16
PCI: PCI BIOS revision 2.10 entry at 0xfd85c, last bus=1
PCI: Using configuration type 1
mtrr: v2.0 (20020519)
ACPI: Subsystem revision 20050211
ACPI: Interpreter enabled
ACPI: Using IOAPIC for interrupt routing
ACPI: PCI Root Bridge [PCI0] (00:00)
PCI: Probing PCI hardware (bus 00)
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
ACPI: PCI Interrupt Link [PIN1] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
ACPI: PCI Interrupt Link [PIN2] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [PIN3] (IRQs 3 4 5 6 7 9 10 11 12 14 *15)
ACPI: PCI Interrupt Link [PIN4] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
Linux Plug and Play Support v0.97 (c) Adam Belay
pnp: PnP ACPI init
pnp: PnP ACPI: found 15 devices
PnPBIOS: Disabled by ACPI PNP
PCI: Using ACPI for IRQ routing
** PCI interrupts are no longer routed automatically.  If this
** causes a device to stop working, it is probably because the
** driver failed to call pci_enable_device().  As a temporary
** workaround, the "pci=routeirq" argument restores the old
** behavior.  If this argument makes the device work again,
** please email the output of "lspci" to [email]bjorn.helgaas@hp.com[/email]
** so I can fix the driver.
pnp: 00:0b: ioport range 0x4d0-0x4d1 has been reserved
pnp: 00:0b: ioport range 0xfd00-0xfd3f could not be reserved
pnp: 00:0b: ioport range 0xfe00-0xfe0f has been reserved
audit: initializing netlink socket (disabled)
audit(1130582888.998:0): initialized
VFS: Disk quotas dquot_6.5.1
Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
devfs: boot_options: 0x0
Initializing Cryptographic API
Limiting direct PCI/PCI transfers.
isapnp: Scanning for PnP cards...
isapnp: Card 'Crystal Audio'
isapnp: 1 Plug & Play card detected total
serio: i8042 AUX port at 0x60,0x64 irq 12
serio: i8042 KBD port at 0x60,0x64 irq 1
Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
ttyS1 at I/O 0x2f8 (irq = 3) is a NS16550A
ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
ttyS1 at I/O 0x2f8 (irq = 3) is a NS16550A
io scheduler noop registered
io scheduler anticipatory registered
io scheduler deadline registered
io scheduler cfq registered
RAMDISK driver initialized: 16 RAM disks of 8192K size 1024 blocksize
input: AT Translated Set 2 keyboard on isa0060/serio0
NET: Registered protocol family 2
IP: routing cache hash table of 2048 buckets, 16Kbytes
TCP: Hash tables configured (established 16384 bind 16384)
NET: Registered protocol family 8
NET: Registered protocol family 20
Restarting tasks...<6> Strange, kswapd0 not stopped
 Strange, kseriod not stopped
 done
ACPI wakeup devices: 
PCI0 PS2K PS2M COM1 COM2 USB0 
ACPI: (supports S0 S1 S4 S5)
RAMDISK: cramfs filesystem found at block 0
RAMDISK: Loading 4484KiB [1 disk] into ram disk... |/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|done.
VFS: Mounted root (cramfs filesystem) readonly.
Freeing unused kernel memory: 192k freed
NET: Registered protocol family 1
SCSI subsystem initialized
ACPI: PCI interrupt 0000:00:03.0[A] -> GSI 20 (level, low) -> IRQ 20
ACPI: PCI interrupt 0000:00:03.1[B] -> GSI 20 (level, low) -> IRQ 20
scsi0 : Adaptec AIC7XXX EISA/VLB/PCI SCSI HBA DRIVER, Rev 6.2.36
        <Adaptec aic7895 Ultra SCSI adapter>
        aic7895C: Ultra Wide Channel A, SCSI Id=7, 32/253 SCBs

elevator: using anticipatory as default io scheduler
(scsi0:A:0): 40.000MB/s transfers (20.000MHz, offset 8, 16bit)
  Vendor: IBM-PSG   Model: DNES-309170W  !#  Rev: SAB0
  Type:   Direct-Access                      ANSI SCSI revision: 03
scsi0:A:0:0: Tagged Queuing enabled.  Depth 8
scsi1 : Adaptec AIC7XXX EISA/VLB/PCI SCSI HBA DRIVER, Rev 6.2.36
        <Adaptec aic7895 Ultra SCSI adapter>
        aic7895C: Ultra Wide Channel B, SCSI Id=7, 32/253 SCBs

SCSI device sda: 17774160 512-byte hdwr sectors (9100 MB)
SCSI device sda: drive cache: write back
SCSI device sda: 17774160 512-byte hdwr sectors (9100 MB)
SCSI device sda: drive cache: write back
 /dev/scsi/host0/bus0/target0/lun0: p1 p2 p3
Attached scsi disk sda at scsi0, channel 0, id 0, lun 0
EXT3-fs: INFO: recovery required on readonly filesystem.
EXT3-fs: write access will be enabled during recovery.
EXT3-fs: recovery complete.
kjournald starting.  Commit interval 5 seconds
EXT3-fs: mounted filesystem with ordered data mode.
Adding 682720k swap on /dev/sda1.  Priority:-1 extents:1
EXT3 FS on sda3, internal journal
NET: Registered protocol family 17
ne2k-pci.c:v1.03 9/22/2003 D. Becker/P. Gortmaker
  [http://www.scyld.com/network/ne2k-pci.html](http://www.scyld.com/network/ne2k-pci.html)
ACPI: PCI interrupt 0000:00:0e.0[A] -> GSI 18 (level, low) -> IRQ 18
eth0: RealTek RTL-8029 found at 0x70e0, IRQ 18, 00:4F:49:09:6A:35.
pnp: Device 01:01.00 activated.
pnp: Device 01:01.02 activated.
Capability LSM initialized
EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
kjournald starting.  Commit interval 5 seconds
EXT3 FS on sda2, internal journal
EXT3-fs: recovery complete.
EXT3-fs: mounted filesystem with ordered data mode.
Linux agpgart interface v0.100 (c) Dave Jones
agpgart: Detected an Intel 440BX Chipset.
agpgart: Maximum main memory to use for agp memory: 203M
agpgart: AGP aperture is 64M @ 0xf0000000
cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
pciehp: acpi_pciehprm:\_SB_.PCI0 evaluate _BBN fail=0x5
pciehp: acpi_pciehprm:get_device PCI ROOT HID fail=0x5
shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
e100: Intel(R) PRO/100 Network Driver, 3.2.3-k2-NAPI
e100: Copyright(c) 1999-2004 Intel Corporation
ACPI: PCI interrupt 0000:00:02.0[A] -> GSI 18 (level, low) -> IRQ 18
e100: eth1: e100_probe: addr 0xf5fff000, irq 18, MAC addr 00:04:AC:96:DC:B4
Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
usbcore: registered new driver usbfs
usbcore: registered new driver hub
USB Universal Host Controller Interface driver v2.2
ACPI: PCI interrupt 0000:00:04.2[D] -> GSI 19 (level, low) -> IRQ 19
uhci_hcd 0000:00:04.2: Intel Corp. 82371AB/EB/MB PIIX4 USB
uhci_hcd 0000:00:04.2: irq 19, io base 0xff00
uhci_hcd 0000:00:04.2: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 2 ports detected
piix4_smbus 0000:00:04.3: Found 0000:00:04.3 device
piix4_smbus 0000:00:04.3: IBM Laptop detected; this module may corrupt your serial eeprom! Refusing to load module!
piix4_smbus: probe of 0000:00:04.3 failed with error -1
input: ImPS/2 Generic Wheel Mouse on isa0060/serio1
inserting floppy driver for 2.6.10-5-686-smp
Floppy drive(s): fd0 is 1.44M
mice: PS/2 mouse device common for all mice
ts: Compaq touchscreen protocol output
floppy0: no floppy controllers found
parport: PnPBIOS parport detected.
parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
Real Time Clock Driver v1.12
input: PC Speaker
NET: Registered protocol family 10
Disabled Privacy Extensions on device c0317e40(lo)
IPv6 over IPv4 tunneling driver
lp0: using parport0 (interrupt-driven).
eth0: no IPv6 routers present


any ideas?

btw. I think it worked when i had installed debian sarge - than I upgraded to hoary and never used it again until today :)

---

### Post by bernardfrancois on 2005-11-27
I have a similar problem. I could install ubuntu, but afterwards the cdrom is not recognised. There is no /dev/hdc or /dev/cdrom. It's a HP Omnibook 4150. It worked under Fedora Core 3. 

Anyone who can help? I would really appreciate, since I urgently need to install oracle on it (which I have on a cd), it's for a school task...

---

