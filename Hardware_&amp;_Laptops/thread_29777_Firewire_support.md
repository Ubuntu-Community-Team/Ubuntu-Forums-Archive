---
title: "Firewire support"
date: 2005-04-25
forum: Hardware &amp; Laptops
---

### Post by innersports on 2005-04-25
I have a Toshiba Laptop (5205-S503). I cannot use my firewire to capture video from my Sony DSC-TRV330. I believe I have to rebuild the kernel. If anyone thinks I am in the wrong category with this, please let me know, so I can post it in the right place, since my last posting did not receive any answers.

I am excited with the Linux idea as my windows system became very slow, whenever I was doing video-editing. I decided to reload after many months of trying to fix it. Then the windows disc no.2 of the recovery disks was not readable even though its condition was like new, it kept slowing down and stalling. Windows or cd drive, maybe both ?

I loaded Ubuntu and was astounded by its speed and multitude of programs, but I think the major hurdle for any lap user will be that it cannot read a number of devices. To rebuild a kernel is also not an easy affair, but I am ready to do it if there was more support. Else I am stuck...

Thanks for any compassionate soul out there... Mark

---

### Post by soce_32 on 2005-04-25
In a terminal do an lsmod | grep 1394.  You should see several modules loaded after you plug your camera in.  The firewire and video modules are standard in the ubuntu kernel, and they should auto-load when a firewire device is attached.

You can also use the dmesg command to see what happens when you plug in your camera.

---

### Post by innersports on 2005-05-09
Thanks for the reply !

Do I have to do this when I am on the internet I suppose ? I am here in Mexico and trying to get internet connection to my home, right now I am still on internet cafes... I will let you know how it works. So far,The firewire does appear in the hardware, but the device is not recognized.

Thanks again, Mark

---

### Post by innersports on 2005-05-19
Hi,

This is what I got on the second command. I think only the last lines are relevant...

Thanks again, but I think the general knowledge is to rebuild the kernel...
finding the patch needed first...

536 bytes)
Detected 1994.200 MHz processor.
Using pmtmr for high-res timesource
Console: colour VGA+ 80x25
Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Memory: 771408k/786224k available (1587k kernel code, 14252k reserved, 714k data
, 164k init, 0k highmem)
Checking if this processor honours the WP bit even in supervisor mode... Ok.
Calibrating delay loop... 3948.54 BogoMIPS (lpj=1974272)
Security Framework v1.0.0 initialized
SELinux:  Disabled at boot.
Mount-cache hash table entries: 512 (order: 0, 4096 bytes)
CPU: After generic identify, caps: 3febf9ff 00000000 00000000 00000000 00000000
00000000
CPU: After vendor identify, caps: 3febf9ff 00000000 00000000 00000000 00000000 0
0000000
CPU: Trace cache: 12K uops, L1 D cache: 8K
CPU: L2 cache: 512K
CPU: After all inits, caps: 3febf9ff 00000000 00000000 00000080 00000000 0000000
0
Intel machine check architecture supported.
Intel machine check reporting enabled on CPU#0.
CPU0: Intel P4/Xeon Extended MCE MSRs (12) available
CPU0: Thermal monitoring enabled
CPU: Intel(R) Pentium(R) 4 Mobile CPU 2.00GHz stepping 04
Enabling fast FPU save and restore... done.
Enabling unmasked SIMD FPU exception support... done.
Checking 'hlt' instruction... OK.
ACPI: Looking for DSDT in initrd... not found!
ACPI: setting ELCR to 0200 (from 0af0)
checking if image is initramfs...it isn't (bad gzip magic numbers); looks like a
n initrd
Freeing initrd memory: 4524k freed
NET: Registered protocol family 16
PCI: PCI BIOS revision 2.10 entry at 0xfcebc, last bus=4
PCI: Using configuration type 1
mtrr: v2.0 (20020519)
ACPI: Subsystem revision 20050211
ACPI: Interpreter enabled
ACPI: Using PIC for interrupt routing
ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 10 11 12) *0, disabled.
ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 6 7 10 11 12) *0, disabled.
ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 10 *11 12)
ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *6 7 10 11 12)
ACPI: PCI Interrupt Link [LNKE] (IRQs 3 *4 6 7 10 11 12)
ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12) *0, disabled.
ACPI: PCI Interrupt Link [LNKG] (IRQs *5)
ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 6 7 10 11 12) *0, disabled.
ACPI: PCI Root Bridge [PCI0] (00:00)
PCI: Probing PCI hardware (bus 00)
PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
PCI: Transparent bridge - 0000:00:1e.0
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
ACPI: Power Resource [PFN0] (off)
ACPI: Power Resource [PFN1] (off)
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
Simple Boot Flag at 0x7c set to 0x1
audit: initializing netlink socket (disabled)
audit(1116518678.109:0): initialized
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
PCI: Enabling device 0000:00:1f.6 (0000 -> 0001)
ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
PCI: setting IRQ 11 as level-triggered
ACPI: PCI interrupt 0000:00:1f.6[B] -> GSI 11 (level, low) -> IRQ 11
io scheduler noop registered
io scheduler anticipatory registered
io scheduler deadline registered
io scheduler cfq registered
RAMDISK driver initialized: 16 RAM disks of 8192K size 1024 blocksize
input: AT Translated Set 2 keyboard on isa0060/serio0
NET: Registered protocol family 2
IP: routing cache hash table of 8192 buckets, 64Kbytes
TCP: Hash tables configured (established 262144 bind 65536)
NET: Registered protocol family 8
NET: Registered protocol family 20
Restarting tasks...<6> Strange, kswapd0 not stopped
 Strange, kseriod not stopped
 done
ACPI wakeup devices:
 LAN CBC0 USB2 USB3 USB4 AMDM  LID
ACPI: (supports S0 S3 S4 S5)
RAMDISK: cramfs filesystem found at block 0
RAMDISK: Loading 4524KiB [1 disk] into ram disk... done.
VFS: Mounted root (cramfs filesystem) readonly.
Freeing unused kernel memory: 164k freed
ACPI: Fan [FAN0] (off)
ACPI: Fan [FAN1] (off)
ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
ACPI: Thermal Zone [THRM] (48 C)
NET: Registered protocol family 1
Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
ICH3M: IDE controller at PCI slot 0000:00:1f.1
ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
ACPI: PCI interrupt 0000:00:1f.1[A] -> GSI 11 (level, low) -> IRQ 11
ICH3M: chipset revision 2
ICH3M: not 100% native mode: will probe irqs later
    ide0: BM-DMA at 0xcfa0-0xcfa7, BIOS settings: hda:DMA, hdb:DMA
    ide1: BM-DMA at 0xcfa8-0xcfaf, BIOS settings: hdc:pio, hdd:pio
Probing IDE interface ide0...
hda: TOSHIBA MK4018GAS, ATA DISK drive
hdb: DW-224E, ATAPI CD/DVD-ROM drive
elevator: using anticipatory as default io scheduler
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
hda: max request size: 128KiB
hda: 78140160 sectors (40007 MB), CHS=65535/16/63, UDMA(100)
hda: cache flushes supported
 /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >
Probing IDE interface ide1...
Probing IDE interface ide1...
Probing IDE interface ide2...
Probing IDE interface ide3...
Probing IDE interface ide4...
Probing IDE interface ide5...
Stopping tasks: ==|
Freeing memory... done (464 pages freed)
Restarting tasks... done
EXT3-fs: mounted filesystem with ordered data mode.
kjournald starting.  Commit interval 5 seconds
Adding 1622524k swap on /dev/hda5.  Priority:-1 extents:1
EXT3 FS on hda1, internal journal
hdb: ATAPI 24X DVD-ROM CD-R/RW drive, 1658kB Cache
Uniform CD-ROM driver Revision: 3.20
lp: driver loaded but no devices found
mice: PS/2 mouse device common for all mice
input: ImPS/2 Generic Wheel Mouse on isa0060/serio1
ieee1394: Initialized config rom entry `ip1394'
ts: Compaq touchscreen protocol output
SCSI subsystem initialized
sbp2: $Rev: 1219 $ Ben Collins <bcollins@debian.org>
Linux agpgart interface v0.100 (c) Dave Jones
nvidia: module license 'NVIDIA' taints kernel.
ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 5
PCI: setting IRQ 5 as level-triggered
ACPI: PCI interrupt 0000:01:00.0[A] -> GSI 5 (level, low) -> IRQ 5
NVRM: loading NVIDIA Linux x86 NVIDIA Kernel Module  1.0-7174  Tue Mar 22 06:44:
39 PST 2005
Capability LSM initialized
device-mapper: 4.3.0-ioctl (2004-09-30) initialised: [email]dm-devel@redhat.com[/email]
md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
cdrom: open failed.
input: PC Speaker
Real Time Clock Driver v1.12
agpgart: Detected an Intel i845 Chipset.
agpgart: Maximum main memory to use for agp memory: 690M
agpgart: AGP aperture is 256M @ 0xe0000000
cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
pciehp: acpi_pciehprm:\_SB_.PCI0 evaluate _BBN fail=0x5
pciehp: acpi_pciehprm:get_device PCI ROOT HID fail=0x5
shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
pciehp: acpi_pciehprm:\_SB_.PCI0 evaluate _BBN fail=0x5
pciehp: acpi_pciehprm:get_device PCI ROOT HID fail=0x5
hw_random: RNG not detected
PCI: Enabling device 0000:00:1f.5 (0000 -> 0001)
ACPI: PCI interrupt 0000:00:1f.5[B] -> GSI 11 (level, low) -> IRQ 11
PCI: Setting latency timer of device 0000:00:1f.5 to 64
intel8x0_measure_ac97_clock: measured 49397 usecs
intel8x0: clocking to 48000
usbcore: registered new driver usbfs
usbcore: registered new driver hub
ohci_hcd: 2004 Nov 08 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 6
PCI: setting IRQ 6 as level-triggered
ACPI: PCI interrupt 0000:02:06.0[A] -> GSI 6 (level, low) -> IRQ 6
ohci_hcd 0000:02:06.0: NEC Corporation USB
ohci_hcd 0000:02:06.0: irq 6, pci mem 0xfceff000
ohci_hcd 0000:02:06.0: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 3 ports detected
ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 4
PCI: setting IRQ 4 as level-triggered
ACPI: PCI interrupt 0000:02:06.1[B] -> GSI 4 (level, low) -> IRQ 4
ohci_hcd 0000:02:06.1: NEC Corporation USB (#2)
ohci_hcd 0000:02:06.1: irq 4, pci mem 0xfcefe000
ohci_hcd 0000:02:06.1: new USB bus registered, assigned bus number 2
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 2 ports detected
usb 1-3: new low speed USB device using ohci_hcd and address 2
PCI: Enabling device 0000:02:06.2 (0000 -> 0002)
ACPI: PCI interrupt 0000:02:06.2[C] -> GSI 11 (level, low) -> IRQ 11
ehci_hcd 0000:02:06.2: NEC Corporation USB 2.0
ehci_hcd 0000:02:06.2: irq 11, pci mem 0x30000400
ehci_hcd 0000:02:06.2: new USB bus registered, assigned bus number 3
ehci_hcd 0000:02:06.2: USB 2.0 initialized, EHCI 0.95, driver 26 Oct 2004
hub 3-0:1.0: USB hub found
hub 3-0:1.0: 5 ports detected
usbcore: registered new driver hiddev
usbhid: probe of 1-3:1.0 failed with error -5
usbcore: registered new driver usbhid
drivers/usb/input/hid-core.c: v2.0:USB HID core driver
usb 1-3: USB disconnect, address 2
ohci1394: $Rev: 1223 $ Ben Collins <bcollins@debian.org>
PCI: Enabling device 0000:02:07.0 (0000 -> 0002)
ACPI: PCI Interrupt Link [LNKF] enabled at IRQ 10
PCI: setting IRQ 10 as level-triggered
ACPI: PCI interrupt 0000:02:07.0[A] -> GSI 10 (level, low) -> IRQ 10
PCI: Setting latency timer of device 0000:02:07.0 to 64
usb 1-3: new low speed USB device using ohci_hcd and address 3
ohci1394: fw-host0: Set PHY Reg timeout [0xffffffff/0x00004000/100]
ohci1394: fw-host0: Runaway loop while stopping context: ...
input: USB HID v1.00 Mouse [Synaptics Inc. Synaptics WheelPad] on usb-0000:02:06
.0-3
ohci1394: fw-host0: Runaway loop while stopping context: ...
ohci1394: fw-host0: Runaway loop while stopping context: ...
ohci1394: fw-host0: Runaway loop while stopping context: ...
ohci1394: fw-host0: OHCI-1394 165.165 (PCI): IRQ=[10]  MMIO=[30000800-30000fff]
 Max Packet=[65536]
ohci1394: fw-host0: Set PHY Reg timeout [0xffffffff/0x00004000/100]
ohci1394: fw-host0: Set PHY Reg timeout [0xffffffff/0x00004000/100]
ohci1394: fw-host0: Set PHY Reg timeout [0xffffffff/0x00004000/100]
ohci1394: fw-host0: Set PHY Reg timeout [0xffffffff/0x00004000/100]
ohci1394: fw-host0: Set PHY Reg timeout [0xffffffff/0x00004000/100]
ohci1394: fw-host0: Set PHY Reg timeout [0xffffffff/0x00004000/100]
ohci1394: fw-host0: Set PHY Reg timeout [0xffffffff/0x00004000/100]
ohci1394: fw-host0: Set PHY Reg timeout [0xffffffff/0x00004000/100]
ohci1394: fw-host0: Set PHY Reg timeout [0xffffffff/0x00004000/100]
ohci1394: fw-host0: Set PHY Reg timeout [0xffffffff/0x00004000/100]
ohci1394: fw-host0: Set PHY Reg timeout [0xffffffff/0x00004000/100]
ohci1394: fw-host0: Set PHY Reg timeout [0xffffffff/0x00004000/100]
ohci1394: fw-host0: Set PHY Reg timeout [0xffffffff/0x00004000/100]
ohci1394: fw-host0: Set PHY Reg timeout [0xffffffff/0x00004000/100]
ohci1394: fw-host0: Set PHY Reg timeout [0xffffffff/0x00004000/100]
ohci1394: fw-host0: Set PHY Reg timeout [0xffffffff/0x00004000/100]
ohci1394: fw-host0: Set PHY Reg timeout [0xffffffff/0x00004000/100]
ohci1394: fw-host0: Set PHY Reg timeout [0xffffffff/0x00004000/100]
ohci1394: fw-host0: Set PHY Reg timeout [0xffffffff/0x00004000/100]
ohci1394: fw-host0: Set PHY Reg timeout [0xffffffff/0x00004000/100]
ohci1394: fw-host0: Set PHY Reg timeout [0xffffffff/0x00004000/100]
ohci1394: fw-host0: Set PHY Reg timeout [0xffffffff/0x00004000/100]
ohci1394: fw-host0: Set PHY Reg timeout [0xffffffff/0x00004000/100]
ohci1394: fw-host0: Set PHY Reg timeout [0xffffffff/0x00004000/100]
ohci1394: fw-host0: Set PHY Reg timeout [0xffffffff/0x00004000/100]
ohci1394: fw-host0: Set PHY Reg timeout [0xffffffff/0x00004000/100]
ohci1394: fw-host0: Set PHY Reg timeout [0xffffffff/0x00004000/100]
ohci1394: fw-host0: Set PHY Reg timeout [0xffffffff/0x00004000/100]
ohci1394: fw-host0: Set PHY Reg timeout [0xffffffff/0x00004000/100]
ohci1394: fw-host0: Set PHY Reg timeout [0xffffffff/0x00004000/100]
ohci1394: fw-host0: Serial EEPROM has suspicious values, attempting to setting m
ax_packet_size to 512 bytes
e100: Intel(R) PRO/100 Network Driver, 3.2.3-k2-NAPI
e100: Copyright(c) 1999-2004 Intel Corporation
ACPI: PCI interrupt 0000:02:08.0[A] -> GSI 4 (level, low) -> IRQ 4
e100: eth0: e100_probe: addr 0xfcefd000, irq 4, MAC addr 00:00:39:2C:2E:DD
Linux Kernel Card Services
  options:  [pci] [cardbus] [pm]
PCI: Enabling device 0000:02:0b.0 (0000 -> 0002)
ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 10
ACPI: PCI interrupt 0000:02:0b.0[A] -> GSI 10 (level, low) -> IRQ 10
Yenta: CardBus bridge found at 0000:02:0b.0 [1179:0001]
Yenta: ISA IRQ mask 0x0008, PCI irq 10
Socket status: 30000007
ohci1394: fw-host0: Set PHY Reg timeout [0xffffffff/0x00004000/100]
e100: eth0: e100_watchdog: link up, 10Mbps, half-duplex
NET: Registered protocol family 17
NET: Registered protocol family 10
Disabled Privacy Extensions on device c0313ce0(lo)
IPv6 over IPv4 tunneling driver
ACPI: AC Adapter [ADP1] (on-line)
ACPI: Battery Slot [BAT1] (battery present)
ACPI: Battery Slot [BAT2] (battery absent)
ACPI: Power Button (FF) [PWRF]
ACPI: Lid Switch [LID]
ibm_acpi: ec object not found
toshiba_acpi: Toshiba Laptop ACPI Extras version 0.19a
toshiba_acpi:     HCI method: \_SB_.VALD.GHCI
toshiba_acpi: Toshiba hotkeys are sent as ACPI events
toshiba_acpi: ktoshkeyd will check 2 times per second
toshiba_acpi: Dropped 0 keys from the queue on startup
ACPI: Video Device [VGA] (multi-head: yes  rom: yes  post: no)
apm: BIOS not found.
cs: IO port probe 0x0100-0x04ff: excluding 0x170-0x177 0x1e0-0x1e7 0x370-0x377 0                                                                                          x4d0-0x4d7
cs: IO port probe 0x0800-0x08ff: clean.
cs: IO port probe 0x0c00-0x0cff: clean.
cs: IO port probe 0x0a00-0x0aff: clean.
acpi-cpufreq: CPU0 - ACPI performance management activated.
eth0: no IPv6 routers present
agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
spurious 8259A interrupt: IRQ7.

For the first command this is what I got:

ohci1394               34596  0
ieee1394              108312  2 ohci1394,sbp2

---

### Post by sksbir on 2006-01-15
I'm on the same problem has you. take a look here : [http://forum.ubuntu-fr.org/viewtopic.php?id=24257](http://forum.ubuntu-fr.org/viewtopic.php?id=24257)

---

