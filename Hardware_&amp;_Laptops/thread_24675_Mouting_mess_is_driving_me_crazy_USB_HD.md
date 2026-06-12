---
title: "Mouting mess is driving me crazy: USB HD"
date: 2005-04-07
forum: Hardware &amp; Laptops
---

### Post by Nano on 2005-04-07
After months and months I still can't do something as simple as mount external partitions at boot.

I have an internal hd and an external one. This is my /etc/fstab:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0

/dev/hda1	/mnt/Windows	vfat	user,owner,rw,umask=000 0 0
/dev/hda3	/mnt/Data01 	vfat	user,owner,rw,umask=000 0 0
/dev/hda4	/mnt/Data02	vfat	user,owner,rw,umask=000 0 0

/dev/sda5	/mnt/Data03 	ext3	defaults 
/dev/sda6	/mnt/Data04	vfat	user,owner,rw,umask=000 0 0

```

I recently reformatted sda with 2 partitions using qparted. The problem is that I can't get sda5 mounted at boot.
I tried many combinations in /etc/fstab but I nad no luck.
Sda6, which is fat32, loads perfecty and shows the icon in gnome as chosen (Data04).
The weird part also is that if I don't plug the usb drive at boot all 3 internal extra partitions will show up (Windows, Data01 and Data02), and if I plug the usb these last 3 wont show up.

Again, how is it possible that simple things like this aren't automatically done?


Can anyone help me? THanks

---

### Post by Nis on 2005-04-07
[QUOTE=Nano]After months and months I still can't do something as simple as mount external partitions at boot.

I have an internal hd and an external one. This is my /etc/fstab:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0

/dev/hda1	/mnt/Windows	vfat	user,owner,rw,umask=000 0 0
/dev/hda3	/mnt/Data01 	vfat	user,owner,rw,umask=000 0 0
/dev/hda4	/mnt/Data02	vfat	user,owner,rw,umask=000 0 0

/dev/sda5	/mnt/Data03 	ext3	defaults 
/dev/sda6	/mnt/Data04	vfat	user,owner,rw,umask=000 0 0

```

I recently reformatted sda with 2 partitions using qparted. The problem is that I can't get sda5 mounted at boot.
I tried many combinations in /etc/fstab but I nad no luck.
Sda6, which is fat32, loads perfecty and shows the icon in gnome as chosen (Data04).
The weird part also is that if I don't plug the usb drive at boot all 3 internal extra partitions will show up (Windows, Data01 and Data02), and if I plug the usb these last 3 wont show up.

Again, how is it possible that simple things like this aren't automatically done?


Can anyone help me? THanks[/QUOTE]
 From a quick glance you're missing the dump and pass numbers for /dev/sda5.  Both should be 0.  Also try removing the owner setting from /dev/hda1, /dev/hda3, /dev/hda4, and /dev/sda6.  The user option should do what I think you want.

---

### Post by Nano on 2005-04-07
[QUOTE=Nis]From a quick glance you're missing the dump and pass numbers for /dev/sda5.  Both should be 0.  Also try removing the owner setting from /dev/hda1, /dev/hda3, /dev/hda4, and /dev/sda6.  The user option should do what I think you want.[/QUOTE]
 I tried also the two "0" thingie with no luck.
Let me restart so I can try removing the owner setting.
Thanks for your attention.

---

### Post by Nano on 2005-04-07
No luck.
Still I have to "mount -a" to get sda5 mounted after login.

Just in case you or someone else still wants to spend some seconds trying to help me, this is my dmesg ([http://pastebin.ca/9073):](http://pastebin.ca/9073):)

```

dmesg
0000e) @ 0x00000000
ACPI: PM-Timer IO Port: 0x1008
ACPI: Local APIC address 0xfee00000
ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Processor #0 15:2 APIC version 20
ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
ACPI: IRQ9 used by override.
Enabling APIC mode:  Flat.  Using 1 I/O APICs
Using ACPI (MADT) for SMP configuration information
Built 1 zonelists
Kernel command line: root=/dev/hda2 ro quiet splash
mapped APIC to ffffd000 (fee00000)
mapped IOAPIC to ffffc000 (fec00000)
Initializing CPU#0
PID hash table entries: 2048 (order: 11, 32768 bytes)
Detected 2793.627 MHz processor.
Using pmtmr for high-res timesource
Console: colour VGA+ 80x25
Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Memory: 510928k/523712k available (1587k kernel code, 12156k reserved, 714k data, 164k init, 0k highmem)
Checking if this processor honours the WP bit even in supervisor mode... Ok.
Calibrating delay loop... 5537.79 BogoMIPS (lpj=2768896)
Security Framework v1.0.0 initialized
SELinux:  Disabled at boot.
Mount-cache hash table entries: 512 (order: 0, 4096 bytes)
CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000
CPU: After vendor identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000
CPU: Trace cache: 12K uops, L1 D cache: 8K
CPU: L2 cache: 512K
CPU: After all inits, caps: bfebfbff 00000000 00000000 00000080 00004400 00000000
Intel machine check architecture supported.
Intel machine check reporting enabled on CPU#0.
CPU0: Intel P4/Xeon Extended MCE MSRs (12) available
CPU0: Thermal monitoring enabled
CPU: Intel Mobile Intel(R) Pentium(R) 4     CPU 2.80GHz stepping 09
Enabling fast FPU save and restore... done.
Enabling unmasked SIMD FPU exception support... done.
Checking 'hlt' instruction... OK.
ACPI: Looking for DSDT in initrd... not found!
ENABLING IO-APIC IRQs
..TIMER: vector=0x31 pin1=0 pin2=-1
checking if image is initramfs...it isn't (bad gzip magic numbers); looks like an initrd
Freeing initrd memory: 4524k freed
NET: Registered protocol family 16
PCI: PCI BIOS revision 2.10 entry at 0xfd822, last bus=3
PCI: Using configuration type 1
mtrr: v2.0 (20020519)
ACPI: Subsystem revision 20050211
ACPI: Interpreter enabled
ACPI: Using IOAPIC for interrupt routing
ACPI: PCI Root Bridge [PCI0] (00:00)
PCI: Probing PCI hardware (bus 00)
PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
PCI: Transparent bridge - 0000:00:1e.0
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
ACPI: PCI Interrupt Link [LNKA] (IRQs 10 *11 14 15)
ACPI: PCI Interrupt Link [LNKB] (IRQs *10 11 14 15)
ACPI: PCI Interrupt Link [LNKC] (IRQs 10 *11 14 15)
ACPI: PCI Interrupt Link [LNKD] (IRQs *10 11 14 15)
ACPI: PCI Interrupt Link [LNKE] (IRQs 10 *11 14 15)
ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LNKH] (IRQs *10 11 14 15)
ACPI: Embedded Controller [EC] (gpe 28)
Linux Plug and Play Support v0.97 (c) Adam Belay
pnp: PnP ACPI init
pnp: PnP ACPI: found 10 devices
PnPBIOS: Disabled by ACPI PNP
PCI: Using ACPI for IRQ routing
** PCI interrupts are no longer routed automatically.  If this
** causes a device to stop working, it is probably because the
** driver failed to call pci_enable_device().  As a temporary
** workaround, the "pci=routeirq" argument restores the old
** behavior.  If this argument makes the device work again,
** please email the output of "lspci" to bjorn.helgaas@hp.com
** so I can fix the driver.
Simple Boot Flag at 0x36 set to 0x1
audit: initializing netlink socket (disabled)
audit(1112939167.092:0): initialized
VFS: Disk quotas dquot_6.5.1
Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
devfs: boot_options: 0x0
Initializing Cryptographic API
isapnp: Scanning for PnP cards...
isapnp: No Plug & Play device found
i8042.c: Detected active multiplexing controller, rev 1.9.
serio: i8042 AUX0 port at 0x60,0x64 irq 12
serio: i8042 AUX1 port at 0x60,0x64 irq 12
serio: i8042 AUX2 port at 0x60,0x64 irq 12
serio: i8042 AUX3 port at 0x60,0x64 irq 12
serio: i8042 KBD port at 0x60,0x64 irq 1
Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
ACPI: PCI interrupt 0000:00:1f.6[B] -> GSI 17 (level, low) -> IRQ 17
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
SLPB LID0 PCIB LANC MODM USB1 USB2 USB3 USB4 EUSB
ACPI: (supports S0 S3 S4 S5)
RAMDISK: cramfs filesystem found at block 0
RAMDISK: Loading 4524KiB [1 disk] into ram disk... done.
VFS: Mounted root (cramfs filesystem) readonly.
Freeing unused kernel memory: 164k freed
ACPI: CPU0 (power states: C1[C1] C2[C2])
ACPI: Processor [CPU0] (supports 8 throttling states)
ACPI: Thermal Zone [THM0] (74 C)
NET: Registered protocol family 1
Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
ICH5: IDE controller at PCI slot 0000:00:1f.1
PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
ACPI: PCI interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
ICH5: chipset revision 2
ICH5: not 100% native mode: will probe irqs later
    ide0: BM-DMA at 0x2060-0x2067, BIOS settings: hda:DMA, hdb:pio
    ide1: BM-DMA at 0x2068-0x206f, BIOS settings: hdc:DMA, hdd:pio
Probing IDE interface ide0...
hda: IC25N060ATMR04-0, ATA DISK drive
elevator: using anticipatory as default io scheduler
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
hda: max request size: 1024KiB
hda: 117210240 sectors (60011 MB) w/7884KiB Cache, CHS=16383/255/63, UDMA(100)
hda: cache flushes supported
 /dev/ide/host0/bus0/target0/lun0: p1 p2 p3 p4
Probing IDE interface ide1...
hdc: HL-DT-ST DVD+RW GCA-4040N, ATAPI CD/DVD-ROM drive
ide1 at 0x170-0x177,0x376 on irq 15
Probing IDE interface ide2...
Probing IDE interface ide3...
Probing IDE interface ide4...
Probing IDE interface ide5...
EXT3-fs: mounted filesystem with ordered data mode.
kjournald starting.  Commit interval 5 seconds
EXT3 FS on hda2, internal journal
hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache
Uniform CD-ROM driver Revision: 3.20
parport: PnPBIOS parport detected.
parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
lp0: using parport0 (interrupt-driven).
mice: PS/2 mouse device common for all mice
Synaptics Touchpad, model: 1
 Firmware: 13.8
 180 degree mounted touchpad
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
ts: Compaq touchscreen protocol output
Linux agpgart interface v0.100 (c) Dave Jones
nvidia: module license 'NVIDIA' taints kernel.
ACPI: PCI interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
NVRM: loading NVIDIA Linux x86 NVIDIA Kernel Module  1.0-7174  Tue Mar 22 06:44:39 PST 2005
acerhk: model string indicates it a medion MD40100
Acer Travelmate hotkey driver v0.5.3
Capability LSM initialized
device-mapper: 4.3.0-ioctl (2004-09-30) initialised: dm-devel@redhat.com
md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
cdrom: open failed.
Real Time Clock Driver v1.12
input: PC Speaker
agpgart: Detected an Intel 865 Chipset.
agpgart: Maximum main memory to use for agp memory: 439M
agpgart: AGP aperture is 128M @ 0x28000000
cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
shpchp: shpc_init : shpc_cap_offset == 0
shpchp: shpc_init : shpc_cap_offset == 0
shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Evaluate _OSC Set fails. Status = 0x0005
pciehp: add_host_bridge: status 5
pciehp: Fails to gain control of native hot-plug
usbcore: registered new driver usbfs
usbcore: registered new driver hub
USB Universal Host Controller Interface driver v2.2
ACPI: PCI interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
uhci_hcd 0000:00:1d.0: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #1
PCI: Setting latency timer of device 0000:00:1d.0 to 64
uhci_hcd 0000:00:1d.0: irq 16, io base 0x1cc0
uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
uhci_hcd 0000:00:1d.1: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #2
PCI: Setting latency timer of device 0000:00:1d.1 to 64
uhci_hcd 0000:00:1d.1: irq 19, io base 0x1ce0
uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
uhci_hcd 0000:00:1d.2: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #3
PCI: Setting latency timer of device 0000:00:1d.2 to 64
uhci_hcd 0000:00:1d.2: irq 18, io base 0x2000
uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
hub 3-0:1.0: USB hub found
hub 3-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:1d.3[A] -> GSI 16 (level, low) -> IRQ 16
uhci_hcd 0000:00:1d.3: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #4
PCI: Setting latency timer of device 0000:00:1d.3 to 64
uhci_hcd 0000:00:1d.3: irq 16, io base 0x2020
usb 2-2: new low speed USB device using uhci_hcd and address 2
uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
hub 4-0:1.0: USB hub found
hub 4-0:1.0: 2 ports detected
usbcore: registered new driver hiddev
input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.1-2
usbcore: registered new driver usbhid
drivers/usb/input/hid-core.c: v2.0:USB HID core driver
ACPI: PCI interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 23
ehci_hcd 0000:00:1d.7: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
PCI: Setting latency timer of device 0000:00:1d.7 to 64
ehci_hcd 0000:00:1d.7: irq 23, pci mem 0xd0000000
ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
PCI: cache line size of 128 is not supported by device 0000:00:1d.7
ehci_hcd 0000:00:1d.7: USB 2.0 initialized, EHCI 1.00, driver 26 Oct 2004
hub 5-0:1.0: USB hub found
hub 5-0:1.0: 8 ports detected
usb 5-2: new high speed USB device using ehci_hcd and address 2
Evaluate _OSC Set fails. Status = 0x0005
pciehp: add_host_bridge: status 5
pciehp: Fails to gain control of native hot-plug
hw_random hardware driver 1.0.0 loaded
Initializing USB Mass Storage driver...
scsi0 : SCSI emulation for USB Mass Storage devices
usbcore: registered new driver usb-storage
USB Mass Storage support registered.
usb 2-2: USB disconnect, address 2
usb-storage: device found at 2
usb-storage: waiting for device to settle before scanning
usb 2-2: new low speed USB device using uhci_hcd and address 3
input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.1-2
ACPI: PCI interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 17
PCI: Setting latency timer of device 0000:00:1f.5 to 64
intel8x0_measure_ac97_clock: measured 49107 usecs
intel8x0: clocking to 48000
Linux Kernel Card Services
  options:  [pci] [cardbus] [pm]
ACPI: PCI interrupt 0000:03:04.0[A] -> GSI 20 (level, low) -> IRQ 20
Yenta: CardBus bridge found at 0000:03:04.0 [17c0:17c0]
Yenta: ISA IRQ mask 0x0c78, PCI irq 20
Socket status: 30000006
ACPI: PCI interrupt 0000:03:04.1[B] -> GSI 21 (level, low) -> IRQ 21
Yenta: CardBus bridge found at 0000:03:04.1 [17c0:17c0]
Yenta: ISA IRQ mask 0x0c78, PCI irq 21
Socket status: 30000006
ohci1394: $Rev: 1223 $ Ben Collins <bcollins@debian.org>
ACPI: PCI interrupt 0000:03:04.2[C] -> GSI 23 (level, low) -> IRQ 23
ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[23]  MMIO=[d2007000-d20077ff]  Max Packet=[2048]
8139too Fast Ethernet driver 0.9.27
ACPI: PCI interrupt 0000:03:05.0[A] -> GSI 19 (level, low) -> IRQ 19
eth0: RealTek RTL8139 at 0x3000, 00:0a:e4:47:dd:ef, IRQ 19
eth0:  Identified 8139 chip type 'RTL-8101'
8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
Loaded prism54 driver, version 1.2
ACPI: PCI interrupt 0000:03:06.0[A] -> GSI 18 (level, low) -> IRQ 18
  Vendor: IC25N030  Model: ATDA04-0          Rev:  0 0
  Type:   Direct-Access                      ANSI SCSI revision: 00
usb-storage: device scan complete
SCSI device sda: 58605120 512-byte hdwr sectors (30006 MB)
sda: assuming drive cache: write through
SCSI device sda: 58605120 512-byte hdwr sectors (30006 MB)
sda: assuming drive cache: write through
 /dev/scsi/host0/bus0/target0/lun0:<7>eth1: resetting device...
eth1: uploading firmware...
ieee1394: Host added: ID:BUS[0-00:1023]  GUID[000ae40340101088]
eth1: firmware version: 1.0.4.3
eth1: firmware upload complete
 p1 < p5 p6 >
Attached scsi disk sda at scsi0, channel 0, id 0, lun 0
eth1: interface reset complete
NET: Registered protocol family 10
Disabled Privacy Extensions on device c0313ce0(lo)
IPv6 over IPv4 tunneling driver
ACPI: AC Adapter [AC] (on-line)
ACPI: Battery Slot [BAT0] (battery present)
ACPI: Power Button (FF) [PWRF]
ACPI: Sleep Button (CM) [SLPB]
ACPI: Lid Switch [LID0]
ibm_acpi: ec object not found
ACPI: Video Device [EVGA] (multi-head: yes  rom: no  post: no)
apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
apm: overridden by ACPI.
agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
ip_tables: (C) 2000-2002 Netfilter core team
ip_conntrack version 2.1 (4091 buckets, 32728 max) - 336 bytes per conntrack
eth1: no IPv6 routers present
cs: IO port probe 0x0100-0x04ff: excluding 0x4d0-0x4d7
cs: IO port probe 0x0800-0x08ff: clean.
cs: IO port probe 0x0c00-0x0cff: clean.
cs: IO port probe 0x0a00-0x0aff: clean.

```

and this is fdisk -l section of sda:

```

Disco /dev/sda: 30.0 GB, 30005821440 bytes
255 cabezas, 63 sectores/pista, 3648 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1               1        3648    29302528+   5  Extendida
/dev/sda5               1        1824    14651217   83  Linux
/dev/sda6            1825        3648    14651248+   b  W95 FAT32


```

---

### Post by guyforget on 2005-04-20
This frustrated me too.  I just moved the mountall script back in the order when booting.  

```
cd /etc/rcS.d/
sudo mv S35mountall.sh S60mountall.sh

```

---

### Post by Nano on 2005-04-20
[QUOTE=guyforget]This frustrated me too.  I just moved the mountall script back in the order when booting.  

```
cd /etc/rcS.d/
sudo mv S35mountall.sh S60mountall.sh

```[/QUOTE]
 Sometimes it amazes me how these simple things aren't solved yet...

---

