---
title: "Windows NTFS partition won't mount?"
date: 2005-10-04
forum: Hardware &amp; Laptops
---

### Post by eXcentra on 2005-10-04
At first, I've been trying to boot into my Windows XP partition and trying to solve that problem (as you can see [here](http://ubuntuforums.org/showthread.php?t=71302)) but I found out that I couldn't even mount the partition. 
I try mounting it and get the following:
```

mount: wrong fs type, bad option, bad superblock on /dev/hda2,
missing codepage or other error
In some cases useful info is found in syslog - try
dmesg | tail  or so

```Any variation of the mount command will not work. I've tried many different ways...
So I type in dmesg and get the following:
```

6>ACPI: PCI interrupt 0000:00:14.1[A] -> GSI 10 (level, low) -> IRQ 10
ATIIXP: chipset revision 0
ATIIXP: not 100% native mode: will probe irqs later
ide0: BM-DMA at 0x8070-0x8077, BIOS settings: hda:DMA, hdb:pio
ide1: BM-DMA at 0x8078-0x807f, BIOS settings: hdc:DMA, hdd:pio
Probing IDE interface ide0...
hda: FUJITSU MHT2080AT, ATA DISK drive
elevator: using anticipatory as default io scheduler
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
hda: max request size: 128KiB
hda: 156301488 sectors (80026 MB) w/8192KiB Cache, CHS=65535/16/63, UDMA(100)
hda: cache flushes supported
/dev/ide/host0/bus0/target0/lun0: p1 p2 p3 p4 < p5 p6 >
Probing IDE interface ide1...
hdc: TSSTcorpCDW/DVD TS-L462A, ATAPI CD/DVD-ROM drive
ide1 at 0x170-0x177,0x376 on irq 15
Probing IDE interface ide2...
Probing IDE interface ide3...
Probing IDE interface ide4...
Probing IDE interface ide5...
Stopping tasks: ==|
Freeing memory... done (455 pages freed)
Restarting tasks... done
EXT3-fs: mounted filesystem with ordered data mode.
kjournald starting.  Commit interval 5 seconds
Adding 1461872k swap on /dev/hda5.  Priority:-1 extents:1
EXT3 FS on hda3, internal journal
hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache
Uniform CD-ROM driver Revision: 3.20
lp: driver loaded but no devices found
mice: PS/2 mouse device common for all mice
Synaptics Touchpad, model: 1
Firmware: 5.9
Sensor: 37
new absolute packet format
Touchpad has extended capability bits
-> multifinger detection
-> palm detection
input: SynPS/2 Synaptics TouchPad on isa0060/serio4
Capability LSM initialized
ts: Compaq touchscreen protocol output
device-mapper: 4.3.0-ioctl (2004-09-30) initialised: dm-devel@redhat.com
md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
cdrom: open failed.
NTFS driver 2.1.22 [Flags: R/O MODULE].
NTFS-fs error (device hda2): read_ntfs_boot_sector(): Primary boot sector is invalid.
NTFS-fs error (device hda2): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
NTFS-fs error (device hda2): ntfs_fill_super(): Not an NTFS volume.
Real Time Clock Driver v1.12
input: PC Speaker
Linux agpgart interface v0.100 (c) Dave Jones
agpgart: Detected Ati IGP9100/M chipset
agpgart: Maximum main memory to use for agp memory: 627M
agpgart: AGP aperture is 64M @ 0xdc000000
cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
shpchp: shpc_init : shpc_cap_offset == 0
shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
Evaluate _OSC Set fails. Status = 0x0005
pciehp: add_host_bridge: status 5
pciehp: Fails to gain control of native hot-plug
ACPI: PCI interrupt 0000:00:14.5[B] -> GSI 5 (level, low) -> IRQ 5
ACPI: PCI interrupt 0000:00:14.6[B] -> GSI 5 (level, low) -> IRQ 5
ath_hal: module license 'Proprietary' taints kernel.
ath_hal: 0.9.12.14 (AR5210, AR5211, AR5212)
wlan: 0.8.4.5 (EXPERIMENTAL)
ath_rate_onoe: 1.0
ath_pci: 0.9.4.12 (EXPERIMENTAL)
ACPI: PCI Interrupt Link [LNK2] enabled at IRQ 6
PCI: setting IRQ 6 as level-triggered
ACPI: PCI interrupt 0000:02:03.0[A] -> GSI 6 (level, low) -> IRQ 6
ath0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
ath0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
ath0: mac 5.9 phy 4.3 radio 4.6
ath0: 802.11 address: 00:02:78:42:4b:23
ath0: Use hw queue 0 for WME_AC_BE traffic
ath0: Use hw queue 1 for WME_AC_BK traffic
ath0: Use hw queue 2 for WME_AC_VI traffic
ath0: Use hw queue 3 for WME_AC_VO traffic
ath0: Atheros 5212: mem=0xd8200000, irq=6
Linux Kernel Card Services
options:  [pci] [cardbus] [pm]
ACPI: PCI interrupt 0000:02:04.0[A] -> GSI 10 (level, low) -> IRQ 10
Yenta: CardBus bridge found at 0000:02:04.0 [144d:b028]
Yenta: ISA IRQ mask 0x0098, PCI irq 10
Socket status: 30000006
b44.c:v0.95 (Aug 3, 2004)
ACPI: PCI interrupt 0000:02:05.0[A] -> GSI 6 (level, low) -> IRQ 6
eth0: Broadcom 4400 10/100BaseT Ethernet 00:00:f0:73:cd:c2
usbcore: registered new driver usbfs
usbcore: registered new driver hub
ohci_hcd: 2004 Nov 08 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
ACPI: PCI Interrupt Link [LNK3] enabled at IRQ 11
PCI: setting IRQ 11 as level-triggered
ACPI: PCI interrupt 0000:02:06.0[A] -> GSI 11 (level, low) -> IRQ 11
ohci_hcd 0000:02:06.0: NEC Corporation USB
ohci_hcd 0000:02:06.0: irq 11, pci mem 0xd8210000
ohci_hcd 0000:02:06.0: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 3 ports detected
ACPI: PCI interrupt 0000:02:06.1[B] -> GSI 6 (level, low) -> IRQ 6
ohci_hcd 0000:02:06.1: NEC Corporation USB (#2)
ohci_hcd 0000:02:06.1: irq 6, pci mem 0xd8211000
ohci_hcd 0000:02:06.1: new USB bus registered, assigned bus number 2
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 2 ports detected
usb 1-2: new low speed USB device using ohci_hcd and address 2
ACPI: PCI interrupt 0000:02:06.2[C] -> GSI 5 (level, low) -> IRQ 5
ehci_hcd 0000:02:06.2: NEC Corporation USB 2.0
ehci_hcd 0000:02:06.2: irq 5, pci mem 0xd8212000
ehci_hcd 0000:02:06.2: new USB bus registered, assigned bus number 3
ehci_hcd 0000:02:06.2: USB 2.0 initialized, EHCI 1.00, driver 26 Oct 2004
hub 3-0:1.0: USB hub found
hub 3-0:1.0: 5 ports detected
usbcore: registered new driver hiddev
usbhid: probe of 1-2:1.0 failed with error -5
usbcore: registered new driver usbhid
drivers/usb/input/hid-core.c: v2.0:USB HID core driver
usb 1-2: USB disconnect, address 2
usb 1-2: new low speed USB device using ohci_hcd and address 3
b44: eth0: Link is down.
input: USB HID v1.10 Mouse [USB Mouse              ] on usb-0000:02:06.0-2
NET: Registered protocol family 17
b44: eth0: Link is up at 100 Mbps, full duplex.
b44: eth0: Flow control is off for TX and off for RX.
NET: Registered protocol family 10
Disabled Privacy Extensions on device c02f0500(lo)
IPv6 over IPv4 tunneling driver
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: AC Adapter [ADP1] (on-line)
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: Battery Slot [BAT1] (battery present)
ACPI: Power Button (FF) [PWRF]
ACPI: Sleep Button (CM) [SLPB]
ACPI: Lid Switch [LID0]
ibm_acpi: ec object not found
ACPI: Video Device [ATIM] (multi-head: yes  rom: no  post: no)
apm: BIOS version 1.2 Flags 0x0b (Driver version 1.16ac)
apm: overridden by ACPI.
[drm] Initialized drm 1.0.0 20040925
ACPI: PCI interrupt 0000:01:05.0[A] -> GSI 10 (level, low) -> IRQ 10
[drm] Initialized radeon 1.14.0 20050125 on minor 0: PCI device 1002:5835 (ATI Technologies Inc)
agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
agpgart: Xorg passes broken AGP3 flags (1f00020f). Fixed.
agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
agpgart: Putting AGP V3 device at 0000:01:05.0 into 8x mode
[drm] Loading R200 Microcode
cs: IO port probe 0x0100-0x04ff: clean.
cs: IO port probe 0x0800-0x08ff: clean.
cs: IO port probe 0x0c00-0x0cff: excluding 0xc00-0xc07 0xc10-0xc17 0xc50-0xc57 0xc68-0xc6f 0xcd0-0xcd7
cs: IO port probe 0x0a00-0x0aff: clean.
speedstep-centrino: invalid ACPI data
speedstep-centrino: no table support for CPU model "Intel(R) Pentium(R) M processor 1.60GHz":
acpi-cpufreq: CPU0 - ACPI performance management activated.
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
eth0: no IPv6 routers present
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
NTFS-fs error (device hda2): read_ntfs_boot_sector(): Primary boot sector is invalid.
NTFS-fs error (device hda2): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
NTFS-fs error (device hda2): ntfs_fill_super(): Not an NTFS volume.
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
NTFS-fs error (device hda2): read_ntfs_boot_sector(): Primary boot sector is invalid.
NTFS-fs error (device hda2): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
NTFS-fs error (device hda2): ntfs_fill_super(): Not an NTFS volume.
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8
NTFS-fs error (device hda2): read_ntfs_boot_sector(): Primary boot sector is invalid.
NTFS-fs error (device hda2): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
NTFS-fs error (device hda2): ntfs_fill_super(): Not an NTFS volume.
ACPI: acpi_ec_space_handler: bit_width should be 8
ACPI: acpi_ec_space_handler: bit_width should be 8

```
I've tried adding this to my fstab:
```

/dev/hda1 /mnt/hda1 ntfs noatime,defaults,users,ro,umask=0 0 0

```
and during Ubuntu boot up when it says it's mounting the filesystems, it gives me that "mount: wrong fs type" error. But when I go to Places --> Computer, I see a drive that says "31G Drive" which must mean that it detects the partition in some way, right? Is there any way I can access this thing?

What I want to do is copy some files from the Windows partition into my empty FAT32 partition or my mp3 player.

---

### Post by User-007 on 2005-10-04
Maybe you should edit fstab following this way...

```


sudo mkdir /mnt/hda1
/dev/hda1       /mnt/hda1 ntfs    nls=utf8,umask=0222 0       0


```

Hope this helps
Pate

---

### Post by eXcentra on 2005-10-04
Tried it out and it didn't work. :| I get the same error message. 
"/dev/hda1 /mnt/hda1 ntfs noatime,defaults,users,ro,umask=0 0 0" is still the closest one so far.

---

