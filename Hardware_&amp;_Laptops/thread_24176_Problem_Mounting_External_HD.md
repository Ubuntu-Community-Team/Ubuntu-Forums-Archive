---
title: "Problem Mounting External HD"
date: 2005-04-05
forum: Hardware &amp; Laptops
---

### Post by chien on 2005-04-05
Hi Everyone,

I'm having a serious problem in trying to mount my external Hard Drive. It is a Bafo 2010 with a 80gb hard disk, formatted in ntfs.

fdisk -l shows

root@chien:/ # fdisk -l

Disk /dev/hda: 10.0 GB, 10056130560 bytes
255 heads, 63 sectors/track, 1222 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hda1 * 1 489 3927861 b W95 FAT32
/dev/hda2 490 1062 4602622+ 83 Linux
/dev/hda4 1063 1222 1285200 f W95 Ext'd (LBA)
/dev/hda5 1093 1222 1044193+ b W95 FAT32
/dev/hda6 1063 1092 240912 82 Linux swap / Solaris

Partition table entries are not in disk order



fdisk -l doesn't detect my external hard drive, it only detect my internal one, which has 6 partitions.



dmesg shows:

Linux version 2.6.10-4-386 (buildd@mcmurdo) (gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)) #1 Sat Mar 12 11:09:25 GMT 2005
BIOS-provided physical RAM map:
BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
BIOS-e820: 00000000000e5800 - 0000000000100000 (reserved)
BIOS-e820: 0000000000100000 - 000000001fe70000 (usable)
BIOS-e820: 000000001fe70000 - 000000001fe7f800 (ACPI data)
BIOS-e820: 000000001fe7f800 - 000000001fe80000 (ACPI NVS)
BIOS-e820: 000000001fe80000 - 0000000020000000 (reserved)
BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
510MB LOWMEM available.
On node 0 totalpages: 130672
DMA zone: 4096 pages, LIFO batch:1
Normal zone: 126576 pages, LIFO batch:16
HighMem zone: 0 pages, LIFO batch:1
DMI present.
Built 1 zonelists
Kernel command line: root=/dev/hda2 ro acpi=off quiet splash
Local APIC disabled by BIOS -- you can enable it with "lapic"
mapped APIC to ffffd000 (01403000)
Initializing CPU#0
PID hash table entries: 2048 (order: 11, 32768 bytes)
Detected 695.776 MHz processor.
Using tsc for high-res timesource
Console: colour VGA+ 80x25
Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
Memory: 510620k/522688k available (1435k kernel code, 11468k reserved, 755k data, 224k init, 0k highmem)
Checking if this processor honours the WP bit even in supervisor mode... Ok.
Calibrating delay loop... 1372.16 BogoMIPS (lpj=686080)
Security Framework v1.0.0 initialized
SELinux: Disabled at boot.
Mount-cache hash table entries: 512 (order: 0, 4096 bytes)
CPU: After generic identify, caps: 0387f9ff 00000000 00000000 00000000 00000000 00000000
CPU: After vendor identify, caps: 0387f9ff 00000000 00000000 00000000 00000000 00000000
CPU: L1 I cache: 16K, L1 D cache: 16K
CPU: L2 cache: 256K
CPU serial number disabled.
CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 00000000 00000000
CPU: Intel Pentium III (Coppermine) stepping 06
Enabling fast FPU save and restore... done.
Enabling unmasked SIMD FPU exception support... done.
Checking 'hlt' instruction... OK.
Checking for popad bug... OK.
checking if image is initramfs...it isn't (bad gzip magic numbers); looks like an initrd
Freeing initrd memory: 4300k freed
NET: Registered protocol family 16
EISA bus registered
PCI: PCI BIOS revision 2.10 entry at 0xfd9b0, last bus=1
PCI: Using configuration type 1
mtrr: v2.0 (20020519)
ACPI: Subsystem revision 20050211
ACPI: Interpreter disabled.
Linux Plug and Play Support v0.97 (c) Adam Belay
pnp: PnP ACPI: disabled
PnPBIOS: Scanning system for PnP BIOS support...
PnPBIOS: Found PnP BIOS installation structure at 0xc00f7470
PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xa899, dseg 0x400
PnPBIOS: 19 nodes reported by PnP BIOS; 19 recorded by driver
PCI: Probing PCI hardware
PCI: Probing PCI hardware (bus 00)
PCI: Transparent bridge - 0000:00:1e.0
PCI: Using IRQ router PIIX/ICH [8086/244c] at 0000:00:1f.0
pnp: 00:0a: ioport range 0x4d0-0x4d1 has been reserved
pnp: 00:0a: ioport range 0x1000-0x105f has been reserved
pnp: 00:0a: ioport range 0x1100-0x110f has been reserved
pnp: 00:0a: ioport range 0x1060-0x107f has been reserved
pnp: 00:0a: ioport range 0x1180-0x11bf has been reserved
audit: initializing netlink socket (disabled)
audit(1112715507.297:0): initialized
VFS: Disk quotas dquot_6.5.1
Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
devfs: boot_options: 0x0
Initializing Cryptographic API
isapnp: Scanning for PnP cards...
isapnp: No Plug & Play device found
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
Cannot allocate resource for EISA slot 1
Cannot allocate resource for EISA slot 2
EISA: Detected 0 cards.
NET: Registered protocol family 2
IP: routing cache hash table of 4096 buckets, 32Kbytes
TCP: Hash tables configured (established 32768 bind 65536)
NET: Registered protocol family 8
NET: Registered protocol family 20
Restarting tasks...<6> Strange, kswapd0 not stopped
Strange, kpnpbiosd not stopped
Strange, kseriod not stopped
done
RAMDISK: cramfs filesystem found at block 0
RAMDISK: Loading 4300KiB [1 disk] into ram disk... |/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|done.
VFS: Mounted root (cramfs filesystem) readonly.
Freeing unused kernel memory: 224k freed
NET: Registered protocol family 1
Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
ICH2M: IDE controller at PCI slot 0000:00:1f.1
ICH2M: chipset revision 3
ICH2M: not 100% native mode: will probe irqs later
ide0: BM-DMA at 0x1800-0x1807, BIOS settings: hdaMA, hdbio
ide1: BM-DMA at 0x1808-0x180f, BIOS settings: hdcMA, hddio
Probing IDE interface ide0...
hda: HITACHI_DK23BA-10, ATA DISK drive
elevator: using anticipatory as default io scheduler
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
hda: max request size: 128KiB
hda: 19640880 sectors (10056 MB) w/512KiB Cache, CHS=19485/16/63, UDMA(66)
hda: cache flushes not supported
/dev/ide/host0/bus0/target0/lun0: p1 p2 p4 < p5 p6 >
Probing IDE interface ide1...
hdc: TOSHIBA DVD-ROM SD-C2502, ATAPI CD/DVD-ROM drive
ide1 at 0x170-0x177,0x376 on irq 15
Probing IDE interface ide2...
Probing IDE interface ide3...
Probing IDE interface ide4...
Probing IDE interface ide5...
EXT3-fs: mounted filesystem with ordered data mode.
kjournald starting. Commit interval 5 seconds
Adding 240904k swap on /dev/hda6. Priority:-1 extents:1
EXT3 FS on hda2, internal journal
SCSI subsystem initialized
input: PS/2 Generic Mouse on isa0060/serio1
mice: PS/2 mouse device common for all mice
ts: Compaq touchscreen protocol output
hdc: ATAPI 24X DVD-ROM drive, 128kB Cache
Uniform CD-ROM driver Revision: 3.20
ieee1394: Initialized config rom entry `ip1394'
sbp2: $Rev: 1219 $ Ben Collins <bcollins@debian.org>
parport: PnPBIOS parport detected.
parport0: PC-style at 0x378 (0x77, irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
lp0: using parport0 (interrupt-driven).
Capability LSM initialized
device-mapper: 4.3.0-ioctl (2004-09-30) initialised: [email]dm-devel@redhat.com[/email]
md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
cdrom: open failed.
cdrom: open failed.
Real Time Clock Driver v1.12
input: PC Speaker
Linux agpgart interface v0.100 (c) Dave Jones
agpgart: Detected an Intel i815 Chipset.
agpgart: Maximum main memory to use for agp memory: 438M
agpgart: AGP aperture is 64M @ 0xf8000000
cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x1001
pciehp: acpi_pciehprm:get_device PCI ROOT HID fail=0x1001
hw_random hardware driver 1.0.0 loaded
usbcore: registered new driver usbfs
usbcore: registered new driver hub
USB Universal Host Controller Interface driver v2.2
PCI: Found IRQ 9 for device 0000:00:1f.2
uhci_hcd 0000:00:1f.2: Intel Corp. 82801BA/BAM USB (Hub #1)
PCI: Setting latency timer of device 0000:00:1f.2 to 64
uhci_hcd 0000:00:1f.2: irq 9, io base 0x1820
uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 2 ports detected
PCI: Found IRQ 11 for device 0000:00:1f.4
uhci_hcd 0000:00:1f.4: Intel Corp. 82801BA/BAM USB (Hub #2)
PCI: Setting latency timer of device 0000:00:1f.4 to 64
uhci_hcd 0000:00:1f.4: irq 11, io base 0x1880
uhci_hcd 0000:00:1f.4: new USB bus registered, assigned bus number 2
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 2 ports detected
usb 1-2: new low speed USB device using uhci_hcd and address 2
usbcore: registered new driver hiddev
input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1f.2-2
usbcore: registered new driver usbhid
drivers/usb/input/hid-core.c: v2.0:USB HID core driver
PCI: Found IRQ 5 for device 0000:00:1f.5
PCI: Sharing IRQ 5 with 0000:00:1f.3
PCI: Setting latency timer of device 0000:00:1f.5 to 64
intel8x0_measure_ac97_clock: measured 49090 usecs
intel8x0: clocking to 48000
ohci1394: $Rev: 1223 $ Ben Collins <bcollins@debian.org>
PCI: Enabling device 0000:01:00.0 (0110 -> 0112)
PCI: No IRQ known for interrupt pin A of device 0000:01:00.0. Please try using pci=biosirq.
ohci1394: Failed to allocate shared interrupt 0
ohci1394: probe of 0000:01:00.0 failed with error -12
Linux Kernel Card Services
options: [pci] [cardbus] [pm]
PCI: No IRQ known for interrupt pin A of device 0000:01:02.0. Please try using pci=biosirq.
Yenta: CardBus bridge found at 0000:01:02.0 [104d:80df]
Yenta: ISA IRQ mask 0x0018, PCI irq 0
Socket status: 30000006
PCI: No IRQ known for interrupt pin B of device 0000:01:02.1. Please try using pci=biosirq.
Yenta: CardBus bridge found at 0000:01:02.1 [104d:80df]
Yenta: ISA IRQ mask 0x0018, PCI irq 0
Socket status: 30000006
e100: Intel(R) PRO/100 Network Driver, 3.2.3-k2-NAPI
e100: Copyright(c) 1999-2004 Intel Corporation
PCI: Enabling device 0000:01:08.0 (0110 -> 0113)
PCI: Found IRQ 9 for device 0000:01:08.0
e100: eth0: e100_probe: addr 0xf4105000, irq 9, MAC addr 08:00:46:15:0A:8D
e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
NET: Registered protocol family 17
NET: Registered protocol family 10
Disabled Privacy Extensions on device c02f0500(lo)
IPv6 over IPv4 tunneling driver
apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
eth0: no IPv6 routers present
cs: IO port probe 0x0100-0x04ff: clean.
cs: IO port probe 0x0800-0x08ff: clean.
cs: IO port probe 0x0c00-0x0cff: clean.
cs: IO port probe 0x0a00-0x0aff: clean.
cpufreq: change failed with new_state 2 and result 0
cpufreq: change failed with new_state 2 and result 0
cpufreq: change failed with new_state 2 and result 0
cpufreq: change failed with new_state 2 and result 0
e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
eth0: no IPv6 routers present
e100: eth0: e100_watchdog: link down
e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
e100: eth0: e100_watchdog: link down
e100: eth0: e100_watchdog: link up, 10Mbps, half-duplex
e100: eth0: e100_watchdog: link up, 10Mbps, half-duplex
eth0: no IPv6 routers present
e100: eth0: e100_watchdog: link up, 10Mbps, half-duplex
eth0: no IPv6 routers present
e100: eth0: e100_watchdog: link down
drivers/usb/input/hid-core.c: input irq status -84 received
drivers/usb/input/hid-core.c: input irq status -84 received
drivers/usb/input/hid-core.c: input irq status -84 received
usb 1-2: USB disconnect, address 2
usb 1-2: new full speed USB device using uhci_hcd and address 3
eth0: no IPv6 routers present
e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
usb 1-2: USB disconnect, address 3
usb 1-1: new full speed USB device using uhci_hcd and address 4


The last line

"usb 1-1: new full speed USB device using uhci_hcd and address 4"

says that it detects the device but it doesn't put it in any of sda# devices.

Any help would be gladly appreciated.

---

### Post by alastair on 2005-04-05
Not sure.

Try booting the system without the USB disk.
Login.

Open a shell and :

sudo tail -f /var/log/syslog

Then, plug in the USB disk and see what is printed.

Anything?

---

### Post by chien on 2005-04-06
> 	Not sure.  Try booting the system without the USB disk. Login.  Open a shell and : 

 sudo tail -f /var/log/syslog  

Then, plug in the USB disk and see what is printed.  Anything? 


This is what the line that it shows in /var/log/syslog once I plug the USB disk


Apr  6 01:29:01 localhost kernel: usb 1-1: new full speed USB device using uhci_hcd and address 3


The same line that dmesg gives me, it detects the USB device, but it doesn't seem to detect the Hard Disk.


Thanks for the reply,

Anyone else has any suggestion?

---

### Post by Nano on 2005-04-06
fdisk -l won't show main drive unless you "sudo" it:
```

sudo fdisk -l

```

---

### Post by chien on 2005-04-06
> 	fdisk -l won't show main drive unless you "sudo" it: 

ok I did "sudo fdisk -l" and it's giving me the same.


chien@chien:~/opera $ sudo fdisk -l

Disk /dev/hda: 10.0 GB, 10056130560 bytes
255 heads, 63 sectors/track, 1222 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         489     3927861    b  W95 FAT32
/dev/hda2             490        1062     4602622+  83  Linux
/dev/hda4            1063        1222     1285200    f  W95 Ext'd (LBA)
/dev/hda5            1093        1222     1044193+   b  W95 FAT32
/dev/hda6            1063        1092      240912   82  Linux swap / Solaris

Partition table entries are not in disk order

I REALLY NEED HELP HERE, this is driving me nuts  :confused:

---

### Post by alastair on 2005-04-06
This message looks suspicious - but it might be a false trail :

input irq status -84 received

Has this disk ever worked on Ubuntu? 
What about other Linux dists?
Does it work on Windows?

What about trying a different USB port? or a different cable?

---

### Post by chien on 2005-04-06
<quote>This message looks suspicious - but it might be a false trail :

input irq status -84 received

Has this disk ever worked on Ubuntu?
What about other Linux dists?
Does it work on Windows?

What about trying a different USB port? or a different cable?</quote>

I don't think the problem is with the port or the cable cause it's working perfectly on windows XP. I've tried mounting it on Fedora, Suse, and then I heard that Ubuntu has a really good hardware support, and I decided to give it a try and here I'm with Ubuntu and a still not working external HD. I keep switching back to windows because that's the only way of accesing it, all my videos and mp3 are in that drive.

I've read tons of forum with the hope of fixing this problem, no luck so far.

---

