---
title: "USB hard drive not working"
date: 2005-03-03
forum: Hardware &amp; Laptops
---

### Post by Titanium on 2005-03-03
When I plug in a USB hard drive, nothing happens. It doesn't show up in /proc/bus/usb/devices (it should, right?). The controller driver seems to be working fine, I have no problems with my USB mouse.

The motherboard is an Asus A8N-SLI. I'm not sure if it's related, but System -> Administration -> Device Manager shows almost all devices as unknown, it can't even detect the processor type or memory properly, although the Advanced tab does show some useful strings.

Using 32bit Hoary Array5.

Thanks.

---

### Post by Titanium on 2005-03-04
Any pointers at all? Should I file a bug report? Do I need to provide some more information?

---

### Post by alastair on 2005-03-05
No idea - looks like unsupported hardware perhaps. Post :

- exact Ubuntu version
- uname -r
- output of "dmesg"

Has Linux worked on this h/w before?

---

### Post by Titanium on 2005-03-06
I reported this as [bug 7214](https://bugzilla.ubuntu.com/show_bug.cgi?id=7214), and posted all the details and a bunch of logs there. I'm now running an up-to-date 32bit Hoary. This is the first Linux on this hardware.

Here's the description from bugzilla (minus the logs):

"Hardware:
Asus A8N-SLI
Athlon64 3200+
1GB RAM
GeForce 6600GT PCIex
1 PATA HDD (OS)
2 SATA HDD
USB wireless bluetooth mouse and keyboard

Nothing happens when an external USB hard drive or camera (probably any USB
device) is plugged in. They do not show up in /proc/bus/usb/devices, nor is any
line appended to the system log. I do not notice any change, and the devices
aren't detected if they are plugged in during boot. The USB support itself seems
to be working because there are no problems with my Logitech diNovo USB
bluetooth mouse and keyboard. The only clue I've come across is the following
line in syslog, which consistently appears:
hal.hotplug[20084]: DEVPATH is not set"



```
$ uname -r
2.6.10-3-386
```

```
$ dmesg
I Interrupt Link [APC1] (IRQs *16), disabled.
ACPI: PCI Interrupt Link [APC2] (IRQs *17), disabled.
ACPI: PCI Interrupt Link [APC3] (IRQs *18), disabled.
ACPI: PCI Interrupt Link [APC4] (IRQs *19), disabled.
ACPI: PCI Interrupt Link [APC5] (IRQs *16), disabled.
ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0, disabled.
ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22 23) *0, disabled.
ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0, disabled.
ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22 23) *0, disabled.
ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22 23) *0, disabled.
ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0, disabled.
ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *"0, disabled.
ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0, disabled.
ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0, disabled.
ACPI: PCI Interrupt Link [APCP] (IRQs 20 21 22 23) *0, disabled.
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
pnp: 00:00: ioport range 0x4000-0x407f could not be reserved
pnp: 00:00: ioport range 0x4080-0x40ff has been reserved
pnp: 00:00: ioport range 0x4400-0x447f has been reserved
pnp: 00:00: ioport range 0x4480-0x44ff could not be reserved
pnp: 00:00: ioport range 0x4800-0x487f has been reserved
pnp: 00:00: ioport range 0x4880-0x48ff has been reserved
audit: initializing netlink socket (disabled)
audit(1110043664.281:0): initialized
VFS: Disk quotas dquot_6.5.1
Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
devfs: boot_options: 0x0
Initializing Cryptographic API
isapnp: Scanning for PnP cards...
isapnp: No Plug & Play device found
inotify device minor=63
serio: i8042 AUX port at 0x60,0x64 irq 12
serio: i8042 KBD port at 0x60,0x64 irq 1
Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
io scheduler noop registered
io scheduler anticipatory registered
io scheduler deadline registered
io scheduler cfq registered
RAMDISK driver initialized: 16 RAM disks of 8192K size 1024 blocksize
input: AT Translated Set 2 keyboard on isa0060/serio0
EISA: Probing bus 0 at eisa0
Cannot allocate resource for EISA slot 4
EISA: Detected 0 cards.
NET: Registered protocol family 2
IP: routing cache hash table of 8192 buckets, 64Kbytes
TCP: Hash tables configured (established 262144 bind 65536)
NET: Registered protocol family 8
NET: Registered protocol family 20
Restarting tasks...<6> Strange, kswapd0 not stopped
 Strange, kseriod not stopped
 done
ACPI wakeup devices:
HUB0 XVR0 XVR1 XVR2 XVR3 USB0 USB2 MMAC MMCI UAR1
ACPI: (supports S0 S1 S3 S4 S5)
RAMDISK: cramfs filesystem found at block 0
RAMDISK: Loading 4252KiB [1 disk] into ram disk... done.
VFS: Mounted root (cramfs filesystem) readonly.
Freeing unused kernel memory: 224k freed
ACPI: Fan [FAN] (on)
ACPI: Processor [CPU0] (supports 8 throttling states)
ACPI: Thermal Zone [THRM] (40 C)
NET: Registered protocol family 1
Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
NFORCE-CK804: IDE controller at PCI slot 0000:00:06.0
NFORCE-CK804: chipset revision 162
NFORCE-CK804: not 100% native mode: will probe irqs later
NFORCE-CK804: BIOS didn't set cable bits correctly. Enabling workaround.
NFORCE-CK804: 0000:00:06.0 (rev a2) UDMA133 controller
    ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:DMA
    ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdc:DMA, hdd:DMA
Probing IDE interface ide0...
hda: Maxtor 6Y080L0, ATA DISK drive
elevator: using anticipatory as default io scheduler
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
hda: max request size: 128KiB
hda: 160086528 sectors (81964 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(133)
hda: cache flushes supported
 /dev/ide/host0/bus0/target0/lun0: p1 p2 p3 p4
Probing IDE interface ide1...
hdc: PIONEER DVD-RW DVR-108, ATAPI CD/DVD-ROM drive
hdd: HL-DT-ST GCE-8160B, ATAPI CD/DVD-ROM drive
ide1 at 0x170-0x177,0x376 on irq 15
Probing IDE interface ide2...
Probing IDE interface ide3...
Probing IDE interface ide4...
Probing IDE interface ide5...
EXT3-fs: mounted filesystem with ordered data mode.
kjournald starting.  Commit interval 5 seconds
Adding 1052248k swap on /dev/hda2.  Priority:-1 extents:1
EXT3 FS on hda1, internal journal
hdc: ATAPI 32X DVD-ROM DVD-R CD-R/RW drive, 2000kB Cache
Uniform CD-ROM driver Revision: 3.20
hdd: ATAPI 40X CD-ROM CD-R/RW drive, 2048kB Cache
parport: PnPBIOS parport detected.
parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
lp0: using parport0 (interrupt-driven).
mice: PS/2 mouse device common for all mice
nvidia: module license 'NVIDIA' taints kernel.
ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
ACPI: PCI interrupt 0000:01:00.0[A] -> GSI 18 (level, low) -> IRQ 18
PCI: Setting latency timer of device 0000:01:00.0 to 64
NVRM: loading NVIDIA Linux x86 NVIDIA Kernel Module  1.0-6629  Wed Nov  3 13:12:51 PST 2004
Capability LSM initialized
device-mapper: 4.3.0-ioctl (2004-09-30) initialised: [email]dm-devel@redhat.com[/email]
md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
kjournald starting.  Commit interval 5 seconds
EXT3 FS on hda4, internal journal
EXT3-fs: mounted filesystem with ordered data mode.
NTFS driver 2.1.22 [Flags: R/O MODULE].
Real Time Clock Driver v1.12
input: PC Speaker
inserting floppy driver for 2.6.10-3-386
Floppy drive(s): fd0 is 1.44M
FDC 0 is a post-1991 82077
usbcore: registered new driver usbfs
usbcore: registered new driver hub
ohci_hcd: 2004 Nov 08 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
ACPI: PCI Interrupt Link [APCF] enabled at IRQ 23
ACPI: PCI interrupt 0000:00:02.0[A] -> GSI 23 (level, low) -> IRQ 23
ohci_hcd 0000:00:02.0: PCI device 10de:005a (nVidia Corporation)
PCI: Setting latency timer of device 0000:00:02.0 to 64
ohci_hcd 0000:00:02.0: irq 23, pci mem 0xd2004000
ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 10 ports detected
usb 1-2: new full speed USB device using ohci_hcd and address 2
ACPI: PCI Interrupt Link [APCL] enabled at IRQ 22
ACPI: PCI interrupt 0000:00:02.1[B] -> GSI 22 (level, low) -> IRQ 22
ehci_hcd 0000:00:02.1: PCI device 10de:005b (nVidia Corporation)
PCI: Setting latency timer of device 0000:00:02.1 to 64
ehci_hcd 0000:00:02.1: irq 22, pci mem 0xd2005000
ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
PCI: cache line size of 64 is not supported by device 0000:00:02.1
ehci_hcd 0000:00:02.1: USB 2.0 initialized, EHCI 1.00, driver 26 Oct 2004
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 4 ports detected
usb 1-2: new full speed USB device using ohci_hcd and address 3
hub 1-2:1.0: USB hub found
hub 1-2:1.0: 2 ports detected
ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 21
ACPI: PCI interrupt 0000:00:04.0[A] -> GSI 21 (level, low) -> IRQ 21
PCI: Setting latency timer of device 0000:00:04.0 to 64
usb 1-2.1: new low speed USB device using ohci_hcd and address 4
intel8x0_measure_ac97_clock: measured 122256 usecs
intel8x0: clocking to 48000
usbcore: registered new driver hiddev
input: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:02.0-2.1
input,hiddev96: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:02.0-2.1
usbcore: registered new driver usbhid
drivers/usb/input/hid-core.c: v2.0:USB HID core driver
ts: Compaq touchscreen protocol output
SCSI subsystem initialized
libata version 1.10 loaded.
sata_nv version 0.5
ACPI: PCI Interrupt Link [APSI] enabled at IRQ 20
ACPI: PCI interrupt 0000:00:07.0[A] -> GSI 20 (level, low) -> IRQ 20
PCI: Setting latency timer of device 0000:00:07.0 to 64
ata1: SATA max UDMA/133 cmd 0x9F0 ctl 0xBF2 bmdma 0xD800 irq 20
ata2: SATA max UDMA/133 cmd 0x970 ctl 0xB72 bmdma 0xD808 irq 20
ata1: dev 0 cfg 49:2f00 82:7c6b 83:7f09 84:4063 85:7c69 86:3e01 87:4063 88:407f
ata1: dev 0 ATA, max UDMA/133, 398297088 sectors: lba48
nv_sata: Primary device added
nv_sata: Primary device removed
nv_sata: Secondary device added
nv_sata: Secondary device removed
ata1: dev 0 configured for UDMA/133
scsi0 : sata_nv
ata2: no device found (phy stat 00000000)
scsi1 : sata_nv
  Vendor: ATA       Model: Maxtor 6B200M0    Rev: BANC
  Type:   Direct-Access                      ANSI SCSI revision: 05
ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 23
ACPI: PCI interrupt 0000:00:08.0[A] -> GSI 23 (level, low) -> IRQ 23
PCI: Setting latency timer of device 0000:00:08.0 to 64
ata3: SATA max UDMA/133 cmd 0x9E0 ctl 0xBE2 bmdma 0xC400 irq 23
ata4: SATA max UDMA/133 cmd 0x960 ctl 0xB62 bmdma 0xC408 irq 23
SCSI device sda: 398297088 512-byte hdwr sectors (203928 MB)
SCSI device sda: drive cache: write back
SCSI device sda: 398297088 512-byte hdwr sectors (203928 MB)
SCSI device sda: drive cache: write back
 /dev/scsi/host0/bus0/target0/lun0: p1 < p5 > p2
Attached scsi disk sda at scsi0, channel 0, id 0, lun 0
ata3: dev 0 cfg 49:2f00 82:7c6b 83:7f09 84:4063 85:7c69 86:3e01 87:4063 88:407f
ata3: dev 0 ATA, max UDMA/133, 398297088 sectors: lba48
nv_sata: Primary device added
nv_sata: Primary device removed
nv_sata: Secondary device added
nv_sata: Secondary device removed
ata3: dev 0 configured for UDMA/133
scsi2 : sata_nv
ata4: no device found (phy stat 00000000)
scsi3 : sata_nv
  Vendor: ATA       Model: Maxtor 6B200M0    Rev: BANC
  Type:   Direct-Access                      ANSI SCSI revision: 05
SCSI device sdb: 398297088 512-byte hdwr sectors (203928 MB)
SCSI device sdb: drive cache: write back
SCSI device sdb: 398297088 512-byte hdwr sectors (203928 MB)
SCSI device sdb: drive cache: write back
 /dev/scsi/host2/bus0/target0/lun0:<4>nv_sata: Primary device added
nv_sata: Primary device removed
nv_sata: Secondary device added
nv_sata: Secondary device removed
 p1 p2
Attached scsi disk sdb at scsi2, channel 0, id 0, lun 0
forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.30.
ACPI: PCI Interrupt Link [APCH] enabled at IRQ 22
ACPI: PCI interrupt 0000:00:0a.0[A] -> GSI 22 (level, low) -> IRQ 22
PCI: Setting latency timer of device 0000:00:0a.0 to 64
eth0: forcedeth.c: subsystem: 01043:8141 bound to 0000:00:0a.0
cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
shpchp: shpc_init : shpc_cap_offset == 0
shpchp: shpc_init : shpc_cap_offset == 0
shpchp: shpc_init : shpc_cap_offset == 0
shpchp: shpc_init : shpc_cap_offset == 0
shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Evaluate _OSC Set fails. Status = 0x0005
pciehp: add_host_bridge: status 5
pciehp: Fails to gain control of native hot-plug
Evaluate _OSC Set fails. Status = 0x0005
pciehp: add_host_bridge: status 5
pciehp: Fails to gain control of native hot-plug
Evaluate _OSC Set fails. Status = 0x0005
pciehp: add_host_bridge: status 5
pciehp: Fails to gain control of native hot-plug
Evaluate _OSC Set fails. Status = 0x0005
pciehp: add_host_bridge: status 5
pciehp: Fails to gain control of native hot-plug
Linux video capture interface: v1.00
saa7130/34: v4l2 driver version 0.2.12 loaded
ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
ACPI: PCI interrupt 0000:05:06.0[A] -> GSI 16 (level, low) -> IRQ 16
saa7134[0]: found at 0000:05:06.0, rev: 1, irq: 16, latency: 32, mmio: 0xd1004000
saa7134[0]: subsystem: 153b:1142, board: Terratec Cinergy 400 TV [card=8,autodetected]
saa7134[0]: board init: gpio is 50000
saa7134[0]: registered input device for IR
saa7134[0]: i2c eeprom 00: 3b 15 42 11 ff ff ff ff ff ff ff ff ff ff ff ff
saa7134[0]: i2c eeprom 10: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
saa7134[0]: i2c eeprom 20: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
saa7134[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
tuner: chip found at addr 0xc0 i2c-bus saa7134[0]
tuner: type set to 5 (Philips PAL_BG (FI1216 and compatibles)) by saa7134[0]
saa7134[0]: registered device video0 [v4l2]
saa7134[0]: registered device vbi0
ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
ACPI: PCI interrupt 0000:05:0c.0[A] -> GSI 17 (level, low) -> IRQ 17
ACPI: PCI interrupt 0000:05:0c.0[A] -> GSI 17 (level, low) -> IRQ 17
eth1: Yukon Gigabit Ethernet 10/100/1000Base-T Adapter
      PrefPort:A  RlmtMode:Check Link State
ACPI: Power Button (FF) [PWRF]
ibm_acpi: ec object not found
drivers/usb/input/hid-input.c: event field not found
drivers/usb/input/hid-input.c: event field not found
apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
apm: overridden by ACPI.
powernow-k8: Found 1 AMD Athlon 64 / Opteron processors (version 1.00.09e)
powernow-k8:    0 : fid 0xc (2000 MHz), vid 0x6 (1400 mV)
powernow-k8:    1 : fid 0xa (1800 MHz), vid 0x8 (1350 mV)
powernow-k8:    2 : fid 0x2 (1000 MHz), vid 0x12 (1100 mV)
cpu_init done, current fid 0xc, vid 0x8
powernow-k8: ph2 null fid transition 0xc
NET: Registered protocol family 10
Disabled Privacy Extensions on device c02ef500(lo)
IPv6 over IPv4 tunneling driver
UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'suse92addons', timestamp 2005/02/21 22:33 (103c)
UDF-fs: No VRS found
ISO 9660 Extensions: Microsoft Joliet Level 3
ISOFS: changing to secondary root
CSLIP: code copyright 1989 Regents of the University of California
PPP generic driver version 2.4.2
PPP BSD Compression module registered
PPP Deflate Compression module registered
NTFS volume version 3.1.
NTFS volume version 3.1.
hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
ide: failed opcode was: unknown
hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
ide: failed opcode was: unknown
saa7134[0]/audio: audio carrier scan failed, using 5.500 MHz [last detected]
saa7134[0]/audio: audio carrier scan failed, using 5.500 MHz [last detected]
ibm_acpi: ec object not found
NTFS-fs error (device sda2): ntfs_ucstonls(): Unicode name contains characters that cannot be converted to character set cp437.
NTFS-fs error (device sda2): ntfs_ucstonls(): Unicode name contains characters that cannot be converted to character set cp437.
NTFS-fs error (device sdb2): ntfs_ucstonls(): Unicode name contains characters that cannot be converted to character set cp437.
NTFS-fs error (device sdb2): ntfs_ucstonls(): Unicode name contains characters that cannot be converted to character set cp437.
```

---

### Post by dikki on 2005-03-06
What's the output of dmesg after powering up the HDD? Did you edit the fstab file?

---

### Post by Roger Dunder on 2005-03-06
try this.

plug the usb hdd in.
go to /dev
and see if you have an sd?1
try to mount that one,  

worked for me! :)

---

### Post by Titanium on 2005-03-06
[QUOTE=dikki]What's the output of dmesg after powering up the HDD? Did you edit the fstab file?[/QUOTE]
There's absolutely no change in the system log when plugging in or out the hard drive or camera. I don't think there's any point in editing the fstab file when there's nothing to mount, no?

[QUOTE=Roger Dunder]plug the usb hdd in.
go to /dev
and see if you have an sd?1
try to mount that one,[/QUOTE]
No additional sd? devices appear when after plugging it in. There are only my SATA drives, sda and sdb. I guess the USB drives should start from sdc, but they don't.

---

### Post by alastair on 2005-03-06
The reason I asked for "dmesg" etc. was really when you said :

"it can't even detect the processor type or memory properly"

Unfortunately, the first few log lines are missing i.e. where we detect processor etc.

No change in syslog log when you plug in the USB HDD sounds bad - I usually :

sudo tail -f /var/log/syslog

to see any messages - then plug the drive in.

You could try booting the kernel with args :

acpi=off pci=routeirq noapic

perhaps.

---

### Post by Titanium on 2005-03-06
[QUOTE=alastair]The reason I asked for "dmesg" etc. was really when you said :

"it can't even detect the processor type or memory properly"

Unfortunately, the first few log lines are missing i.e. where we detect processor etc.
[/QUOTE]
I believe that the processor is being detected properly, just the Device Manager doesn't know about it, because the correct processor name is shown on the other tab in DM, and the powernow_k8 module is automatically loaded. I can't check any of this now, because Device Manager refuses to start (bug #7188), but I don't think that has anything to do with the USB problem.

> No change in syslog log when you plug in the USB HDD sounds bad - I usually :

sudo tail -f /var/log/syslog

to see any messages - then plug the drive in.

I've just tried that -- no messages at all when [un]plugging the drive. I've never had any USB problems before on my previous computers, not even 4 years ago when USB support was still relatively new.

> You could try booting the kernel with args :

acpi=off pci=routeirq noapic

perhaps.
I'll try this later and get back with the results.

---

### Post by lorap on 2005-03-07
hi,
i've the same problem with my external usb cdrom and i, like you, have a usb mouse that's working very good.probably they do have some problems with external usb storage support.don't think there's any difference between usb hard drive & cdrom.especially it's a r/w cd so let's keep in touch.if i've this problem solved then you'd too & if you do then let me know in what way.
pavel

---

### Post by Titanium on 2005-03-07
[QUOTE=alastair]You could try booting the kernel with args :

acpi=off pci=routeirq noapic[/QUOTE]

I've just tried this. Adding "acpi=off" results in locking up during boot when "Starting hotplug subsystem..." appears. The other two options don't seem to have any effect on the system.

[QUOTE=lorap]i've the same problem with my external usb cdrom and i, like you, have a usb mouse that's working very good.probably they do have some problems with external usb storage support.[/QUOTE]

That's what I think as well. What kind of hardware do you have and which version of Ubuntu are you running?

---

### Post by Titanium on 2005-03-09
I figured out why the USB input peripherals work -- only the 2 USB ports on the back of the motherboard work properly. Plugging the hard drive into one of them results in a USB icon on the Gnome desktop and everything working as expected.

The symptoms described apply to the expansion USB ports which are connected to appropriate pins on the motherboard. The cabling is OK, because there are no similar functionality issues in Windows.

---

### Post by Cannon on 2005-03-11
[QUOTE=Titanium]I figured out why the USB input peripherals work -- only the 2 USB ports on the back of the motherboard work properly. Plugging the hard drive into one of them results in a USB icon on the Gnome desktop and everything working as expected.

The symptoms described apply to the expansion USB ports which are connected to appropriate pins on the motherboard. The cabling is OK, because there are no similar functionality issues in Windows.[/QUOTE]

Hello,
I'm using the Gigabyte K8N Ultra-SLI built with NForce4 SLI chipset and encouter the same problem of USB 2.0. I just read the articles on the internet (sorry for missing the URL) and somebody said that's the bug of NForce4 SLI chipset. Please downgrade to the 2.6.8 kernel (but it will make your sound hardware unrecognized :-( )or try remove the ehci_hcd module in kernel 2.6.10, and you will find the USB works correctly. :o

---

### Post by Titanium on 2005-03-11
[QUOTE=Cannon]Hello,
I'm using the Gigabyte K8N Ultra-SLI built with NForce4 SLI chipset and encouter the same problem of USB 2.0. I just read the articles on the internet (sorry for missing the URL) and somebody said that's the bug of NForce4 SLI chipset. Please downgrade to the 2.6.8 kernel (but it will make your sound hardware unrecognized :-( )or try remove the ehci_hcd module in kernel 2.6.10, and you will find the USB works correctly. :o[/QUOTE]
Thanks for this -- now we seem to have localized the problem. Indeed, the hard disk was detected after removing ehci_hcd. I just don't understand how this can be a chipset bug, it may have some quirks, but if both an earlier kernel and Windows detect the ports correctly, then it seems to me that it is a 2.6.10 kernel bug.

I found some discussions on a Linux USB mailing list about this problem, maybe this is where you read about it?

[[linux-usb-devel] EHCI not detecting devices in 2.6.10 on nForce4](http://www.mail-archive.com/linux-usb-devel@lists.sourceforge.net/msg32426.html) 
[[linux-usb-devel] Kingston USB 2.0 pen drive not working properly in 2.6.10](http://www.mail-archive.com/linux-usb-devel@lists.sourceforge.net/msg32440.html)

---

### Post by rolfpal on 2005-03-11
Hi there, I had some very similar problems with my firewire/usb drive.

I eventually solved them by adding:

sbp2 serialize_io=1

to /etc/modules

My theory is that some/(cheap) chipsets do not emulate scsi very well and they need to be given data in a more ordered way.  At any rate the drive works well now, but it is slow (in hoary).

Cheers,

---

### Post by Titanium on 2005-03-15
This issue has been fixed in the latest kernel in the repositories.

---

### Post by LichiMan on 2005-03-16
Thanks! I'll try it when I come back at home.

---

### Post by steffen on 2005-03-22
I had to do modprobe --remove ehci_hcd as well - and my USB HD works perfectly.

How do I do this permanent? I have to redo it after each reboot.

---

### Post by moa on 2005-03-23
I have almost the same problem. Am running hoary on an ASUS S1300N laptop & a dual althon tyan thunder scsi system. My scsi drives & usb mouse are recognised. my usb hd is not. usb-storage is present on dmseg, but can't get /dev/sdc.

Ram usb sticks work perfectly if formatted to ext3 or vfat: ntfs sticks are (as usual) read-only.

I need to able to find the darn drive so I can format, and put my music on it...

Chris.

---

