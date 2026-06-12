---
title: "RT2832U driver linux"
date: 2015-02-12
forum: Hardware
---

### Post by ineedwifihelp on 2015-02-12
I am new to linux. So I don't know much. I am trying to set up a dvb-t+sdr dongle for sdr radio. I canot get the thing to work. No program I install can find the device. when I type in lsusb it is listed.
 Bus 001 Device 005: ID 0bda:2838 Realtek Semiconductor Corp. RTL2838 DVB-T

Can anyone help me get this thing to work?
  I have installed gqrx and other programs like that. None of them will find the device.  Would thi s be a missing drive?. If so how do I install it? ...and where can I find it? I know very little about linux. So I have no idea what I'm doing with this? Can anyone help me? I was told I need a RT2832U  Drivver. I do not know where to find it. Or how to install it.

---

### Post by Bucky Ball on 2015-02-12
Can you unplug the device, plug it in and before doing anything else, open a terminal and type:

```
dmesg
```

Please provide the output at then end of that output which will pertain to the DVB device. Your looking for something like this:

```
[ 1290.014662] usb 2-1.1: dvb_usb_v2: 'Realtek RTL2832U reference design' successfully initialized and connected
```

That card used to be a bit of a hassle to setup some time ago, but you don't need to install a driver now. It is already in the kernel. Show us the output and we'll see if it is loading a driver when you insert the dongle.

(I have the same card in my Ezycap DVB card and works fine 'out of the box'.)

PS: Which Ubuntu release are you using? It is a problem in 12.04 LTS from memory, but may not be now. Works faultlessly for me in 14.04 LTS, though. Which software are you trying to use which doesn't find it?

---

### Post by ineedwifihelp on 2015-02-13
```
[    3.020409] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    3.022316] Linux agpgart interface v0.103
[    3.022376] agpgart-intel 0000:00:00.0: Intel 945GM Chipset
[    3.022433] agpgart-intel 0000:00:00.0: detected gtt size: 262144K total, 262144K mappable
[    3.022615] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
[    3.022747] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
[    3.024908] brd: module loaded
[    3.025011] isapnp: Scanning for PnP cards...
[    3.075073] loop: module loaded
[    3.075258] ata_piix 0000:00:1f.1: version 2.13
[    3.163417] scsi0 : ata_piix
[    3.163509] scsi1 : ata_piix
[    3.163561] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
[    3.163564] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
[    3.164047] libphy: Fixed MDIO Bus: probed
[    3.164204] tun: Universal TUN/TAP device driver, 1.6
[    3.164206] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    3.164268] PPP generic driver version 2.4.2
[    3.164325] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    3.164331] ehci-pci: EHCI PCI platform driver
[    3.164542] ehci-pci 0000:00:1d.7: EHCI Host Controller
[    3.164552] ehci-pci 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    3.164571] ehci-pci 0000:00:1d.7: debug port 1
[    3.168481] ehci-pci 0000:00:1d.7: cache line size of 64 is not supported
[    3.168688] ata2: port disabled--ignoring
[    3.168723] ehci-pci 0000:00:1d.7: irq 23, io mem 0xd0544000
[    3.212316] ehci-pci 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    3.212465] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    3.212469] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    3.212472] usb usb1: Product: EHCI Host Controller
[    3.212476] usb usb1: Manufacturer: Linux 3.13.0-37-generic ehci_hcd
[    3.212479] usb usb1: SerialNumber: 0000:00:1d.7
[    3.212621] hub 1-0:1.0: USB hub found
[    3.212633] hub 1-0:1.0: 6 ports detected
[    3.212840] ehci-platform: EHCI generic platform driver
[    3.212856] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.212859] ohci-pci: OHCI PCI platform driver
[    3.212875] ohci-platform: OHCI generic platform driver
[    3.212888] uhci_hcd: USB Universal Host Controller Interface driver
[    3.213077] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.213085] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    3.213118] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001820
[    3.213191] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001
[    3.213195] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    3.213198] usb usb2: Product: UHCI Host Controller
[    3.213201] usb usb2: Manufacturer: Linux 3.13.0-37-generic uhci_hcd
[    3.213204] usb usb2: SerialNumber: 0000:00:1d.0
[    3.213333] hub 2-0:1.0: USB hub found
[    3.213345] hub 2-0:1.0: 2 ports detected
[    3.213621] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.213629] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    3.213674] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001840
[    3.213737] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    3.213741] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    3.213744] usb usb3: Product: UHCI Host Controller
[    3.213747] usb usb3: Manufacturer: Linux 3.13.0-37-generic uhci_hcd
[    3.213750] usb usb3: SerialNumber: 0000:00:1d.1
[    3.213873] hub 3-0:1.0: USB hub found
[    3.213882] hub 3-0:1.0: 2 ports detected
[    3.214156] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.214164] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    3.214211] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
[    3.214273] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    3.214276] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    3.214280] usb usb4: Product: UHCI Host Controller
[    3.214283] usb usb4: Manufacturer: Linux 3.13.0-37-generic uhci_hcd
[    3.214286] usb usb4: SerialNumber: 0000:00:1d.2
[    3.214415] hub 4-0:1.0: USB hub found
[    3.214427] hub 4-0:1.0: 2 ports detected
[    3.214628] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    3.319844] serio: i8042 KBD port at 0x60,0x64 irq 1
[    3.319851] serio: i8042 AUX port at 0x60,0x64 irq 12
[    3.319945] mousedev: PS/2 mouse device common for all mice
[    3.320151] rtc_cmos 00:08: RTC can wake from S4
[    3.320321] rtc_cmos 00:08: rtc core: registered rtc_cmos as rtc0
[    3.320358] rtc_cmos 00:08: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    3.320465] device-mapper: uevent: version 1.0.3
[    3.320554] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: [email]dm-devel@redhat.com[/email]
[    3.320583] platform eisa.0: Probing EISA bus 0
[    3.320592] platform eisa.0: Cannot allocate resource for EISA slot 1
[    3.320597] platform eisa.0: Cannot allocate resource for EISA slot 2
[    3.320600] platform eisa.0: Cannot allocate resource for EISA slot 3
[    3.320604] platform eisa.0: Cannot allocate resource for EISA slot 4
[    3.320628] platform eisa.0: EISA: Detected 0 cards
[    3.320637] cpufreq-nforce2: No nForce2 chipset.
[    3.320641] ledtrig-cpu: registered to indicate activity on CPUs
[    3.320854] TCP: cubic registered
[    3.321000] NET: Registered protocol family 10
[    3.321306] NET: Registered protocol family 17
[    3.321322] Key type dns_resolver registered
[    3.321552] Using IPI No-Shortcut mode
[    3.321654] Loading compiled-in X.509 certificates
[    3.327333] Loaded X.509 cert 'Magrathea: Glacier signing key: 7acf8ed948d77b6a80f24f59d5d8ed0387aab426'
[    3.327362] registered taskstats version 1
[    3.374167] isapnp: No Plug & Play device found
[    3.374231] Key type trusted registered
[    3.376328] ata1.00: ATAPI: Slimtype DVD A  DS8AZP, LH62, max MWDMA2
[    3.378210] Key type encrypted registered
[    3.381200] AppArmor: AppArmor sha1 policy hashing enabled
[    3.381206] IMA: No TPM chip found, activating TPM-bypass!
[    3.381525] regulator-dummy: disabling
[    3.381580]   Magic number: 3:287:860
[    3.381696] rtc_cmos 00:08: setting system clock to 2015-02-13 00:51:47 UTC (1423788707)
[    3.381776] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    3.381778] EDD information not available.
[    3.381835] PM: Hibernation image not present or could not be loaded.
[    3.394636] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    3.409241] ata1.00: configured for MWDMA2
[    3.436193] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    3.436202] ACPI: Battery Slot [BAT1] (battery present)
[    3.437339] scsi 0:0:0:0: CD-ROM            Slimtype DVD A  DS8AZP    LH62 PQ: 0 ANSI: 5
[    3.439772] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    3.439775] cdrom: Uniform CD-ROM driver Revision: 3.20
[    3.439903] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    3.439972] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    3.440522] Freeing unused kernel memory: 872K (c19b9000 - c1a93000)
[    3.440567] Write protecting the kernel text: 6544k
[    3.440643] Write protecting the kernel read-only data: 2768k
[    3.440645] NX-protecting the kernel data: 5744k
[    3.464305] systemd-udevd[97]: starting version 204
[    3.501470] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    3.537336] wmi: Mapper loaded
[    3.563733] [drm] Initialized drm 1.1.0 20060810
[    3.632299] 8139cp: 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    3.632332] 8139cp 0000:08:08.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    3.664281] ssb: Found chip with id 0x4311, rev 0x01 and package 0x00
[    3.664295] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x11, vendor 0x4243)
[    3.664305] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x0A, vendor 0x4243)
[    3.664315] ssb: Core 2 found: USB 1.1 Host (cc 0x817, rev 0x03, vendor 0x4243)
[    3.664324] ssb: Core 3 found: PCI-E (cc 0x820, rev 0x01, vendor 0x4243)
[    3.664830] ahci 0000:00:1f.2: version 3.0
[    3.665069] ahci 0000:00:1f.2: irq 42 for MSI/MSI-X
[    3.665162] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 1.5 Gbps 0x1 impl SATA mode
[    3.665168] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part 
[    3.667159] 8139too: 8139too Fast Ethernet driver 0.9.28
[    3.672399] scsi2 : ahci
[    3.673522] 8139too 0000:08:08.0 eth0: RealTek RTL8139 at 0x00012000, 00:16:d4:c5:06:2d, IRQ 16
[    3.676146] scsi3 : ahci
[    3.681414] scsi4 : ahci
[    3.691670] scsi5 : ahci
[    3.691762] ata3: SATA max UDMA/133 abar m1024@0xd0544400 port 0xd0544500 irq 42
[    3.691766] ata4: DUMMY
[    3.691768] ata5: DUMMY
[    3.691770] ata6: DUMMY
[    3.732192] ssb: Sonics Silicon Backplane found on PCI device 0000:06:00.0
[    3.736181] acpi device:05: registered as cooling_device1
[    3.736288] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input8
[    3.853393] [drm] Memory usable by graphics device = 256M
[    3.853401] checking generic (c0000000 300000) vs hw (c0000000 10000000)
[    3.853404] fb: conflicting fb hw usage inteldrmfb vs VESA VGA - removing generic driver
[    3.853426] Console: switching to colour dummy device 80x25
[    3.855028] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    3.855033] [drm] Driver supports precise vblank timestamp query.
[    3.855134] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    3.937126] [drm] initialized overlay support
[    4.232071] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    4.232953] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    4.232960] ata3.00: ATA-7: Hitachi HTS541680J9SA00, SB2OC7BP, max UDMA/100
[    4.232964] ata3.00: 156301488 sectors, multi 16: LBA48 
[    4.233997] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    4.234004] ata3.00: configured for UDMA/100
[    4.234176] scsi 2:0:0:0: Direct-Access     ATA      Hitachi HTS54168 SB2O PQ: 0 ANSI: 5
[    4.234482] sd 2:0:0:0: [sda] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
[    4.234557] sd 2:0:0:0: [sda] Write Protect is off
[    4.234561] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.234593] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.234892] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    4.387818] fbcon: inteldrmfb (fb0) is primary device
[    4.612213] Console: switching to colour frame buffer device 160x50
[    4.618564] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[    4.618568] i915 0000:00:02.0: registered panic notifier
[    4.619216] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    4.655258]  sda: sda1 sda2 < sda5 >
[    4.655702] sd 2:0:0:0: [sda] Attached SCSI disk
[    4.702428] psmouse serio1: synaptics: Touchpad model: 1, fw: 6.2, id: 0x1a0b1, caps: 0xa04713/0x200000/0x0, board id: 3655, fw id: 152129
[    4.766060] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input7
[    5.798358] random: nonblocking pool is initialized
[    6.533375] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   20.536863] Adding 513020k swap on /dev/sda5.  Priority:-1 extents:1 across:513020k FS
[   20.701367] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   20.937560] systemd-udevd[336]: starting version 204
[   20.960078] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   21.161748] lp: driver loaded but no devices found
[   21.222962] ppdev: user-space parallel port driver
[   21.908329] intel_rng: FWH not detected
[   22.122665] cfg80211: Calling CRDA to update world regulatory domain
[   22.174624] ACPI Warning: 0x00001028-0x0000102f SystemIO conflicts with Region \PMIO 1 (20131115/utaddress-251)
[   22.174634] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   22.174640] ACPI Warning: 0x000011b0-0x000011bf SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)
[   22.174645] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   22.174648] ACPI Warning: 0x00001180-0x000011af SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)
[   22.174652] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   22.174655] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   22.385225] leds_ss4200: no LED devices found
[   22.399478] device-mapper: multipath: version 1.6.0 loaded
[   22.801551] Bluetooth: Core ver 2.17
[   22.801613] NET: Registered protocol family 31
[   22.801616] Bluetooth: HCI device and connection manager initialized
[   22.801629] Bluetooth: HCI socket layer initialized
[   22.801633] Bluetooth: L2CAP socket layer initialized
[   22.801640] Bluetooth: SCO socket layer initialized
[   22.872878] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   22.872883] Bluetooth: BNEP filters: protocol multicast
[   22.872894] Bluetooth: BNEP socket layer initialized
[   22.898601] Bluetooth: RFCOMM TTY layer initialized
[   22.898616] Bluetooth: RFCOMM socket layer initialized
[   22.898626] Bluetooth: RFCOMM ver 1.11
[   22.920682] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
[   22.964082] b43-phy0: Found PHY: Analog 4, Type 2 (G), Revision 8
[   22.997043] Broadcom 43xx driver loaded [ Features: PNL ]
[   23.318746] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   23.355929] init: cups main process (498) killed by HUP signal
[   23.355950] init: cups main process ended, respawning
[   23.503631] snd_hda_intel 0000:00:1b.0: irq 43 for MSI/MSI-X
[   23.603374] hda_codec: CX20549 (Venice): BIOS auto-probing.
[   23.603641] autoconfig: line_outs=1 (0x10/0x0/0x0/0x0/0x0) type:speaker
[   23.603644]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   23.603647]    hp_outs=1 (0x11/0x0/0x0/0x0/0x0)
[   23.603648]    mono: mono_out=0x0
[   23.603650]    dig-out=0x13/0x0
[   23.603652]    inputs:
[   23.603654]      Mic=0x14
[   23.609909] hda_codec: Enable sync_write for stable communication
[   23.660230] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   23.660754] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   24.213727] init: failsafe main process (583) killed by TERM signal
[   24.293298] input: HP WMI hotkeys as /devices/virtual/input/input11
[   24.755381] cfg80211: World regulatory domain updated:
[   24.755388] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   24.755392] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   24.755395] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   24.755398] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   24.755401] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   24.755403] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   28.564063] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[   28.605936] init: samba-ad-dc main process (765) terminated with status 1
[   28.672668] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   28.673114] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   28.687044] 8139too 0000:08:08.0 eth0: link down
[   28.687167] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   28.688338] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   29.919917] wlan0: authenticate with 00:1a:70:5a:c4:d1
[   29.932291] wlan0: send auth to 00:1a:70:5a:c4:d1 (try 1/3)
[   29.934854] wlan0: authenticated
[   29.935087] b43 ssb0:0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   29.935092] b43 ssb0:0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   29.936349] wlan0: associate with 00:1a:70:5a:c4:d1 (try 1/3)
[   29.941023] wlan0: RX AssocResp from 00:1a:70:5a:c4:d1 (capab=0x401 status=0 aid=2)
[   29.941457] wlan0: associated
[   29.941490] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   33.053922] init: plymouth-upstart-bridge main process ended, respawning
[   33.076668] init: plymouth-upstart-bridge main process ended, respawning
[  190.428290] perf samples too long (2511 > 2500), lowering kernel.perf_event_max_sample_rate to 50000
[  401.997628] perf samples too long (5005 > 5000), lowering kernel.perf_event_max_sample_rate to 25000
[ 7589.074685] PM: Syncing filesystems ... done.
[ 7589.216391] PM: Preparing system for mem sleep
[ 7589.216772] Freezing user space processes ... (elapsed 0.005 seconds) done.
[ 7589.221810] Freezing remaining freezable tasks ... (elapsed 0.001 seconds) done.
[ 7589.223315] PM: Entering mem sleep
[ 7589.223440] Suspending console(s) (use no_console_suspend to debug)
[ 7589.223834] wlan0: deauthenticating from 00:1a:70:5a:c4:d1 by local choice (reason=3)
[ 7589.328387] cfg80211: Calling CRDA to update world regulatory domain
[ 7589.328550] sd 2:0:0:0: [sda] Synchronizing SCSI cache
[ 7589.328644] sd 2:0:0:0: [sda] Stopping disk
[ 7589.448164] i8042 aux 00:07: System wakeup disabled by ACPI
[ 7589.488086] i8042 kbd 00:06: System wakeup enabled by ACPI
[ 7589.848121] PM: suspend of devices complete after 624.351 msecs
[ 7589.864174] PM: late suspend of devices complete after 16.028 msecs
[ 7589.880564] PM: noirq suspend of devices complete after 16.385 msecs
[ 7589.880725] ACPI: Preparing to enter system sleep state S3
[ 7589.928175] PM: Saving platform NVS memory
[ 7589.928860] Disabling non-boot CPUs ...
[ 7589.928860] ACPI: Low-level resume complete
[ 7589.928860] PM: Restoring platform NVS memory
[ 7589.928860] CPU0: Thermal monitoring handled by SMI
[ 7589.928860] ACPI: Waking up from system sleep state S3
[ 7590.024180] PM: noirq resume of devices complete after 94.371 msecs
[ 7590.024463] PM: early resume of devices complete after 0.248 msecs
[ 7590.104621] snd_hda_intel 0000:00:1b.0: irq 43 for MSI/MSI-X
[ 7590.104894] usb usb2: root hub lost power or was reset
[ 7590.105081] usb usb3: root hub lost power or was reset
[ 7590.105265] usb usb4: root hub lost power or was reset
[ 7590.105436] usb usb1: root hub lost power or was reset
[ 7590.109332] ehci-pci 0000:00:1d.7: cache line size of 64 is not supported
[ 7590.109760] 8139too 0000:08:08.0 eth0: link down
[ 7590.110419] ata2: port disabled--ignoring
[ 7590.348058] i8042 kbd 00:06: System wakeup disabled by ACPI
[ 7591.856429] ata1.00: ACPI cmd ef/03:0c:00:00:00:a0 (SET FEATURES) filtered out
[ 7591.856432] ata1.00: ACPI cmd ef/03:22:00:00:00:a0 (SET FEATURES) filtered out
[ 7591.888306] ata1.00: configured for MWDMA2
[ 7592.112064] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[ 7592.113130] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[ 7592.119290] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[ 7592.119295] ata3.00: configured for UDMA/100
[ 7592.132102] sd 2:0:0:0: [sda] Starting disk
[ 7592.520064] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[ 7592.612986] PM: resume of devices complete after 2588.516 msecs
[ 7592.613328] b43-pci-bridge 0000:06:00.0: no hotplug settings from platform
[ 7592.613342] PM: Finishing wakeup.
[ 7592.613344] Restarting tasks ... done.
[ 7592.639613] cfg80211: World regulatory domain updated:
[ 7592.639619] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 7592.639622] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 7592.639626] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 7592.639628] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 7592.639631] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 7592.639634] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 7592.720357] video LNXVIDEO:01: Restoring backlight state
[ 7593.857485] wlan0: authenticate with 00:1a:70:5a:c4:d1
[ 7593.868434] wlan0: send auth to 00:1a:70:5a:c4:d1 (try 1/3)
[ 7593.870915] wlan0: authenticated
[ 7593.871131] b43 ssb0:0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 7593.871135] b43 ssb0:0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 7593.872207] wlan0: associate with 00:1a:70:5a:c4:d1 (try 1/3)
[ 7593.874123] wlan0: RX AssocResp from 00:1a:70:5a:c4:d1 (capab=0x401 status=0 aid=2)
[ 7593.874579] wlan0: associated
[ 8685.968062] usb 1-6: new high-speed USB device number 2 using ehci-pci
[ 8686.112064] usb 1-6: New USB device found, idVendor=0bda, idProduct=2838
[ 8686.112072] usb 1-6: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 8686.112077] usb 1-6: Product: RTL2838UHIDIR
[ 8686.112080] usb 1-6: Manufacturer: Realtek
[ 8686.112083] usb 1-6: SerialNumber: 00000001
[ 8686.161078] rc_core: module verification failed: signature and/or  required key missing - tainting kernel
[ 8686.165242] WARNING: You are using an experimental version of the media stack.
[ 8686.165242]     As the driver is backported to an older kernel, it doesn't offer
[ 8686.165242]     enough quality for its usage in production.
[ 8686.165242]     Use it with care.
[ 8686.165242] Latest git patches (needed if you report a bug to [email]linux-media@vger.kernel.org[/email]):
[ 8686.165242]     d6d4c0e00fe559ef54b414e2e6266beaa50b4d8e [media] gpsca: remove the risk of a division by zero
[ 8686.165242]     4bad5d2d25099a42e146d7b18d2b98950ed287f5 [media] dvb_net: Convert local hex dump to print_hex_dump_debug
[ 8686.165242]     5c7c0ca02f01df4345fcf6c0b60281928d3e775e [media] dvb_net: Use standard debugging facilities
[ 8686.183003] WARNING: You are using an experimental version of the media stack.
[ 8686.183003]     As the driver is backported to an older kernel, it doesn't offer
[ 8686.183003]     enough quality for its usage in production.
[ 8686.183003]     Use it with care.
[ 8686.183003] Latest git patches (needed if you report a bug to [email]linux-media@vger.kernel.org[/email]):
[ 8686.183003]     d6d4c0e00fe559ef54b414e2e6266beaa50b4d8e [media] gpsca: remove the risk of a division by zero
[ 8686.183003]     4bad5d2d25099a42e146d7b18d2b98950ed287f5 [media] dvb_net: Convert local hex dump to print_hex_dump_debug
[ 8686.183003]     5c7c0ca02f01df4345fcf6c0b60281928d3e775e [media] dvb_net: Use standard debugging facilities
[ 8686.194080] usb 1-6: dvb_usb_v2: found a 'Realtek RTL2832U reference design' in warm state
[ 8686.254296] usb 1-6: dvb_usb_v2: will pass the complete MPEG2 transport stream to the software demuxer
[ 8686.254327] DVB: registering new adapter (Realtek RTL2832U reference design)
[ 8686.295018] i2c i2c-6: Added multiplexed i2c bus 7
[ 8686.295026] rtl2832 6-0010: Realtek RTL2832 successfully attached
[ 8686.295041] usb 1-6: DVB: registering adapter 0 frontend 0 (Realtek RTL2832 (DVB-T))...
[ 8686.310601] r820t 7-001a: creating new instance
[ 8686.318078] r820t 7-001a: Rafael Micro r820t successfully identified
[ 8686.330465] media: Linux media interface: v0.10
[ 8686.340621] Linux video capture interface: v2.00
[ 8686.340628] WARNING: You are using an experimental version of the media stack.
[ 8686.340628]     As the driver is backported to an older kernel, it doesn't offer
[ 8686.340628]     enough quality for its usage in production.
[ 8686.340628]     Use it with care.
[ 8686.340628] Latest git patches (needed if you report a bug to [email]linux-media@vger.kernel.org[/email]):
[ 8686.340628]     d6d4c0e00fe559ef54b414e2e6266beaa50b4d8e [media] gpsca: remove the risk of a division by zero
[ 8686.340628]     4bad5d2d25099a42e146d7b18d2b98950ed287f5 [media] dvb_net: Convert local hex dump to print_hex_dump_debug
[ 8686.340628]     5c7c0ca02f01df4345fcf6c0b60281928d3e775e [media] dvb_net: Use standard debugging facilities
[ 8686.358161] rtl2832_sdr rtl2832_sdr.0.auto: Registered as swradio0
[ 8686.358167] rtl2832_sdr rtl2832_sdr.0.auto: Realtek RTL2832 SDR attached
[ 8686.358171] rtl2832_sdr rtl2832_sdr.0.auto: SDR API is still slightly experimental and functionality changes may follow
[ 8686.364817] Registered IR keymap rc-empty
[ 8686.364946] input: Realtek RTL2832U reference design as /devices/pci0000:00/0000:00:1d.7/usb1/1-6/rc/rc0/input12
[ 8686.367090] rc0: Realtek RTL2832U reference design as /devices/pci0000:00/0000:00:1d.7/usb1/1-6/rc/rc0
[ 8686.385354] IR NEC protocol handler initialized
[ 8686.391537] IR RC5(x/sz) protocol handler initialized
[ 8686.397984] IR RC6 protocol handler initialized
[ 8686.400871] IR JVC protocol handler initialized
[ 8686.409133] IR Sony protocol handler initialized
[ 8686.415630] IR SANYO protocol handler initialized
[ 8686.420119] IR Sharp protocol handler initialized
[ 8686.426134] IR MCE Keyboard/mouse protocol handler initialized
[ 8686.434374] lirc_dev: IR Remote Control driver registered, major 250 
[ 8686.437417] input: MCE IR Keyboard/Mouse (dvb_usb_rtl28xxu) as /devices/virtual/input/input13
[ 8686.437891] usb 1-6: dvb_usb_v2: schedule remote query interval to 400 msecs
[ 8686.441966] rc rc0: lirc_dev: driver ir-lirc-codec (dvb_usb_rtl28xxu) registered at minor = 0
[ 8686.441973] IR LIRC bridge handler initialized
[ 8686.445762] IR XMP protocol handler initialized
[ 8686.451061] usb 1-6: dvb_usb_v2: 'Realtek RTL2832U reference design' successfully initialized and connected
[ 8686.451505] usbcore: registered new interface driver dvb_usb_rtl28xxu
[16529.795314] usb 1-6: USB disconnect, device number 2
[16529.798557] r820t 7-001a: destroying instance
[16529.798749] usb 1-6: dvb_usb_v2: 'Realtek RTL2832U reference design' successfully deinitialized and disconnected
[16531.508065] usb 1-6: new high-speed USB device number 3 using ehci-pci
[16531.652040] usb 1-6: New USB device found, idVendor=0bda, idProduct=2838
[16531.652047] usb 1-6: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[16531.652051] usb 1-6: Product: RTL2838UHIDIR
[16531.652054] usb 1-6: Manufacturer: Realtek
[16531.652057] usb 1-6: SerialNumber: 00000001
[16531.659036] usb 1-6: dvb_usb_v2: found a 'Realtek RTL2832U reference design' in warm state
[16531.716262] usb 1-6: dvb_usb_v2: will pass the complete MPEG2 transport stream to the software demuxer
[16531.716289] DVB: registering new adapter (Realtek RTL2832U reference design)
[16531.721478] i2c i2c-6: Added multiplexed i2c bus 7
[16531.721484] rtl2832 6-0010: Realtek RTL2832 successfully attached
[16531.721498] usb 1-6: DVB: registering adapter 0 frontend 0 (Realtek RTL2832 (DVB-T))...
[16531.721648] r820t 7-001a: creating new instance
[16531.729036] r820t 7-001a: Rafael Micro r820t successfully identified
[16531.731176] rtl2832_sdr rtl2832_sdr.0.auto: Registered as swradio0
[16531.731182] rtl2832_sdr rtl2832_sdr.0.auto: Realtek RTL2832 SDR attached
[16531.731186] rtl2832_sdr rtl2832_sdr.0.auto: SDR API is still slightly experimental and functionality changes may follow
[16531.739665] Registered IR keymap rc-empty
[16531.739764] input: Realtek RTL2832U reference design as /devices/pci0000:00/0000:00:1d.7/usb1/1-6/rc/rc0/input14
[16531.739995] rc0: Realtek RTL2832U reference design as /devices/pci0000:00/0000:00:1d.7/usb1/1-6/rc/rc0
[16531.740340] input: MCE IR Keyboard/Mouse (dvb_usb_rtl28xxu) as /devices/virtual/input/input15
[16531.742081] rc rc0: lirc_dev: driver ir-lirc-codec (dvb_usb_rtl28xxu) registered at minor = 0
[16531.742089] usb 1-6: dvb_usb_v2: schedule remote query interval to 400 msecs
[16531.752108] usb 1-6: dvb_usb_v2: 'Realtek RTL2832U reference design' successfully initialized and connected
```


 I am using linux mint right now. But I have tried this same thing on ubunto `12.04 and had no luck.

---

### Post by Bucky Ball on 2015-02-13
Output between ```
 tags, please. Neater, space-saving and easier to read. Instructions for doing so in the last link in my signature.

Linux Mint is not supported in the main areas here. Even though based on Ubuntu, there are differences. There is a sub-forum for it [here]("http://ubuntuforums.org/forumdisplay.php?f=453"). 

I suggest you remove whatever driver you've installed for it, namely this:

 [code]WARNING: You are using an experimental version of the media stack.
[ 8686.165242]     As the driver is backported to an older kernel, it doesn't offer
[ 8686.165242]     enough quality for its usage in production.
[ 8686.165242]     Use it with care.
[ 8686.165242] Latest git patches (needed if you report a bug to linux-media@vger.kernel.org):
[ 8686.165242]     d6d4c0e00fe559ef54b414e2e6266beaa50b4d8e [media] gpsca: remove the risk of a division by zero
[ 8686.165242]     4bad5d2d25099a42e146d7b18d2b98950ed287f5 [media] dvb_net: Convert local hex dump to print_hex_dump_debug
[ 8686.165242]     5c7c0ca02f01df4345fcf6c0b60281928d3e775e [media] dvb_net: Use standard debugging facilities
``` 

Probably just getting in the way and confusing the issue. As mentioned, the drivers for that dongle are already in the kernel in 14.04. Install 14.04 LTS and it should kick up without a fuss. There are workarounds for 12.04 and your card (like installing the 14.04 kernel), but they are a bit redundant now. May as well just try 14.04 on another partition to start, if you're able, and try it out in that.

[This]("http://ubuntuhandbook.org/index.php/2014/01/linux-kernel-3-13-install-in-ubuntu-linux-mint/") will get you there without installing 14.04. It will install the correct kernel, with correct drivers for your card, in 12.04 LTS. The way I did it when I was using 12.04 LTS. I've only ever used my Ezycap TV dongle for watching TV. There is no DAB+ solution in Ubuntu/Linux at this point, oddly and unfortunately, but there is SDR. Seems like quite an adventure to get that up and working, but I realise, you need to get the dongle recognised first. Have you tried something like MeTV to see if that sees it? The hardware stack in the latest 12.04 may just do it. 

It seems from your output that your system knows exactly what it is, and from this:

```
[16531.752108] usb 1-6: dvb_usb_v2: 'Realtek RTL2832U reference design' successfully initialized and connected
```

... has installed the driver and all is well. Maybe it's your SDR setup or whatever software you're using. As I asked previously, what are you using to try and get radio going?

Good luck. ;)

---

### Post by ineedwifihelp on 2015-02-15
Thanks for your help. I'm going to just give up on this. It's beyond me.

---

### Post by Bucky Ball on 2015-02-15
You might want to try the [Mint]("http://forums.linuxmint.com/") forums. There could be differences between my 'buntu setup and your Mint install I have no idea about. As I say though, your dmesg output:

```
[16531.752108] usb 1-6: dvb_usb_v2: 'Realtek RTL2832U reference design' successfully initialized and connected
```

Shows the card is recognised, drivers loaded and good to go. I'm thinking it is something to do with the software you are attempting to use and its configuration. I have no idea what software you have installed and are trying to use, so can't help there. 

Good luck.

---

