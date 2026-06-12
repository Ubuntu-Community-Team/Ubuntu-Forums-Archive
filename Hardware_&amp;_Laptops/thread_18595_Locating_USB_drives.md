---
title: "Locating USB drives"
date: 2005-03-07
forum: Hardware &amp; Laptops
---

### Post by javamdk on 2005-03-07
I plugged in my LinkSys USB Adapter and was wondering how I can find out which USB device it's plugged into (currently it's not working...)  I searched in '/dev/' and seen nothing with the name USB.

Also, I have a light on my Wi-Fi adapter which doesn't light up when I plug it in... is it possible the usb modules haven't been installed?

Thanks

---

### Post by alastair on 2005-03-07
Before you plug it in, have a shell open and "tail" the system log - you can see system messages as they occur i.e.

sudo tail -f /var/log/syslog

Then plug in the USB adapter. Any messages?

---

### Post by javamdk on 2005-03-07
yeah, 

it says:

Mar  7 17:03:31 localhost kernel: usb 4-2: new high speed USB device using address 3

What does that mean?

Thanks again

---

### Post by alastair on 2005-03-07
It means it has not found the ethernet device ... although it recognises something getting plugged in.

Nothing else afterwards?

If you boot with the device plugged in, anything in the logs?

Perhaps post 

- output of "dmesg"
- cat /proc/bus/usb/devices (with it plugged in)
- lspci -v

---

### Post by javamdk on 2005-03-07
There wasn't anything after that one line I submitted before with trail -f. 
[b]
dmesg shows:

[/b]joer@venus:~ $ dmesg
Total memory = 768MB; using 2048kB for hash table (at c0400000)
Linux version 2.6.8.1-3-powerpc (buildd@royal) (gcc version 3.3.4 (Debian 1:3.3.4-9ubuntu5)) #1 Tue Oct 12 13:15:29 BST 2004
Found UniNorth memory controller & host bridge, revision: 210
Mapped at 0xfdf00000
Found a Intrepid mac-io controller, rev: 0, mapped at 0xfde80000
Processor NAP mode on idle enabled.
PowerMac motherboard: iBook G4
Found UniNorth PCI host bridge at 0xf0000000. Firmware bus number: 0->0
Found UniNorth PCI host bridge at 0xf2000000. Firmware bus number: 0->0
Found UniNorth PCI host bridge at 0xf4000000. Firmware bus number: 0->0
via-pmu: Server Mode is disabled
PMU driver 2 initialized for Core99, firmware: 0c
nvram: Checking bank 0...
nvram: gen0=162, gen1=163
nvram: Active bank is: 1
nvram: OF partition at 0x410
nvram: XP partition at 0x1020
nvram: NR partition at 0x1120
On node 0 totalpages: 196608
  DMA zone: 196608 pages, LIFO batch:16
  Normal zone: 0 pages, LIFO batch:1
  HighMem zone: 0 pages, LIFO batch:1
Built 1 zonelists
Kernel command line: root=/dev/hda3 ro quiet splash
PowerMac using OpenPIC irq controller at 0x80040000
OpenPIC Version 1.2 (4 CPUs and 64 IRQ sources) at fc62f000
OpenPIC timer frequency is 4.166666 MHz
PID hash table entries: 4096 (order 12: 32768 bytes)
GMT Delta read from XPRAM: 0 minutes, DST: off
time_init: decrementer frequency = 18.432000 MHz
Console: colour dummy device 80x25
serial8250_console_init: nothing to do on PowerMac
Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Memory: 769408k available (1720k kernel code, 1124k data, 164k init, 0k highmem)AGP special page: 0xeffff000
Calibrating delay loop... 663.55 BogoMIPS
Mount-cache hash table entries: 512 (order: 0, 4096 bytes)
checking if image is initramfs...it isn't (ungzip failed); looks like an initrd
Freeing initrd memory: 4228k freed
NET: Registered protocol family 16
PCI: Probing PCI hardware
PCI: Cannot allocate resource region 0 of device 0001:01:18.0
PCI: Cannot allocate resource region 0 of device 0001:01:19.0
Registering openpic with sysfs...
PCI: Enabling device 0000:00:10.0 (0006 -> 0007)
radeonfb: Invalid ROM signature 0 should be 0xaa55
radeonfb: Retreived PLL infos from Open Firmware
radeonfb: Reference=27.00 MHz (RefDiv=12) Memory=190.00 Mhz, System=183.00 MHz
radeonfb: Monitor 1 type LCD found
radeonfb: EDID probed
radeonfb: Monitor 2 type no found
radeonfb: Power Management enabled for Mobility chipsets
Registered "mnca" backlight controller, level: 15/15
radeonfb: ATI Radeon \c  DDR SGRAM 32 MB
Thermal assist unit not available
Registering PowerMac CPU frequency driver
Low: 666 Mhz, High: 1333 Mhz, Boot: 666 Mhz
audit: initializing netlink socket (disabled)
audit(1110235097.341:0): initialized
devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
devfs: boot_options: 0x0
Initializing Cryptographic API
Console: switching to colour frame buffer device 128x48
Generic RTC Driver v1.07
Macintosh non-volatile memory driver v1.1
serial8250_init: nothing to do on PowerMac
pmac_zilog: 0.6 (Benjamin Herrenschmidt <benh@kernel.crashing.org>)
ttyS0 at MMIO 0x80013020 (irq = 22) is a Z85c30 ESCC - Serial port
ttyS1 at MMIO 0x80013000 (irq = 23) is a Z85c30 ESCC - Serial port
RAMDISK driver initialized: 16 RAM disks of 8192K size 1024 blocksize
divert: not allocating divert_blk for non-ethernet device lo
MacIO PCI driver attached to Intrepid chipset
Can't request resource 0 for MacIO device 0.80000000:mac-io
input: Macintosh mouse button emulation
Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
PCI: Enabling device 0002:02:0d.0 (0000 -> 0002)
adb: starting probe task...
adb devices: [2]: 2 c3 [3]: 3 1 [7]: 7 1f
ADB keyboard at 2, handler 1
Detected ADB keyboard, type ANSI.
input: ADB keyboard on adb2:2.c3/input
input: ADB Powerbook buttons on adb7:7.1f/input
ADB mouse at 3, handler set to 4 (trackpad)
input: ADB mouse on adb3:3.01/input
adb: finished probe task...
ide0: Found Apple UniNorth ATA-6 controller, bus ID 3, irq 39
Probing IDE interface ide0...
hda: FUJITSU MHT2060AT, ATA DISK drive
hda: Enabling Ultra DMA 5
Using anticipatory io scheduler
ide0 at 0xf20f7000-0xf20f7007,0xf20f7160 on irq 39
ide1: Found Apple KeyLargo ATA-3 controller, bus ID 0, irq 24
Probing IDE interface ide1...
hdc: MATSHITACD-RW CW-8123, ATAPI CD/DVD-ROM drive
ide1 at 0xf20fa000-0xf20fa007,0xf20fa160 on irq 24
mice: PS/2 mouse device common for all mice
Found KeyWest i2c on "uni-n", 2 channels, stepping: 4 bits
Found KeyWest i2c on "mac-io", 1 channel, stepping: 4 bits
NET: Registered protocol family 2
IP: routing cache hash table of 8192 buckets, 64Kbytes
TCP: Hash tables configured (established 262144 bind 65536)
RAMDISK: cramfs filesystem found at block 0
RAMDISK: Loading 4228 blocks [1 disk] into ram disk... done.
VFS: Mounted root (cramfs filesystem) readonly.
Freeing unused kernel memory: 164k init 4k chrp 32k prep
NET: Registered protocol family 1
hda: max request size: 1024KiB
hda: 117210240 sectors (60011 MB) w/8192KiB Cache, CHS=16383/255/63, UDMA(100)
 /dev/ide/host0/bus0/target0/lun0: [mac] p1 p2 p3 p4
kjournald starting.  Commit interval 5 seconds
EXT3-fs: mounted filesystem with ordered data mode.
Adding 500584k swap on /dev/hda4.  Priority:-1 extents:1
EXT3 FS on hda3, internal journal
SCSI subsystem initialized
adt746x: Thermostat bus: 1, address: 0x2e, limit_adjust: 0, fan_speed: -1
adt746x: ADT7467 initializing
adt746x: Lowering max temperatures from 69, 92, 101 to 70, 50, 70 (°C)
adt746x: Setting speed to: 0 for CPU fan.
apm_emu: APM Emulation 0.5 initialized.
hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache
Uniform CD-ROM driver Revision: 3.20
ieee1394: Initialized config rom entry `ip1394'
sbp2: $Rev: 1219 $ Ben Collins <bcollins@debian.org>
device-mapper: 4.1.0-ioctl (2003-12-10) initialised: [email]dm@uk.sistina.com[/email]
md: md driver 0.90.0 MAX_MD_DEVS=256, MD_SB_DISKS=27
ts: Compaq touchscreen protocol output
Linux agpgart interface v0.100 (c) Dave Jones
agpgart: Detected Apple UniNorth 2 chipset
agpgart: Maximum main memory to use for agp memory: 691M
agpgart: configuring for size idx: 4
agpgart: AGP aperture is 16M @ 0x0
usbcore: registered new driver usbfs
usbcore: registered new driver hub
ohci_hcd: 2004 Feb 02 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
ohci_hcd: block sizes: ed 64 td 64
PCI: Enabling device 0001:01:18.0 (0000 -> 0002)
ohci_hcd 0001:01:18.0: Found HC with no IRQ.  Check BIOS/PCI 0001:01:18.0 setup!PCI: Enabling device 0001:01:19.0 (0000 -> 0002)
ohci_hcd 0001:01:19.0: Found HC with no IRQ.  Check BIOS/PCI 0001:01:19.0 setup!PCI: Enabling device 0001:01:1a.0 (0000 -> 0002)
ohci_hcd 0001:01:1a.0: Apple Computer Inc. KeyLargo/Intrepid USB (#3)
ohci_hcd 0001:01:1a.0: irq 29, pci mem f21fb000
ohci_hcd 0001:01:1a.0: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 2 ports detected
PCI: Enabling device 0001:01:1b.0 (0000 -> 0002)
ohci_hcd 0001:01:1b.0: NEC Corporation USB
ohci_hcd 0001:01:1b.0: irq 63, pci mem f21fd000
ohci_hcd 0001:01:1b.0: new USB bus registered, assigned bus number 2
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 3 ports detected
PCI: Enabling device 0001:01:1b.1 (0000 -> 0002)
ohci_hcd 0001:01:1b.1: NEC Corporation USB (#2)
ohci_hcd 0001:01:1b.1: irq 63, pci mem f2279000
ohci_hcd 0001:01:1b.1: new USB bus registered, assigned bus number 3
hub 3-0:1.0: USB hub found
hub 3-0:1.0: 2 ports detected
usb 1-1: new full speed USB device using address 2
ohci_hcd 0001:01:1b.1: wakeup
adt746x: Setting speed to: 128 for CPU fan.
usb 3-1: new full speed USB device using address 2
usbcore: registered new driver hiddev
input: USB HID v1.11 Keyboard [05ac:1000] on usb-0001:01:1a.0-1
drivers/usb/input/hid-core.c: ctrl urb status -32 received
input: USB HID v1.11 Mouse [05ac:1000] on usb-0001:01:1a.0-1
usbcore: registered new driver usbhid
drivers/usb/input/hid-core.c: v2.0:USB HID core driver
PCI: Enabling device 0001:01:1b.2 (0004 -> 0006)
ehci_hcd 0001:01:1b.2: NEC Corporation USB 2.0
ehci_hcd 0001:01:1b.2: irq 63, pci mem f2291000
ehci_hcd 0001:01:1b.2: new USB bus registered, assigned bus number 4
ehci_hcd 0001:01:1b.2: USB 2.0 enabled, EHCI 1.00, driver 2004-May-10
hub 4-0:1.0: USB hub found
hub 4-0:1.0: 5 ports detected
usb 3-1: USB disconnect, address 2
usb 4-2: new high speed USB device using address 2
ohci1394: $Rev: 1223 $ Ben Collins <bcollins@debian.org>
PCI: Enabling device 0002:02:0e.0 (0000 -> 0002)
ohci1394: fw-host0: Unexpected PCI resource length of 1000!
ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[40]  MMIO=[f5000000-f50007ff]  Max Packet=[2048]
sungem.c:v0.98 8/24/03 David S. Miller (davem@redhat.com)
divert: allocating divert_blk for eth0
eth0: Sun GEM (PCI) 10/100/1000BaseT Ethernet 00:0d:93:4b:b6:46
PHY ID: 4061e4, addr: 0
eth0: Found BCM5221 PHY
ieee1394: Host added: ID:BUS[0-00:1023]  GUID[000d93fffe4bb646]
eth0: Link is up at 100 Mbps, full-duplex.
eth0: Pause is disabled
NET: Registered protocol family 17
NET: Registered protocol family 10
Disabled Privacy Extensions on device c0236384(lo)
IPv6 over IPv4 tunneling driver
divert: not allocating divert_blk for non-ethernet device sit0
hda: Set PIO timing for mode 0, reg: 0x08618a92
eth0: no IPv6 routers present
[drm] Initialized radeon 1.11.0 20020828 on minor 0: ATI Technologies Inc RV250 5c63 [Radeon Mobility 9200 M9+]
agpgart: Putting AGP V2 device at 0000:00:0b.0 into 1x mode
agpgart: Putting AGP V2 device at 0000:00:10.0 into 1x mode
[drm] Loading R200 Microcode
drivers/usb/input/hid-input.c: event field not found
adt746x: Stopping CPU fan.
adt746x: Setting speed to: 0 for CPU fan.
usb 4-2: USB disconnect, address 2
usb 4-2: new high speed USB device using address 3
usb 4-2: USB disconnect, address 3
usb 4-2: new high speed USB device using address 4
usb 4-2: USB disconnect, address 4
usb 4-2: new high speed USB device using address 5
**Below is the cat(ing) devices:**

joer@venus:~ $ cat /proc/bus/usb/devices

T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 5
B:  Alloc=  0/800 us ( 0%), #Int=  0, #Iso=  0
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS= 8 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.8.1-3-powerpc ehci_hcd
S:  Product=NEC Corporation USB 2.0
S:  SerialNumber=0001:01:1b.2
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=256ms

T:  Bus=04 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  5 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ff(vend.) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=5041 ProdID=2235 Rev= 2.02
C:* #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs=11 Cls=ff(vend.) Sub=00 Prot=00 Driver=(none)
E:  Ad=01(O) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=81(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=02(O) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=82(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=83(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=84(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=8d(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=0d(O) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=8e(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=0e(O) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=8f(I) Atr=03(Int.) MxPS=   4 Ivl=125us

T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
B:  Alloc=  0/900 us ( 0%), #Int=  0, #Iso=  0
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.8.1-3-powerpc ohci_hcd
S:  Product=NEC Corporation USB (#2)
S:  SerialNumber=0001:01:1b.1
C:* #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=255ms

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 3
B:  Alloc=  0/900 us ( 0%), #Int=  0, #Iso=  0
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.8.1-3-powerpc ohci_hcd
S:  Product=NEC Corporation USB
S:  SerialNumber=0001:01:1b.0
C:* #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=255ms

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
B:  Alloc= 44/900 us ( 5%), #Int=  2, #Iso=  0
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.8.1-3-powerpc ohci_hcd
S:  Product=Apple Computer Inc. KeyLargo/Intrepid USB (#3)
S:  SerialNumber=0001:01:1a.0
C:* #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=255ms

T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=05ac ProdID=1000 Rev=15.86
C:* #Ifs= 2 Cfg#= 1 Atr=e0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=01 Driver=usbhid
E:  Ad=81(I) Atr=03(Int.) MxPS=  16 Ivl=1ms
I:  If#= 1 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid
E:  Ad=82(I) Atr=03(Int.) MxPS=  16 Ivl=1ms
[b]
lspci -v shows (i just copied and pasted the USB devices)[/b]

0001:01:18.0 USB Controller: Apple Computer Inc. KeyLargo/Intrepid USB (prog-if 10 [OHCI])
        Flags: medium devsel
        Memory at f3000000 (32-bit, non-prefetchable)

0001:01:19.0 USB Controller: Apple Computer Inc. KeyLargo/Intrepid USB (prog-if 10 [OHCI])
        Flags: medium devsel
        Memory at f3001000 (32-bit, non-prefetchable)

0001:01:1a.0 USB Controller: Apple Computer Inc. KeyLargo/Intrepid USB (prog-if 10 [OHCI])
        Flags: bus master, medium devsel, latency 16, IRQ 29
        Memory at 80083000 (32-bit, non-prefetchable)

0001:01:1b.0 USB Controller: NEC Corporation USB (rev 43) (prog-if 10 [OHCI])
        Subsystem: NEC Corporation USB
        Flags: bus master, medium devsel, latency 16, IRQ 63
        Memory at 80082000 (32-bit, non-prefetchable)
        Capabilities: <available only to root>

0001:01:1b.1 USB Controller: NEC Corporation USB (rev 43) (prog-if 10 [OHCI])
        Subsystem: NEC Corporation USB
        Flags: bus master, medium devsel, latency 16, IRQ 63
        Memory at 80081000 (32-bit, non-prefetchable)
        Capabilities: <available only to root>

0001:01:1b.2 USB Controller: NEC Corporation USB 2.0 (rev 04) (prog-if 20 [EHCI])
        Subsystem: NEC Corporation USB 2.0
        Flags: bus master, medium devsel, latency 16, IRQ 63
        Memory at 80080000 (32-bit, non-prefetchable)
        Capabilities: <available only to root>

---

