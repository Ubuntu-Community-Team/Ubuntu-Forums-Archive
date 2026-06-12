---
title: "Realtek ALC861 - no sound"
date: 2006-09-14
forum: Hardware &amp; Laptops
---

### Post by jiaxiang on 2006-09-14
I've tried everything. I can't get sound on my laptop. I'm a musician and graphic artist, so you know this is an emergency. I did reference the previous forum posts thoroughly. This post is my final hope.

I followed both sets of directions here:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

I've even referenced this post:

[http://ubuntuforums.org/showpost.php?p=1410649&postcount=41](http://ubuntuforums.org/showpost.php?p=1410649&postcount=41)

I downloaded drivers for older kernels from the Realtek site. I've compiled, purged, edited, and otherwise mangeled the alsa-base and relate files.

The result?

NO SOUND!

Posting here was my last option because I just cannot figure out what is wrong.

[System Specifications]

Toshiba Satellite 
Realtek ALC861
Intel Celeron M
768 MB RAM


----------------------

aplay -l

card o: SB [HDA ATI SB], device 0: ALC861 Analog [ALC861} Subdevices: 0/1

Subdevice #0: subdevice #0

----------------------
dmesg

[17179597.988000] hda_codec: invalid dep_range_val 0:7fff
[17179598.036000] ACPI: PCI Interrupt 0000:09:01.0[A] -> GSI 20 (level, low) -> IRQ 177
[17179598.036000] Yenta: CardBus bridge found at 0000:09:01.0 [1179:ff31]
[17179598.036000] Yenta: Using CSCINT to route CSC interrupts to PCI
[17179598.036000] Yenta: Routing CardBus interrupts to PCI
[17179598.036000] Yenta TI: socket 0000:09:01.0, mfunc 0x00001002, devctl 0x44
[17179598.268000] Yenta: ISA IRQ mask 0x0cf8, PCI irq 177
[17179598.268000] Socket status: 30000006
[17179598.268000] pcmcia: parent PCI bridge I/O window: 0xa000 - 0xafff
[17179598.268000] cs: IO port probe 0xa000-0xafff: clean.
[17179598.268000] pcmcia: parent PCI bridge Memory window: 0xd0200000 - 0xd02fffff
[17179598.268000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x31ffffff
[17179598.272000] ACPI: PCI Interrupt 0000:09:02.0[A] -> GSI 21 (level, low) -> IRQ 209
[17179598.272000] eth0: RealTek RTL8139 at 0xeea14000, 00:16:36:59:80:1d, IRQ 209
[17179598.272000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[17179598.280000] ACPI: PCI Interrupt 0000:09:04.0[A] -> GSI 22 (level, low) -> IRQ 185
[17179598.292000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[17179598.864000] Build date: Jul 10 2006
[17179598.864000] Debugging version (IEEE80211)
[17179598.864000] ath0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[17179598.864000] ath0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[17179598.864000] ath0: H/W encryption support: WEP AES AES_CCM TKIP
[17179598.864000] ath0: mac 7.8 phy 4.5 radio 5.6
[17179598.864000] ath0: Use hw queue 1 for WME_AC_BE traffic
[17179598.864000] ath0: Use hw queue 0 for WME_AC_BK traffic
[17179598.864000] ath0: Use hw queue 2 for WME_AC_VI traffic
[17179598.864000] ath0: Use hw queue 3 for WME_AC_VO traffic
[17179598.864000] ath0: Use hw queue 8 for CAB traffic
[17179598.868000] ath0: Use hw queue 9 for beacons
[17179598.868000] Debugging version (ATH)
[17179598.868000] ath0: Atheros 5212: mem=0xd0200000, irq=185
[17179599.076000] eth0: link down
[17179599.256000] cs: IO port probe 0x100-0x3af: clean.
[17179599.260000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[17179599.260000] cs: IO port probe 0x820-0x8ff: excluding 0x878-0x87f
[17179599.260000] cs: IO port probe 0xc00-0xcf7: excluding 0xc00-0xc07 0xc10-0xc17 0xc50-0xc57 0xc68-0xc6f 0xcd0-0xcdf
[17179599.260000] cs: IO port probe 0xa00-0xaff: clean.
[17179599.632000] lp: driver loaded but no devices found
[17179599.684000] Adding 1590392k swap on /dev/sda5.  Priority:-1 extents:1 across:1590392k
[17179599.852000] EXT3 FS on sda2, internal journal
[17179600.000000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179600.000000] md: bitmap version 4.39
[17179600.160000] NET: Registered protocol family 17
[17179600.484000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[17179606.776000] ACPI: AC Adapter [ACAD] (on-line)
[17179606.848000] ACPI: Battery Slot [BAT1] (battery present)
[17179606.932000] ACPI: Power Button (FF) [PWRF]
[17179606.932000] ACPI: Lid Switch [LID]
[17179606.932000] ACPI: Power Button (CM) [PWRB]
[17179607.020000] ibm_acpi: ec object not found
[17179607.056000] pcc_acpi: loading...
[17179611.556000] [drm] Initialized drm 1.0.1 20051102
[17179612.580000] ppdev: user-space parallel port driver
[17179613.300000] apm: BIOS not found.
[17179617.724000] Bluetooth: Core ver 2.8
[17179617.724000] NET: Registered protocol family 31
[17179617.724000] Bluetooth: HCI device and connection manager initialized
[17179617.724000] Bluetooth: HCI socket layer initialized
[17179617.796000] Bluetooth: L2CAP ver 2.8
[17179617.796000] Bluetooth: L2CAP socket layer initialized
[17179617.848000] Bluetooth: RFCOMM socket layer initialized
[17179617.848000] Bluetooth: RFCOMM TTY layer initialized
[17179617.848000] Bluetooth: RFCOMM ver 1.7
[17179620.260000] hda-intel: Invalid position buffer, using LPIB read method instead.
[17179633.936000] NET: Registered protocol family 10
[17179633.936000] lo: Disabled Privacy Extensions
[17179633.936000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17179633.936000] IPv6 over IPv4 tunneling driver
[17179644.652000] ath0: no IPv6 routers present
[17180337.580000] usb 3-3: new high speed USB device using ehci_hcd and address 2
[17180337.848000] Initializing USB Mass Storage driver...
[17180337.848000] scsi2 : SCSI emulation for USB Mass Storage devices
[17180337.848000] usb-storage: device found at 2
[17180337.848000] usb-storage: waiting for device to settle before scanning
[17180337.848000] usbcore: registered new driver usb-storage
[17180337.848000] USB Mass Storage support registered.
[17180342.848000]   Vendor: USB 2.0   Model: Flash Disk        Rev: 0.00
[17180342.848000]   Type:   Direct-Access                      ANSI SCSI revision: 02
[17180342.852000] SCSI device sdb: 256000 512-byte hdwr sectors (131 MB)
[17180342.852000] sdb: Write Protect is off
[17180342.852000] sdb: Mode Sense: 00 00 00 00
[17180342.852000] sdb: assuming drive cache: write through
[17180342.852000] SCSI device sdb: 256000 512-byte hdwr sectors (131 MB)
[17180342.852000] sdb: Write Protect is off
[17180342.852000] sdb: Mode Sense: 00 00 00 00
[17180342.852000] sdb: assuming drive cache: write through
[17180342.852000]  sdb:
[17180343.096000] sd 2:0:0:0: Attached scsi removable disk sdb
[17180343.096000] sd 2:0:0:0: Attached scsi generic sg1 type 0
[17180343.096000] usb-storage: device scan complete

----------------------
lspci -v

0000:00:00.0 Host bridge: ATI Technologies Inc: Unknown device 5a31 (rev 01)
        Subsystem: Toshiba America Info Systems: Unknown device ff31
        Flags: bus master, 66MHz, medium devsel, latency 64

0000:00:01.0 PCI bridge: ATI Technologies Inc: Unknown device 5a3f (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        I/O behind bridge: 00009000-00009fff
        Memory behind bridge: d0100000-d01fffff
        Prefetchable memory behind bridge: d4000000-d7ffffff
        Capabilities: <available only to root>

0000:00:12.0 IDE interface: ATI Technologies Inc ATI 4379 Serial ATA Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: Toshiba America Info Systems: Unknown device ff31
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 185
        I/O ports at 8440 [size=8]
        I/O ports at 8430 [size=4]
        I/O ports at 8420 [size=8]
        I/O ports at 8410 [size=4]
        I/O ports at 8400 [size=16]
        Memory at d0004000 (32-bit, non-prefetchable) [size=512]
        Expansion ROM at 32000000 [disabled] [size=512K]
        Capabilities: <available only to root>

0000:00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10 [OHCI])
        Subsystem: Toshiba America Info Systems: Unknown device ff31
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 201
        Memory at d0005000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10 [OHCI])
        Subsystem: Toshiba America Info Systems: Unknown device ff31
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 201
        Memory at d0006000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80) (prog-if 20 [EHCI])
        Subsystem: Toshiba America Info Systems: Unknown device ff31
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 201
        Memory at d0007000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 81)
        Subsystem: Toshiba America Info Systems: Unknown device ff31
        Flags: 66MHz, medium devsel
        I/O ports at 8040 [size=16]
        Memory at d0004400 (32-bit, non-prefetchable) [size=1K]

0000:00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80) (prog-if 88 [Master SecP])
        Subsystem: Toshiba America Info Systems: Unknown device ff31
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 193
        I/O ports at <ignored>
        I/O ports at <ignored>
        I/O ports at <ignored>
        I/O ports at <ignored>
        I/O ports at 8460 [size=16]
        Capabilities: <available only to root>

0000:00:14.2 0403: ATI Technologies Inc: Unknown device 437b (rev 01)
        Subsystem: Toshiba America Info Systems: Unknown device ff31
        Flags: bus master, slow devsel, latency 64, IRQ 193
        Memory at d0000000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <available only to root>

0000:00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
        Subsystem: Toshiba America Info Systems: Unknown device ff31
        Flags: bus master, 66MHz, medium devsel, latency 0

0000:00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80) (prog-if 01 [Subtractive decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=09, subordinate=0e, sec-latency=64
        I/O behind bridge: 0000a000-0000afff
        Memory behind bridge: d0200000-d02fffff
        Prefetchable memory behind bridge: 30000000-31ffffff

0000:01:05.0 VGA compatible controller: ATI Technologies Inc: Unknown device 5a62 (prog-if 00 [VGA])
        Subsystem: Toshiba America Info Systems: Unknown device ff31
        Flags: bus master, 66MHz, medium devsel, latency 66, IRQ 11
        Memory at d4000000 (32-bit, prefetchable) [size=64M]
        I/O ports at 9000 [size=256]
        Memory at d0100000 (32-bit, non-prefetchable) [size=64K]
        Expansion ROM at d0120000 [disabled] [size=128K]
        Capabilities: <available only to root>

0000:09:01.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
        Subsystem: Toshiba America Info Systems: Unknown device ff31
        Flags: bus master, medium devsel, latency 168, IRQ 177
        Memory at d0211000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=09, secondary=0a, subordinate=0d, sec-latency=176
        Memory window 0: 30000000-31fff000 (prefetchable)
        Memory window 1: 34000000-35fff000
        I/O window 0: 0000a400-0000a4ff
        I/O window 1: 0000a800-0000a8ff
        16-bit legacy interface ports at 0001

0000:09:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Toshiba America Info Systems: Unknown device ff31
        Flags: bus master, medium devsel, latency 64, IRQ 209
        I/O ports at a000 [size=256]
        Memory at d0210000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

0000:09:04.0 Ethernet controller: Atheros Communications, Inc.: Unknown device 001a (rev 01)
        Subsystem: Askey Computer Corp.: Unknown device 7094
        Flags: bus master, medium devsel, latency 168, IRQ 185
        Memory at d0200000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <available only to root>

---

### Post by hmjgriffon on 2007-05-17
add the following line to your       /etc/modprobe.d/alsabase      file:

options snd-hda-intel position_fix=1 model=3stack

This made the sound work, but when I put headphones in my pc speakers still play.

---

### Post by zanjabeel5 on 2007-05-17
I have laptop with the same sound chip
now I have sound just by following the instructions in the sound section of the following:

[https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo3000C200_89224MG](https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo3000C200_89224MG)

I did that after undoing all the changes I made to try to get sound work.

---

