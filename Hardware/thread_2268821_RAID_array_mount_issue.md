---
title: "RAID array mount issue"
date: 2015-03-11
forum: Hardware
---

### Post by erictherev on 2015-03-11
I'm working on a Kubuntu 14 fileserver system I built. I had (miraculously and by some unknown means) mounted a RAID0 array and it was working fine until one of the drives failed. Thinking I had lost all data on the array, I shut the system down, pulled the failed drive and put in a new one, then recreated the array in the Motherboard's RAID tool. 

After booting the system, fdisk sees the drives, as does dmesg. Unfortunately, parted does not see the array so I am unable to format the drive. also, attempting to mount the drive has had no noticeable results.

Here is what I get with fdisk:
```
itlce@LCE-NAS:~$ sudo fdisk -l

Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x88e11e19

Device     Boot    Start       End   Sectors   Size Id Type
/dev/sda1  *        2048  31999999  31997952  15.3G 82 Linux swap / Solaris
/dev/sda2       32000000 976773119 944773120 450.5G 83 Linux

[COLOR="#008000"]Disk /dev/sdb: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk /dev/sdc: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes[/COLOR]
Disk /dev/sdd: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0xc5178cc7

Device     Boot Start        End    Sectors  Size Id Type
/dev/sdd1        2048 3907028991 3907026944  1.8T 83 Linux

Disk /dev/sde: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x63bcc82a

Device     Boot      Start        End    Sectors   Size Id Type
/dev/sde1             2048 1953511423 1953509376 931.5G 83 Linux
/dev/sde2       1953511424 3907028991 1953517568 931.5G 83 Linux

[COLOR="#008000"]Disk /dev/md127: 3.7 TiB, 4000529252352 bytes, 7813533696 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 524288 bytes / 1048576 bytes[/COLOR]
```

And here is the result of dmesg:
```
[    1.023337] ata6: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    1.023353] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.024025] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20140424/psargs-359)
[    1.024028] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT5._GTF] (Node ffff8802170553e8), AE_NOT_FOUND (20140424/psparse-536)
[    1.024526] ata6.00: ATA-9: ST2000DM001-1CH164, CC29, max UDMA/133
[    1.024528] ata6.00: 3907029168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.025045] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20140424/psargs-359)
[    1.025049] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT5._GTF] (Node ffff8802170553e8), AE_NOT_FOUND (20140424/psparse-536)
[    1.025406] ata6.00: configured for UDMA/133
[    1.025698] ata2.00: ATAPI: msi     DVD-RW DH24AS, LM21, max UDMA/100
[    1.026546] ata2.00: configured for UDMA/100
[    1.027326] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    1.027340] ata4: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    1.027362] ata5: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    1.027373] ata3: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    1.027834] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20140424/psargs-359)
[    1.027837] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT2._GTF] (Node ffff880217055280), AE_NOT_FOUND (20140424/psparse-536)
[    1.028114] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20140424/psargs-359)
[    1.028118] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT4._GTF] (Node ffff880217055370), AE_NOT_FOUND (20140424/psparse-536)
[    1.028272] ata3.00: ATA-9: ST2000DM001-1ER164, CC25, max UDMA/133
[    1.028274] ata3.00: 3907029168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.028543] ata4.00: ATA-9: ST2000DM001-1CH164, CC29, max UDMA/133
[    1.028544] ata4.00: 3907029168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.028570] ata5.00: ATA-9: ST2000DM001-1CH164, CC29, max UDMA/133
[    1.028572] ata5.00: 3907029168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.028636] ata1.00: ATA-8: ST500DM002-1BD142, KC48, max UDMA/133
[    1.028638] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.028787] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20140424/psargs-359)
[    1.028790] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT2._GTF] (Node ffff880217055280), AE_NOT_FOUND (20140424/psparse-536)
[    1.029068] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20140424/psargs-359)
[    1.029072] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT4._GTF] (Node ffff880217055370), AE_NOT_FOUND (20140424/psparse-536)
[    1.029160] ata3.00: configured for UDMA/133
[    1.029395] ata4.00: configured for UDMA/133
[    1.029411] ata5.00: configured for UDMA/133
[    1.030172] ata1.00: configured for UDMA/133
[    1.030324] scsi 0:0:0:0: Direct-Access     ATA      ST500DM002-1BD14 KC48 PQ: 0 ANSI: 5
[    1.030478] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.030488] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.030489] sd 0:0:0:0: [sda] 4096-byte physical blocks
[    1.030534] sd 0:0:0:0: [sda] Write Protect is off
[    1.030535] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.030546] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.031689] scsi 1:0:0:0: CD-ROM            msi      DVD-RW DH24AS    LM21 PQ: 0 ANSI: 5
[    1.043740] usb 1-1: New USB device found, idVendor=8087, idProduct=8008
[    1.043742] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.044002] hub 1-1:1.0: USB hub found
[    1.044082] hub 1-1:1.0: 6 ports detected
[    1.047881]  sda: sda1 sda2
[    1.048183] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.050103] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.050106] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.050191] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.050226] sr 1:0:0:0: Attached scsi generic sg1 type 5
[COLOR="#008000"][    1.050294] scsi 2:0:0:0: Direct-Access     ATA      ST2000DM001-1ER1 CC25 PQ: 0 ANSI: 5
[    1.050402] sd 2:0:0:0: [sdb] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
[    1.050404] sd 2:0:0:0: [sdb] 4096-byte physical blocks
[    1.050433] sd 2:0:0:0: [sdb] Write Protect is off
[    1.050435] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.050437] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    1.050452] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.050507] scsi 3:0:0:0: Direct-Access     ATA      ST2000DM001-1CH1 CC29 PQ: 0 ANSI: 5
[    1.050594] sd 3:0:0:0: Attached scsi generic sg3 type 0
[    1.050625] sd 3:0:0:0: [sdc] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
[    1.050626] sd 3:0:0:0: [sdc] 4096-byte physical blocks
[    1.050644] scsi 4:0:0:0: Direct-Access     ATA      ST2000DM001-1CH1 CC29 PQ: 0 ANSI: 5
[    1.050651] sd 3:0:0:0: [sdc] Write Protect is off
[    1.050652] sd 3:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    1.050662] sd 3:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA[/COLOR]
[    1.050762] sd 4:0:0:0: Attached scsi generic sg4 type 0
[    1.050790] sd 4:0:0:0: [sdd] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
[    1.050791] sd 4:0:0:0: [sdd] 4096-byte physical blocks
[    1.050809] scsi 5:0:0:0: Direct-Access     ATA      ST2000DM001-1CH1 CC29 PQ: 0 ANSI: 5
[    1.050814] sd 4:0:0:0: [sdd] Write Protect is off
[    1.050815] sd 4:0:0:0: [sdd] Mode Sense: 00 3a 00 00
[    1.050826] sd 4:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.050918] sd 5:0:0:0: Attached scsi generic sg5 type 0
[    1.050946] sd 5:0:0:0: [sde] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
[    1.050947] sd 5:0:0:0: [sde] 4096-byte physical blocks
[    1.050975] sd 5:0:0:0: [sde] Write Protect is off
[    1.050976] sd 5:0:0:0: [sde] Mode Sense: 00 3a 00 00
[    1.050987] sd 5:0:0:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.063888]  sdd: sdd1
[    1.063994] sd 4:0:0:0: [sdd] Attached SCSI disk
[COLOR="#008000"][    1.065886]  sdc: unknown partition table
[    1.065973] sd 3:0:0:0: [sdc] Attached SCSI disk[/COLOR]
[    1.067702]  sde: sde1 sde2
[    1.067962] sd 5:0:0:0: [sde] Attached SCSI disk
[COLOR="#008000"][    1.069707]  sdb: unknown partition table
[    1.069881] sd 2:0:0:0: [sdb] Attached SCSI disk
[    1.099655] md: bind<sdb>
[    1.106089] md: bind<sdc>
[    1.107720] md: raid0 personality registered for level 0
[    1.107851] md/raid0:md127: md_size is 7813533696 sectors.
[    1.107852] md: RAID0 configuration for md127 - 1 zone
[    1.107853] md: zone0=[sdb/sdc]
[    1.107855]       zone-offset=         0KB, device-offset=         0KB, size=3906766848KB

[    1.107861] md127: detected capacity change from 0 to 4000529252352
[    1.135329]  md127: unknown partition table[/COLOR]
[    1.155272] usb 2-1: new high-speed USB device number 2 using ehci-pci
[    1.291651] usb 2-1: New USB device found, idVendor=8087, idProduct=8000
[    1.291654] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.291892] hub 2-1:1.0: USB hub found
[    1.291997] hub 2-1:1.0: 8 ports detected
[    1.306299] random: nonblocking pool is initialized
[    1.463153] usb 3-14: new low-speed USB device number 2 using xhci_hcd
[    1.479994] device-mapper: table: 252:0: striped: Couldn't parse stripe destination
[    1.479997] device-mapper: ioctl: error adding target to table
[    1.486093] device-mapper: table: 252:0: striped: Couldn't parse stripe destination
[    1.486096] device-mapper: ioctl: error adding target to table
[    1.519130] tsc: Refined TSC clocksource calibration: 2993.068 MHz
[    1.598572] usb 3-14: New USB device found, idVendor=0557, idProduct=2221
[    1.598575] usb 3-14: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.598576] usb 3-14: Product: UC-10KM V1.3.124
[    1.598577] usb 3-14: Manufacturer: ATEN
[    1.598578] usb 3-14: SerialNumber: USB Composite device
[    1.598728] usb 3-14: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
[    1.598731] usb 3-14: ep 0x82 - rounding interval to 64 microframes, ep desc says 80 microframes
[    1.604594] hidraw: raw HID events driver (C) Jiri Kosina
[    1.614193] usbcore: registered new interface driver usbhid
[    1.614196] usbhid: USB HID core driver
[    1.614950] md: linear personality registered for level -1
[    1.615347] input: ATEN UC-10KM V1.3.124 as /devices/pci0000:00/0000:00:14.0/usb3/3-14/3-14:1.0/0003:0557:2221.0001/input/input6
[    1.616189] hid-generic 0003:0557:2221.0001: input,hidraw0: USB HID v1.10 Keyboard [ATEN UC-10KM V1.3.124] on usb-0000:00:14.0-14/input0
[    1.616262] input: ATEN UC-10KM V1.3.124 as /devices/pci0000:00/0000:00:14.0/usb3/3-14/3-14:1.1/0003:0557:2221.0002/input/input7
[    1.616374] hid-generic 0003:0557:2221.0002: input,hidraw1: USB HID v1.10 Mouse [ATEN UC-10KM V1.3.124] on usb-0000:00:14.0-14/input1
[    1.617507] md: multipath personality registered for level -4
[    1.620143] md: raid1 personality registered for level 1
[    1.687052] raid6: sse2x1    9669 MB/s
[    1.755028] raid6: sse2x2   12217 MB/s
[    1.823004] raid6: sse2x4   14078 MB/s
[    1.823005] raid6: using algorithm sse2x4 (14078 MB/s)
[    1.823006] raid6: using ssse3x2 recovery algorithm
[    1.823820] xor: measuring software checksum speed
[    1.862998]    prefetch64-sse: 20364.000 MB/sec
[    1.902982]    generic_sse: 18341.000 MB/sec
[    1.902983] xor: using function: prefetch64-sse (20364.000 MB/sec)
[    1.903776] async_tx: api initialized (async)
[    1.908329] md: raid6 personality registered for level 6
[    1.908330] md: raid5 personality registered for level 5
[    1.908331] md: raid4 personality registered for level 4
[    1.911858] md: raid10 personality registered for level 10
[    1.967028] Btrfs loaded
[    2.062274] BTRFS: device fsid a3d83995-4f83-46a9-a7da-24296268e25c devid 1 transid 22586 /dev/sda2
[    2.063040] BTRFS: device label NAS devid 1 transid 85 /dev/sdd1
[    2.063719] BTRFS: device label CIRBAK devid 1 transid 1864 /dev/sde1
[    2.064139] BTRFS: device label LCEBAK devid 1 transid 1150 /dev/sde2
[    2.064718] BTRFS: device fsid 254488a9-c64f-41b3-b066-445ce9a93fc2 devid 1 transid 6 /dev/md127
[    2.069053] BTRFS info (device sda2): disk space caching is enabled
[    2.518783] Switched to clocksource tsc
[    2.818776] [drm] Enabling RC6 states: RC6 on, RC6p off, RC6pp off
[    3.074764] init: plymouth-upstart-bridge main process (388) killed by TERM signal
[    8.306789] Adding 15998972k swap on /dev/sda1.  Priority:-1 extents:1 across:15998972k FS
[    8.681293] BTRFS info (device sda2): disk space caching is enabled
[   10.331977] systemd-udevd[675]: starting version 208
[   10.383626] lp: driver loaded but no devices found
[   10.385664] ppdev: user-space parallel port driver
[   10.387333] parport_pc 00:05: reported by Plug and Play ACPI
[   10.387377] parport0: PC-style at 0x378, irq 5 [PCSPP]
[   10.479227] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   10.483988] lp0: using parport0 (interrupt-driven).
[   10.492281] mei_me 0000:00:16.0: irq 45 for MSI/MSI-X
[   10.580798] audit: type=1400 audit(1426106973.452:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=763 comm="apparmor_parser"
[   10.580803] audit: type=1400 audit(1426106973.452:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=763 comm="apparmor_parser"
[   10.580806] audit: type=1400 audit(1426106973.452:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=763 comm="apparmor_parser"
[   10.641508] snd_hda_intel 0000:00:03.0: irq 46 for MSI/MSI-X
[   10.648011] snd_hda_intel 0000:00:1b.0: irq 47 for MSI/MSI-X
[   10.648402] intel_rapl: Found RAPL domain package
[   10.648405] intel_rapl: Found RAPL domain core
[   10.648407] intel_rapl: Found RAPL domain uncore
[   10.648408] intel_rapl: Found RAPL domain dram
[   10.670140] input: HDA Intel HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:03.0/sound/card0/input8
[   10.670187] input: HDA Intel HDMI HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:03.0/sound/card0/input9
[   10.673648] device-mapper: multipath: version 1.7.0 loaded
[   10.674464] sound hdaudioC1D0: autoconfig: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:line
[   10.674466] sound hdaudioC1D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   10.674468] sound hdaudioC1D0:    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0)
[   10.674469] sound hdaudioC1D0:    mono: mono_out=0x0
[   10.674469] sound hdaudioC1D0:    inputs:
[   10.674471] sound hdaudioC1D0:      Front Mic=0x19
[   10.674472] sound hdaudioC1D0:      Rear Mic=0x18
[   10.674473] sound hdaudioC1D0:      Line=0x1a
[   10.691591] input: HDA Intel PCH Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card1/input10
[   10.691670] input: HDA Intel PCH Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card1/input11
[   10.691742] input: HDA Intel PCH Line as /devices/pci0000:00/0000:00:1b.0/sound/card1/input12
[   10.691987] input: HDA Intel PCH Line Out as /devices/pci0000:00/0000:00:1b.0/sound/card1/input13
[   10.692158] input: HDA Intel PCH Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card1/input14
[   10.744307] audit: type=1400 audit(1426106973.616:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=845 comm="apparmor_parser"
[   10.744313] audit: type=1400 audit(1426106973.616:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=845 comm="apparmor_parser"
[   10.744315] audit: type=1400 audit(1426106973.616:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="third_party" pid=845 comm="apparmor_parser"
[   10.785412] Bluetooth: Core ver 2.19
[   10.785426] NET: Registered protocol family 31
[   10.785427] Bluetooth: HCI device and connection manager initialized
[   10.785842] Bluetooth: HCI socket layer initialized
[   10.785844] Bluetooth: L2CAP socket layer initialized
[   10.785850] Bluetooth: SCO socket layer initialized
[   10.795440] Bluetooth: RFCOMM TTY layer initialized
[   10.795448] Bluetooth: RFCOMM socket layer initialized
[   10.795452] Bluetooth: RFCOMM ver 1.11
[   10.821697] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   10.821699] Bluetooth: BNEP filters: protocol multicast
[   10.821706] Bluetooth: BNEP socket layer initialized
[   10.941322] asus_wmi: ASUS WMI generic driver loaded
[   10.943410] asus_wmi: Initialization: 0x0
[   10.943424] asus_wmi: BIOS WMI version: 0.9
[   10.943448] asus_wmi: SFUN value: 0x0
[   10.943675] input: Eee PC WMI hotkeys as /devices/platform/eeepc-wmi/input/input15
[   10.944269] asus_wmi: Backlight controlled by ACPI video driver
[   11.035822] init: cups main process (846) killed by HUP signal
[   11.035828] init: cups main process ended, respawning
[   11.144762] init: failsafe main process (966) killed by TERM signal
[   11.562014] audit: type=1400 audit(1426106974.432:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=1187 comm="apparmor_parser"
[   11.562020] audit: type=1400 audit(1426106974.432:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="chromium" pid=1187 comm="apparmor_parser"
[   11.563064] audit: type=1400 audit(1426106974.432:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=1187 comm="apparmor_parser"
[   11.563069] audit: type=1400 audit(1426106974.432:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1187 comm="apparmor_parser"
[   11.869032] systemd-logind[1217]: New seat seat0.
[   11.869267] systemd-logind[1217]: Watching system buttons on /dev/input/event1 (Power Button)
[   11.869302] systemd-logind[1217]: Watching system buttons on /dev/input/event2 (Video Bus)
[   11.869332] systemd-logind[1217]: Watching system buttons on /dev/input/event0 (Power Button)
[   11.971466] e1000e 0000:00:19.0: irq 43 for MSI/MSI-X
[   12.075352] e1000e 0000:00:19.0: irq 43 for MSI/MSI-X
[   12.075431] IPv6: ADDRCONF(NETDEV_UP): eth2: link is not ready
[   12.083778] r8169 0000:04:00.0 eth0: link down
[   12.083794] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   12.091792] r8169 0000:04:01.0 eth1: link down
[   12.091816] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[   12.798180] init: samba-ad-dc main process (1396) terminated with status 1
[   13.635747] device-mapper: table: 252:1: striped: Couldn't parse stripe destination
[   13.635750] device-mapper: ioctl: error adding target to table
[   13.642895] device-mapper: table: 252:0: striped: Couldn't parse stripe destination
[   13.642898] device-mapper: ioctl: error adding target to table
[   15.128768] systemd-logind[1217]: Failed to start unit user@111.service: Unknown unit: user@111.service
[   15.128773] systemd-logind[1217]: Failed to start user service: Unknown unit: user@111.service
[   15.131122] systemd-logind[1217]: New session c1 of user lightdm.
[   15.131135] systemd-logind[1217]: Linked /tmp/.X11-unix/X0 to /run/user/111/X11-display.
[   15.208473] Fusion MPT base driver 3.04.20
[   15.208475] Copyright (c) 1999-2008 LSI Corporation
[   15.209756] Fusion MPT misc device (ioctl) driver 3.04.20
[   15.209804] mptctl: Registered with Fusion MPT base driver
[   15.209806] mptctl: /dev/mptctl @ (major,minor=10,220)
[   15.631649] e1000e: eth2 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
[   15.631679] IPv6: ADDRCONF(NETDEV_CHANGE): eth2: link becomes ready
[   27.344734] systemd-logind[1217]: Failed to start unit user@1000.service: Unknown unit: user@1000.service
[   27.344739] systemd-logind[1217]: Failed to start user service: Unknown unit: user@1000.service
[   27.364346] systemd-logind[1217]: New session c2 of user administrator.
[   27.364361] systemd-logind[1217]: Linked /tmp/.X11-unix/X0 to /run/user/1000/X11-display.
[   40.840805] audit_printk_skb: 48 callbacks suppressed
[   40.840808] audit: type=1400 audit(1426107003.730:28): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=3329 comm="apparmor_parser"
[   40.840813] audit: type=1400 audit(1426107003.730:29): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=3329 comm="apparmor_parser"
[   40.850136] audit: type=1400 audit(1426107003.742:30): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="third_party" pid=3329 comm="apparmor_parser"
[  129.503055] systemd-logind[1217]: Failed to start unit user@1001.service: Unknown unit: user@1001.service
[  129.503067] systemd-logind[1217]: Failed to start user service: Unknown unit: user@1001.service
[  129.510773] systemd-logind[1217]: New session 1 of user itlce.
[  238.487924] BTRFS info (device md127): disk space caching is enabled
[  361.817474] BTRFS info (device md127): disk space caching is enabled

```

I am administrating this system in an office environment and would really like for people to see the benefits of open-source, so getting this back up and running is a bit of a priority.

Any help anyone can offer is greatly appreciated.

---

### Post by tgalati4 on 2015-03-12
Are you sure you were using RAID0?  Typically you can't rebuild a RAID0 if you pull out a drive.  With RAID1 (mirror of two drives), you can reimage the new drive to get a working RAID1 array.  

I don't think *fdisk* can handle any RAID configuration.  It can mark partitions as type "software RAID", but the management of software RAID is handled by *mdadm* not *fdisk*.  If you used the BIOS to format the RAID, then you are using hardware RAID and the array should show up a a single volume in *fdisk*.

I'm confused.

---

### Post by erictherev on 2015-03-12
> **tgalati4 said:**
> Are you sure you were using RAID0?
Yes, I'm using RAID0 (stripe).
> **tgalati4 said:**
> Typically you can't rebuild a RAID0 if you pull out a drive. 
I fully expected to have lost all data from the array.
> **tgalati4 said:**
> If you used the BIOS to format the RAID, then you are using hardware RAID and the array should show up a a single volume in *fdisk*. 
fdisk shows a single volume. Unfortunately, BIOS offers no formatting options. I am trying to use parted to format the array, but parted doesn't see it.
> **tgalati4 said:**
> the management of software RAID is handled by *mdadm* not *fdisk*.
mdadm probably works great for software raid. I'm using hardware raid.


I'm looking for a way to format the hardware RAID0 as btrfs and make the array usable. I included the results of *fdisk -l* and *dmesg* in my original post to show what the OS is seeing of the array.


Any suggestions would be greatly appreciated.

---

### Post by tgalati4 on 2015-03-12
Have you tried to update the RAID BIOS?   Perhaps your hardware RAID is really fakeRAID and you might need to use software RAID afterall.  What is the make and model of the RAID controller?  What is the version of the RAID BIOS?

Sometimes the server manufacturer has a CD with RAID utilities for formating and reconfiguring--things that can't be done from the RAID BIOS.

---

### Post by erictherev on 2015-03-12
> **tgalati4 said:**
> Have you tried to update the RAID BIOS?   Perhaps your hardware RAID is really fakeRAID and you might need to use software RAID afterall.  What is the make and model of the RAID controller?  What is the version of the RAID BIOS?

Sometimes the server manufacturer has a CD with RAID utilities for formating and reconfiguring--things that can't be done from the RAID BIOS.

I believe what I am trying to do can be done without resorting to any of this since I had done it before. 

I'll have to look up the BIOS info you asked for. In the meantime, I found this in the dmesg output I had posted:

```
[    1.479994] device-mapper: table: 252:0: striped: Couldn't parse stripe destination
[    1.479997] device-mapper: ioctl: error adding target to table
[    1.486093] device-mapper: table: 252:0: striped: Couldn't parse stripe destination
[    1.486096] device-mapper: ioctl: error adding target to table
```

I'm not sure if that's relevant, but I thought it might be worth mentioning.

Thanks for your help.

---

### Post by erictherev on 2015-03-12
As far as the BIOS info goes -

lspci:
```
itlce@LCE-NAS:~$lspci
00:00.0 Host bridge: Intel Corporation 4th Gen Core Processor DRAM Controller (rev 06)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller (rev 06)
00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller (rev 06)
00:03.0 Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06)
00:14.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI (rev 05)
00:16.0 Communication controller: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 (rev 04)
00:16.3 Serial controller: Intel Corporation 8 Series/C220 Series Chipset Family KT Controller (rev 04)
00:19.0 Ethernet controller: Intel Corporation Ethernet Connection I217-LM (rev 05)
00:1a.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 (rev d5)
00:1c.3 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d5)
00:1d.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation Q87 Express LPC Controller (rev 05)
00:1f.2 RAID bus controller: Intel Corporation SATA Controller [RAID mode] (rev 05)
00:1f.3 SMBus: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller (rev 05)
03:00.0 PCI bridge: ASMedia Technology Inc. ASM1083/1085 PCIe to PCI Bridge (rev 04)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8169 PCI Gigabit Ethernet Controller (rev 10)
04:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8169 PCI Gigabit Ethernet Controller (rev 10)
```

dmesg (part 1):
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.16.0-31-generic (buildd@batsu) (gcc version 4.9.1 (Ubuntu 4.9.1-16ubuntu6) ) #41-Ubuntu SMP Tue Feb 10 15:24:04 UTC 2015 (Ubuntu 3.16.0-31.41-generic 3.16.7-ckt5)
[    0.000000] Command line: BOOT_IMAGE=/@/boot/vmlinuz-3.16.0-31-generic root=UUID=a3d83995-4f83-46a9-a7da-24296268e25c ro rootflags=subvol=@ quiet splash nomdmonddf nomdmonisw vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x0000000000091bff] usable
[    0.000000] BIOS-e820: [mem 0x0000000000091c00-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000c53bffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000c53c0000-0x00000000c53c6fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000c53c7000-0x00000000c5811fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000c5812000-0x00000000c5c73fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000c5c74000-0x00000000d8700fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000d8701000-0x00000000d8908fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000d8909000-0x00000000d891efff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000d891f000-0x00000000d8e5afff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000d8e5b000-0x00000000d9ffefff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000d9fff000-0x00000000d9ffffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000dc000000-0x00000000de1fffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000f8000000-0x00000000fbffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed00000-0x00000000fed03fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ff000000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000021fdfffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.7 present.
[    0.000000] DMI: ASUS All Series/Q87M-E, BIOS 0906 11/28/2013
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] AGP: No AGP bridge found
[    0.000000] e820: last_pfn = 0x21fe00 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-DBFFF write-protect
[    0.000000]   DC000-E7FFF uncachable
[    0.000000]   E8000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask 7E00000000 write-back
[    0.000000]   1 base 0200000000 mask 7FE0000000 write-back
[    0.000000]   2 base 00E0000000 mask 7FE0000000 uncachable
[    0.000000]   3 base 00DC000000 mask 7FFC000000 uncachable
[    0.000000]   4 base 021FE00000 mask 7FFFE00000 uncachable
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000]   8 disabled
[    0.000000]   9 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 8GB, type WB
[    0.000000] reg 1, base: 8GB, range: 512MB, type WB
[    0.000000] reg 2, base: 3584MB, range: 512MB, type UC
[    0.000000] reg 3, base: 3520MB, range: 64MB, type UC
[    0.000000] reg 4, base: 8702MB, range: 2MB, type UC
[    0.000000] total RAM covered: 8126M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K  chunk_size: 128M        num_reg: 7      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3GB, range: 512MB, type WB
[    0.000000] reg 3, base: 3520MB, range: 64MB, type UC
[    0.000000] reg 4, base: 4GB, range: 4GB, type WB
[    0.000000] reg 5, base: 8GB, range: 512MB, type WB
[    0.000000] reg 6, base: 8702MB, range: 2MB, type UC
[    0.000000] e820: update [mem 0xdc000000-0xffffffff] usable ==> reserved
[    0.000000] e820: last_pfn = 0xda000 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [mem 0x000fd7e0-0x000fd7ef] mapped at [ffff8800000fd7e0]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff88000008b000] 8b000 size 24576
[    0.000000] Using GB pages for direct mapping
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x01fd2000, 0x01fd2fff] PGTABLE
[    0.000000] BRK [0x01fd3000, 0x01fd3fff] PGTABLE
[    0.000000] BRK [0x01fd4000, 0x01fd4fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x21fc00000-0x21fdfffff]
[    0.000000]  [mem 0x21fc00000-0x21fdfffff] page 2M
[    0.000000] BRK [0x01fd5000, 0x01fd5fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x21c000000-0x21fbfffff]
[    0.000000]  [mem 0x21c000000-0x21fbfffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x200000000-0x21bffffff]
[    0.000000]  [mem 0x200000000-0x21bffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x00100000-0xc53bffff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x3fffffff] page 2M
[    0.000000]  [mem 0x40000000-0xbfffffff] page 1G
[    0.000000]  [mem 0xc0000000-0xc51fffff] page 2M
[    0.000000]  [mem 0xc5200000-0xc53bffff] page 4k
[    0.000000] init_memory_mapping: [mem 0xc53c7000-0xc5811fff]
[    0.000000]  [mem 0xc53c7000-0xc53fffff] page 4k
[    0.000000]  [mem 0xc5400000-0xc57fffff] page 2M
[    0.000000]  [mem 0xc5800000-0xc5811fff] page 4k
[    0.000000] BRK [0x01fd6000, 0x01fd6fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0xc5c74000-0xd8700fff]
[    0.000000]  [mem 0xc5c74000-0xc5dfffff] page 4k
[    0.000000]  [mem 0xc5e00000-0xd85fffff] page 2M
[    0.000000]  [mem 0xd8600000-0xd8700fff] page 4k
[    0.000000] BRK [0x01fd7000, 0x01fd7fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0xd9fff000-0xd9ffffff]
[    0.000000]  [mem 0xd9fff000-0xd9ffffff] page 4k
[    0.000000] init_memory_mapping: [mem 0x100000000-0x1ffffffff]
[    0.000000]  [mem 0x100000000-0x1ffffffff] page 1G
[    0.000000] RAMDISK: [mem 0x34598000-0x362c3fff]
```

dmesg (part 2):
```

[    0.000000]   node   0: [mem 0xc53c7000-0xc5811fff]
[    0.000000]   node   0: [mem 0xc5c74000-0xd8700fff]
[    0.000000]   node   0: [mem 0xd9fff000-0xd9ffffff]
[    0.000000]   node   0: [mem 0x100000000-0x21fdfffff]
[    0.000000] On node 0 totalpages: 2064425
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 21 pages reserved
[    0.000000]   DMA zone: 3984 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 13771 pages used for memmap
[    0.000000]   DMA32 zone: 881305 pages, LIFO batch:31
[    0.000000]   Normal zone: 18424 pages used for memmap
[    0.000000]   Normal zone: 1179136 pages, LIFO batch:31
[    0.000000] Reserving Intel graphics stolen memory at 0xdc200000-0xde1fffff
[    0.000000] ACPI: PM-Timer IO Port: 0x1808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] smpboot: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: [mem 0x00091000-0x00091fff]
[    0.000000] PM: Registered nosave memory: [mem 0x00092000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xc53c0000-0xc53c6fff]
[    0.000000] PM: Registered nosave memory: [mem 0xc5812000-0xc5c73fff]
[    0.000000] PM: Registered nosave memory: [mem 0xd8701000-0xd8908fff]
[    0.000000] PM: Registered nosave memory: [mem 0xd8909000-0xd891efff]
[    0.000000] PM: Registered nosave memory: [mem 0xd891f000-0xd8e5afff]
[    0.000000] PM: Registered nosave memory: [mem 0xd8e5b000-0xd9ffefff]
[    0.000000] PM: Registered nosave memory: [mem 0xda000000-0xdbffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xdc000000-0xde1fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xde200000-0xf7ffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xf8000000-0xfbffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfc000000-0xfebfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfecfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed00000-0xfed03fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed04000-0xfed1bfff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed1c000-0xfed1ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed20000-0xfedfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xfeffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xff000000-0xffffffff]
[    0.000000] e820: [mem 0xde200000-0xf7ffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88021fa00000 s83328 r8192 d23168 u1048576
[    0.000000] pcpu-alloc: s83328 r8192 d23168 u1048576 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 2032145
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/@/boot/vmlinuz-3.16.0-31-generic root=UUID=a3d83995-4f83-46a9-a7da-24296268e25c ro rootflags=subvol=@ quiet splash nomdmonddf nomdmonisw vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] xsave: enabled xstate_bv 0x3, cntxt size 0x240
[    0.000000] AGP: Checking aperture...
[    0.000000] AGP: No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 8013884K/8257700K available (7743K kernel code, 1197K rwdata, 3612K rodata, 1360K init, 1308K bss, 243816K reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]  RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]  RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=2.
[    0.000000]  Offload RCU callbacks from all CPUs
[    0.000000]  Offload RCU callbacks from CPUs: 0-1.
[    0.000000] RCU: Adjusting geometry for rcu_fanout_leaf=16, nr_cpu_ids=2
[    0.000000] NR_IRQS:16640 nr_irqs:512 16
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 33554432 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.000000] tsc: Detected 2992.875 MHz processor
[    0.000024] Calibrating delay loop (skipped), value calculated using timer frequency.. 5985.75 BogoMIPS (lpj=11971500)
[    0.000026] pid_max: default: 32768 minimum: 301
[    0.000031] ACPI: Core revision 20140424
[    0.007917] ACPI: All ACPI Tables successfully acquired
[    0.010008] Security Framework initialized
[    0.010019] AppArmor: AppArmor initialized
[    0.010020] Yama: becoming mindful.
[    0.010415] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.011639] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.012170] Mount-cache hash table entries: 16384 (order: 5, 131072 bytes)
[    0.012177] Mountpoint-cache hash table entries: 16384 (order: 5, 131072 bytes)
[    0.012353] Initializing cgroup subsys memory
[    0.012370] Initializing cgroup subsys devices
[    0.012374] Initializing cgroup subsys freezer
[    0.012377] Initializing cgroup subsys net_cls
[    0.012379] Initializing cgroup subsys blkio
[    0.012382] Initializing cgroup subsys perf_event
[    0.012383] Initializing cgroup subsys net_prio
[    0.012388] Initializing cgroup subsys hugetlb
[    0.012405] CPU: Physical Processor ID: 0
[    0.012406] CPU: Processor Core ID: 0
[    0.012409] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.013193] mce: CPU supports 7 MCE banks
[    0.013202] CPU0: Thermal monitoring enabled (TM1)
[    0.013210] Last level iTLB entries: 4KB 1024, 2MB 1024, 4MB 1024
Last level dTLB entries: 4KB 1024, 2MB 1024, 4MB 1024, 1GB 4
tlb_flushall_shift: 6
[    0.013297] Freeing SMP alternatives memory: 32K (ffffffff81e81000 - ffffffff81e89000)
[    0.014134] ftrace: allocating 29316 entries in 115 pages
[    0.024172] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.063840] smpboot: CPU0: Intel(R) Pentium(R) CPU G3220 @ 3.00GHz (fam: 06, model: 3c, stepping: 03)
[    0.063846] TSC deadline timer enabled
[    0.063864] Performance Events: PEBS fmt2+, 16-deep LBR, Haswell events, full-width counters, Intel PMU driver.
[    0.063880] ... version:                3
[    0.063881] ... bit width:              48
[    0.063881] ... generic registers:      8
[    0.063882] ... value mask:             0000ffffffffffff
[    0.063882] ... max period:             0000ffffffffffff
[    0.063883] ... fixed-purpose events:   3
[    0.063884] ... event mask:             00000007000000ff
[    0.065146] x86: Booting SMP configuration:
[    0.065147] .... node  #0, CPUs:      #1
[    0.079076] x86: Booted up 1 node, 2 CPUs
[    0.079078] smpboot: Total of 2 processors activated (11971.50 BogoMIPS)
[    0.079136] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.080515] devtmpfs: initialized
[    0.082192] evm: security.selinux
[    0.082193] evm: security.SMACK64
[    0.082193] evm: security.SMACK64EXEC
[    0.082194] evm: security.SMACK64TRANSMUTE
[    0.082194] evm: security.SMACK64MMAP
[    0.082195] evm: security.ima
[    0.082196] evm: security.capability
[    0.082238] PM: Registering ACPI NVS region [mem 0xc53c0000-0xc53c6fff] (28672 bytes)
[    0.082239] PM: Registering ACPI NVS region [mem 0xd891f000-0xd8e5afff] (5488640 bytes)
[    0.082854] pinctrl core: initialized pinctrl subsystem
[    0.082904] regulator-dummy: no parameters
[    0.082933] RTC time: 20:49:23, date: 03/11/15
[    0.082968] NET: Registered protocol family 16
[    0.083082] cpuidle: using governor ladder
[    0.083083] cpuidle: using governor menu
[    0.083126] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.083127] ACPI: bus type PCI registered
[    0.083128] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.083176] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    0.083178] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
[    0.083238] PCI: Using configuration type 1 for base access
[    0.088680] ACPI: Added _OSI(Module Device)
[    0.088681] ACPI: Added _OSI(Processor Device)
[    0.088682] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.088683] ACPI: Added _OSI(Processor Aggregator Device)
[    0.091470] ACPI: Executed 1 blocks of module-level executable AML code
[    0.093124] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.096481] ACPI: Dynamic OEM Table Load:
[    0.096485] ACPI: SSDT 0xFFFF880214367800 0003D3 (v01 PmRef  Cpu0Cst  00003001 INTL 20051117)
[    0.100575] ACPI: Dynamic OEM Table Load:
[    0.100579] ACPI: SSDT 0xFFFF8802143E8800 0005AA (v01 PmRef  ApIst    00003000 INTL 20051117)
[    0.104495] ACPI: Dynamic OEM Table Load:
[    0.104498] ACPI: SSDT 0xFFFF8802143E4C00 000119 (v01 PmRef  ApCst    00003000 INTL 20051117)
[    0.108750] ACPI: Interpreter enabled
[    0.108755] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20140424/hwxface-580)
[    0.108759] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20140424/hwxface-580)
[    0.108772] ACPI: (supports S0 S3 S4 S5)
[    0.108773] ACPI: Using IOAPIC for interrupt routing
[    0.108791] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.114502] ACPI: Power Resource [FN00] (off)
[    0.114553] ACPI: Power Resource [FN01] (off)
[    0.114603] ACPI: Power Resource [FN02] (off)
[    0.114651] ACPI: Power Resource [FN03] (off)
[    0.114699] ACPI: Power Resource [FN04] (off)
[    0.115282] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3e])
[    0.115286] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.115439] acpi PNP0A08:00: _OSC: platform does not support [PCIeHotplug PME]
[    0.115522] acpi PNP0A08:00: _OSC: OS now controls [AER PCIeCapability]
[    0.115932] PCI host bridge to bus 0000:00
[    0.115934] pci_bus 0000:00: root bus resource [bus 00-3e]
[    0.115935] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.115936] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.115937] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.115939] pci_bus 0000:00: root bus resource [mem 0x000dc000-0x000dffff]
[    0.115939] pci_bus 0000:00: root bus resource [mem 0x000e0000-0x000e3fff]
[    0.115940] pci_bus 0000:00: root bus resource [mem 0x000e4000-0x000e7fff]
[    0.115942] pci_bus 0000:00: root bus resource [mem 0xde200000-0xfeafffff]
```

---

### Post by erictherev on 2015-03-12
dmesg (part 3):
```
[    0.000000] ACPI: Early table checksum verification disabled
[    0.000000] ACPI: RSDP 0x00000000000F0490 000024 (v02 ALASKA)
[    0.000000] ACPI: XSDT 0x00000000D890D080 00007C (v01 ALASKA A M I    01072009 AMI  00010013)
[    0.000000] ACPI: FACP 0x00000000D891A048 00010C (v05 ALASKA A M I    01072009 AMI  00010013)
[    0.000000] ACPI: DSDT 0x00000000D890D198 00CEB0 (v02 ALASKA A M I    00000024 INTL 20091112)
[    0.000000] ACPI: FACS 0x00000000D8E59080 000040
[    0.000000] ACPI: APIC 0x00000000D891A158 000062 (v03 ALASKA A M I    01072009 AMI  00010013)
[    0.000000] ACPI: FPDT 0x00000000D891A1C0 000044 (v01 ALASKA A M I    01072009 AMI  00010013)
[    0.000000] ACPI: SSDT 0x00000000D891A208 000539 (v01 PmRef  Cpu0Ist  00003000 INTL 20051117)
[    0.000000] ACPI: SSDT 0x00000000D891A748 000AD8 (v01 PmRef  CpuPm    00003000 INTL 20051117)
[    0.000000] ACPI: MCFG 0x00000000D891B220 00003C (v01 ALASKA A M I    01072009 MSFT 00000097)
[    0.000000] ACPI: HPET 0x00000000D891B260 000038 (v01 ALASKA A M I    01072009 AMI. 00000005)
[    0.000000] ACPI: SSDT 0x00000000D891B298 00036D (v01 SataRe SataTabl 00001000 INTL 20091112)
[    0.000000] ACPI: SSDT 0x00000000D891B608 003482 (v01 SaSsdt SaSsdt   00003000 INTL 20091112)
[    0.000000] ACPI: BGRT 0x00000000D891EB90 000038 (v00 ALASKA A M I    01072009 AMI  00010013)
[    0.000000] ACPI: ASF! 0x00000000D891EAE8 0000A5 (v32 INTEL   HCG     00000001 TFSM 000F4240)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000021fdfffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x21fdfffff]
[    0.000000]   NODE_DATA [mem 0x21fdf7000-0x21fdfbfff]
[    0.000000]  [ffffea0000000000-ffffea00087fffff] PMD -> [ffff880217400000-ffff88021f3fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x21fdfffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x00090fff]
[    0.000000]   node   0: [mem 0x00100000-0xc53bffff]
[    0.115947] pci 0000:00:00.0: [8086:0c00] type 00 class 0x060000
[    0.116011] pci 0000:00:01.0: [8086:0c01] type 01 class 0x060400
[    0.116039] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.116073] pci 0000:00:01.0: System wakeup disabled by ACPI
[    0.116103] pci 0000:00:02.0: [8086:0402] type 00 class 0x030000
[    0.116112] pci 0000:00:02.0: reg 0x10: [mem 0xf7800000-0xf7bfffff 64bit]
[    0.116117] pci 0000:00:02.0: reg 0x18: [mem 0xe0000000-0xefffffff 64bit pref]
[    0.116120] pci 0000:00:02.0: reg 0x20: [io  0xf000-0xf03f]
[    0.116177] pci 0000:00:03.0: [8086:0c0c] type 00 class 0x040300
[    0.116183] pci 0000:00:03.0: reg 0x10: [mem 0xf7d34000-0xf7d37fff 64bit]
[    0.116263] pci 0000:00:14.0: [8086:8c31] type 00 class 0x0c0330
[    0.116280] pci 0000:00:14.0: reg 0x10: [mem 0xf7d20000-0xf7d2ffff 64bit]
[    0.116332] pci 0000:00:14.0: PME# supported from D3hot D3cold
[    0.116359] pci 0000:00:14.0: System wakeup disabled by ACPI
[    0.116387] pci 0000:00:16.0: [8086:8c3a] type 00 class 0x078000
[    0.116404] pci 0000:00:16.0: reg 0x10: [mem 0xf7d40000-0xf7d4000f 64bit]
[    0.116463] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.116514] pci 0000:00:16.3: [8086:8c3d] type 00 class 0x070002
[    0.116528] pci 0000:00:16.3: reg 0x10: [io  0xf0e0-0xf0e7]
[    0.116535] pci 0000:00:16.3: reg 0x14: [mem 0xf7d3e000-0xf7d3efff]
[    0.116641] pci 0000:00:19.0: [8086:153a] type 00 class 0x020000
[    0.116655] pci 0000:00:19.0: reg 0x10: [mem 0xf7d00000-0xf7d1ffff]
[    0.116662] pci 0000:00:19.0: reg 0x14: [mem 0xf7d3d000-0xf7d3dfff]
[    0.116669] pci 0000:00:19.0: reg 0x18: [io  0xf080-0xf09f]
[    0.116722] pci 0000:00:19.0: PME# supported from D0 D3hot D3cold
[    0.116750] pci 0000:00:19.0: System wakeup disabled by ACPI
[    0.116780] pci 0000:00:1a.0: [8086:8c2d] type 00 class 0x0c0320
[    0.116798] pci 0000:00:1a.0: reg 0x10: [mem 0xf7d3c000-0xf7d3c3ff]
[    0.116877] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.116913] pci 0000:00:1a.0: System wakeup disabled by ACPI
[    0.116942] pci 0000:00:1b.0: [8086:8c20] type 00 class 0x040300
[    0.116956] pci 0000:00:1b.0: reg 0x10: [mem 0xf7d30000-0xf7d33fff 64bit]
[    0.117017] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.117045] pci 0000:00:1b.0: System wakeup disabled by ACPI
[    0.117070] pci 0000:00:1c.0: [8086:8c10] type 01 class 0x060400
[    0.117130] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.117160] pci 0000:00:1c.0: System wakeup disabled by ACPI
[    0.117187] pci 0000:00:1c.3: [8086:244e] type 01 class 0x060401
[    0.117247] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.117276] pci 0000:00:1c.3: System wakeup disabled by ACPI
[    0.117309] pci 0000:00:1d.0: [8086:8c26] type 00 class 0x0c0320
[    0.117327] pci 0000:00:1d.0: reg 0x10: [mem 0xf7d3b000-0xf7d3b3ff]
[    0.117406] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.117442] pci 0000:00:1d.0: System wakeup disabled by ACPI
[    0.117471] pci 0000:00:1f.0: [8086:8c4e] type 00 class 0x060100
[    0.117610] pci 0000:00:1f.2: [8086:2822] type 00 class 0x010400
[    0.117623] pci 0000:00:1f.2: reg 0x10: [io  0xf0d0-0xf0d7]
[    0.117629] pci 0000:00:1f.2: reg 0x14: [io  0xf0c0-0xf0c3]
[    0.117635] pci 0000:00:1f.2: reg 0x18: [io  0xf0b0-0xf0b7]
[    0.117641] pci 0000:00:1f.2: reg 0x1c: [io  0xf0a0-0xf0a3]
[    0.117648] pci 0000:00:1f.2: reg 0x20: [io  0xf060-0xf07f]
[    0.117654] pci 0000:00:1f.2: reg 0x24: [mem 0xf7d3a000-0xf7d3a7ff]
[    0.117686] pci 0000:00:1f.2: PME# supported from D3hot
[    0.117733] pci 0000:00:1f.3: [8086:8c22] type 00 class 0x0c0500
[    0.117745] pci 0000:00:1f.3: reg 0x10: [mem 0xf7d39000-0xf7d390ff 64bit]
[    0.117763] pci 0000:00:1f.3: reg 0x20: [io  0xf040-0xf05f]
[    0.117843] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.117900] acpiphp: Slot [1] registered
[    0.117903] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.117964] pci 0000:03:00.0: [1b21:1080] type 01 class 0x060401
[    0.118060] pci 0000:03:00.0: System wakeup disabled by ACPI
[    0.118082] pci 0000:00:1c.3: PCI bridge to [bus 03-04] (subtractive decode)
[    0.118085] pci 0000:00:1c.3:   bridge window [io  0xe000-0xefff]
[    0.118088] pci 0000:00:1c.3:   bridge window [mem 0xf7c00000-0xf7cfffff]
[    0.118092] pci 0000:00:1c.3:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.118093] pci 0000:00:1c.3:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.118094] pci 0000:00:1c.3:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.118096] pci 0000:00:1c.3:   bridge window [mem 0x000dc000-0x000dffff] (subtractive decode)
[    0.118097] pci 0000:00:1c.3:   bridge window [mem 0x000e0000-0x000e3fff] (subtractive decode)
[    0.118098] pci 0000:00:1c.3:   bridge window [mem 0x000e4000-0x000e7fff] (subtractive decode)
[    0.118099] pci 0000:00:1c.3:   bridge window [mem 0xde200000-0xfeafffff] (subtractive decode)
[    0.118149] pci 0000:04:00.0: [10ec:8169] type 00 class 0x020000
[    0.118180] pci 0000:04:00.0: reg 0x10: [io  0xe100-0xe1ff]
[    0.118196] pci 0000:04:00.0: reg 0x14: [mem 0xf7c41000-0xf7c410ff]
[    0.118278] pci 0000:04:00.0: reg 0x30: [mem 0xf7c20000-0xf7c3ffff pref]
[    0.118327] pci 0000:04:00.0: supports D1 D2
[    0.118328] pci 0000:04:00.0: PME# supported from D1 D2 D3hot D3cold
[    0.118377] pci 0000:04:01.0: [10ec:8169] type 00 class 0x020000
[    0.118408] pci 0000:04:01.0: reg 0x10: [io  0xe000-0xe0ff]
[    0.118424] pci 0000:04:01.0: reg 0x14: [mem 0xf7c40000-0xf7c400ff]
[    0.118505] pci 0000:04:01.0: reg 0x30: [mem 0xf7c00000-0xf7c1ffff pref]
[    0.118555] pci 0000:04:01.0: supports D1 D2
[    0.118556] pci 0000:04:01.0: PME# supported from D1 D2 D3hot D3cold
[    0.118657] pci 0000:03:00.0: PCI bridge to [bus 04] (subtractive decode)
[    0.118665] pci 0000:03:00.0:   bridge window [io  0xe000-0xefff]
[    0.118669] pci 0000:03:00.0:   bridge window [mem 0xf7c00000-0xf7cfffff]
[    0.118676] pci 0000:03:00.0:   bridge window [io  0xe000-0xefff] (subtractive decode)
[    0.118677] pci 0000:03:00.0:   bridge window [mem 0xf7c00000-0xf7cfffff] (subtractive decode)
[    0.118678] pci 0000:03:00.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.118679] pci 0000:03:00.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.118681] pci 0000:03:00.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.118682] pci 0000:03:00.0:   bridge window [mem 0x000dc000-0x000dffff] (subtractive decode)
[    0.118683] pci 0000:03:00.0:   bridge window [mem 0x000e0000-0x000e3fff] (subtractive decode)
[    0.118684] pci 0000:03:00.0:   bridge window [mem 0x000e4000-0x000e7fff] (subtractive decode)
[    0.118685] pci 0000:03:00.0:   bridge window [mem 0xde200000-0xfeafffff] (subtractive decode)
[    0.118704] acpi PNP0A08:00: Disabling ASPM (FADT indicates it is unsupported)
[    0.119265] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.119296] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.119327] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.119357] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11 12 14 *15)
[    0.119386] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[    0.119416] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.119445] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 *14 15)
[    0.119474] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 *6 7 10 11 12 14 15)
[    0.119718] ACPI: Enabled 5 GPEs in block 00 to 3F
[    0.119787] vgaarb: setting as boot device: PCI:0000:00:02.0
[    0.119789] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.119791] vgaarb: loaded
[    0.119792] vgaarb: bridge control possible 0000:00:02.0
[    0.119956] SCSI subsystem initialized
[    0.119984] libata version 3.00 loaded.
[    0.120002] ACPI: bus type USB registered
[    0.120014] usbcore: registered new interface driver usbfs
[    0.120020] usbcore: registered new interface driver hub
[    0.120038] usbcore: registered new device driver usb
[    0.120124] PCI: Using ACPI for IRQ routing
[    0.121378] PCI: pci_cache_line_size set to 64 bytes
[    0.121427] e820: reserve RAM buffer [mem 0x00091c00-0x0009ffff]
[    0.121428] e820: reserve RAM buffer [mem 0xc53c0000-0xc7ffffff]
[    0.121429] e820: reserve RAM buffer [mem 0xc5812000-0xc7ffffff]
[    0.121430] e820: reserve RAM buffer [mem 0xd8701000-0xdbffffff]
[    0.121431] e820: reserve RAM buffer [mem 0xda000000-0xdbffffff]
[    0.121432] e820: reserve RAM buffer [mem 0x21fe00000-0x21fffffff]
[    0.121515] NetLabel: Initializing
[    0.121515] NetLabel:  domain hash size = 128
[    0.121516] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.121524] NetLabel:  unlabeled traffic allowed by default
[    0.121582] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.121586] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.123613] Switched to clocksource hpet
[    0.127782] AppArmor: AppArmor Filesystem Enabled
[    0.127806] pnp: PnP ACPI init
[    0.127816] ACPI: bus type PNP registered
[    0.127882] system 00:00: [mem 0xfed40000-0xfed44fff] has been reserved
[    0.127885] system 00:00: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.128006] system 00:01: [io  0x0680-0x069f] has been reserved
[    0.128007] system 00:01: [io  0xffff] has been reserved
[    0.128009] system 00:01: [io  0xffff] has been reserved
[    0.128010] system 00:01: [io  0xffff] has been reserved
[    0.128011] system 00:01: [io  0x1c00-0x1cfe] has been reserved
[    0.128012] system 00:01: [io  0x1d00-0x1dfe] has been reserved
[    0.128014] system 00:01: [io  0x1e00-0x1efe] has been reserved
[    0.128015] system 00:01: [io  0x1f00-0x1ffe] has been reserved
[    0.128016] system 00:01: [io  0x1800-0x18fe] could not be reserved
[    0.128017] system 00:01: [io  0x164e-0x164f] has been reserved
[    0.128019] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.128042] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.128075] system 00:03: [io  0x1854-0x1857] has been reserved
[    0.128076] system 00:03: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    0.128131] system 00:04: [io  0x0290-0x029f] has been reserved
[    0.128133] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.128304] pnp 00:05: [dma 0 disabled]
[    0.128367] pnp 00:05: Plug and Play ACPI device, IDs PNP0400 (active)
[    0.128401] system 00:06: [io  0x04d0-0x04d1] has been reserved
[    0.128402] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.128522] pnp 00:07: [dma 0 disabled]
[    0.128554] pnp 00:07: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.128674] pnp 00:08: [dma 0 disabled]
[    0.128702] pnp 00:08: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.128986] system 00:09: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.128988] system 00:09: [mem 0xfed10000-0xfed17fff] has been reserved
[    0.128989] system 00:09: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.128990] system 00:09: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.128991] system 00:09: [mem 0xf8000000-0xfbffffff] has been reserved
[    0.128993] system 00:09: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.128994] system 00:09: [mem 0xfed90000-0xfed93fff] has been reserved
[    0.128995] system 00:09: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.128996] system 00:09: [mem 0xff000000-0xffffffff] has been reserved
[    0.128998] system 00:09: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.128999] system 00:09: [mem 0xf7fef000-0xf7feffff] has been reserved
[    0.129000] system 00:09: [mem 0xf7ff0000-0xf7ff0fff] has been reserved
[    0.129002] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.129176] pnp: PnP ACPI: found 10 devices
[    0.129176] ACPI: bus type PNP unregistered
[    0.134992] pci 0000:00:1c.0: bridge window [io  0x1000-0x0fff] to [bus 02] add_size 1000
[    0.134995] pci 0000:00:1c.0: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 02] add_size 200000
[    0.134996] pci 0000:00:1c.0: bridge window [mem 0x00100000-0x000fffff] to [bus 02] add_size 200000
[    0.135014] pci 0000:00:1c.0: res[14]=[mem 0x00100000-0x000fffff] get_res_add_size add_size 200000
[    0.135016] pci 0000:00:1c.0: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.135017] pci 0000:00:1c.0: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
[    0.135020] pci 0000:00:1c.0: BAR 14: assigned [mem 0xde200000-0xde3fffff]
[    0.135025] pci 0000:00:1c.0: BAR 15: assigned [mem 0xde400000-0xde5fffff 64bit pref]
[    0.135026] pci 0000:00:1c.0: BAR 13: assigned [io  0x2000-0x2fff]
[    0.135028] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.135033] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.135035] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.135038] pci 0000:00:1c.0:   bridge window [mem 0xde200000-0xde3fffff]
[    0.135041] pci 0000:00:1c.0:   bridge window [mem 0xde400000-0xde5fffff 64bit pref]
[    0.135046] pci 0000:03:00.0: PCI bridge to [bus 04]
[    0.135049] pci 0000:03:00.0:   bridge window [io  0xe000-0xefff]
[    0.135055] pci 0000:03:00.0:   bridge window [mem 0xf7c00000-0xf7cfffff]
[    0.135065] pci 0000:00:1c.3: PCI bridge to [bus 03-04]
[    0.135067] pci 0000:00:1c.3:   bridge window [io  0xe000-0xefff]
[    0.135071] pci 0000:00:1c.3:   bridge window [mem 0xf7c00000-0xf7cfffff]
[    0.135077] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.135078] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.135080] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.135081] pci_bus 0000:00: resource 7 [mem 0x000dc000-0x000dffff]
[    0.135082] pci_bus 0000:00: resource 8 [mem 0x000e0000-0x000e3fff]
[    0.135083] pci_bus 0000:00: resource 9 [mem 0x000e4000-0x000e7fff]
[    0.135084] pci_bus 0000:00: resource 10 [mem 0xde200000-0xfeafffff]
[    0.135085] pci_bus 0000:02: resource 0 [io  0x2000-0x2fff]
[    0.135086] pci_bus 0000:02: resource 1 [mem 0xde200000-0xde3fffff]
[    0.135087] pci_bus 0000:02: resource 2 [mem 0xde400000-0xde5fffff 64bit pref]
[    0.135088] pci_bus 0000:03: resource 0 [io  0xe000-0xefff]
[    0.135090] pci_bus 0000:03: resource 1 [mem 0xf7c00000-0xf7cfffff]
[    0.135091] pci_bus 0000:03: resource 4 [io  0x0000-0x0cf7]
[    0.135092] pci_bus 0000:03: resource 5 [io  0x0d00-0xffff]
[    0.135093] pci_bus 0000:03: resource 6 [mem 0x000a0000-0x000bffff]
[    0.135094] pci_bus 0000:03: resource 7 [mem 0x000dc000-0x000dffff]
[    0.135095] pci_bus 0000:03: resource 8 [mem 0x000e0000-0x000e3fff]
[    0.135096] pci_bus 0000:03: resource 9 [mem 0x000e4000-0x000e7fff]
[    0.135097] pci_bus 0000:03: resource 10 [mem 0xde200000-0xfeafffff]
[    0.135098] pci_bus 0000:04: resource 0 [io  0xe000-0xefff]
[    0.135099] pci_bus 0000:04: resource 1 [mem 0xf7c00000-0xf7cfffff]
[    0.135100] pci_bus 0000:04: resource 4 [io  0xe000-0xefff]
[    0.135101] pci_bus 0000:04: resource 5 [mem 0xf7c00000-0xf7cfffff]
[    0.135102] pci_bus 0000:04: resource 6 [io  0x0000-0x0cf7]
[    0.135103] pci_bus 0000:04: resource 7 [io  0x0d00-0xffff]
[    0.135104] pci_bus 0000:04: resource 8 [mem 0x000a0000-0x000bffff]
[    0.135105] pci_bus 0000:04: resource 9 [mem 0x000dc000-0x000dffff]
[    0.135106] pci_bus 0000:04: resource 10 [mem 0x000e0000-0x000e3fff]
[    0.135107] pci_bus 0000:04: resource 11 [mem 0x000e4000-0x000e7fff]
[    0.135108] pci_bus 0000:04: resource 12 [mem 0xde200000-0xfeafffff]
```

dmesg (part 4):
```
[    0.135126] NET: Registered protocol family 2
[    0.135260] TCP established hash table entries: 65536 (order: 7, 524288 bytes)
[    0.135365] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.135488] TCP: Hash tables configured (established 65536 bind 65536)
[    0.135502] TCP: reno registered
[    0.135510] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    0.135533] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    0.135575] NET: Registered protocol family 1
[    0.135587] pci 0000:00:02.0: Video device with shadowed ROM
[    0.171667] PCI: CLS 64 bytes, default 64
[    0.171705] Trying to unpack rootfs image as initramfs...
[    0.519778] Freeing initrd memory: 29872K (ffff880034598000 - ffff8800362c4000)
[    0.519792] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.519794] software IO TLB [mem 0xd4701000-0xd8701000] (64MB) mapped at [ffff8800d4701000-ffff8800d8700fff]
[    0.519948] RAPL PMU detected, hw unit 2^-14 Joules, API unit is 2^-32 Joules, 4 fixed counters 655360 ms ovfl timer
[    0.519980] microcode: CPU0 sig=0x306c3, pf=0x2, revision=0x9
[    0.519984] microcode: CPU1 sig=0x306c3, pf=0x2, revision=0x9
[    0.520018] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.520040] Scanning for low memory corruption every 60 seconds
[    0.520253] futex hash table entries: 512 (order: 3, 32768 bytes)
[    0.520264] Initialise system trusted keyring
[    0.520284] audit: initializing netlink subsys (disabled)
[    0.520296] audit: type=2000 audit(1426106963.520:1): initialized
[    0.520549] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.521503] zpool: loaded
[    0.521505] zbud: loaded
[    0.521624] VFS: Disk quotas dquot_6.5.2
[    0.521651] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.521970] fuse init (API version 7.23)
[    0.522031] msgmni has been set to 15710
[    0.522071] Key type big_key registered
[    0.522349] Key type asymmetric registered
[    0.522351] Asymmetric key parser 'x509' registered
[    0.522377] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.522403] io scheduler noop registered
[    0.522405] io scheduler deadline registered (default)
[    0.522440] io scheduler cfq registered
[    0.522583] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    0.522710] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.522721] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.522757] vesafb: mode is 1280x1024x32, linelength=5120, pages=0
[    0.522757] vesafb: scrolling: redraw
[    0.522759] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    0.522770] vesafb: framebuffer at 0xe0000000, mapped to 0xffffc90004e80000, using 5120k, total 5120k
[    0.522832] Console: switching to colour frame buffer device 160x64
[    0.522844] fb0: VESA VGA frame buffer device
[    0.522861] intel_idle: MWAIT substates: 0x2120
[    0.522862] intel_idle: v0.4 model 0x3C
[    0.522862] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.522983] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.522986] ACPI: Power Button [PWRB]
[    0.523012] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.523014] ACPI: Power Button [PWRF]
[    0.523058] ACPI: Fan [FAN0] (off)
[    0.523078] ACPI: Fan [FAN1] (off)
[    0.523095] ACPI: Fan [FAN2] (off)
[    0.523112] ACPI: Fan [FAN3] (off)
[    0.523128] ACPI: Fan [FAN4] (off)
[    0.523406] thermal LNXTHERM:00: registered as thermal_zone0
[    0.523407] ACPI: Thermal Zone [TZ00] (28 C)
[    0.523544] thermal LNXTHERM:01: registered as thermal_zone1
[    0.523545] ACPI: Thermal Zone [TZ01] (30 C)
[    0.523595] GHES: HEST is not enabled!
[    0.523672] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.544035] 00:07: ttyS0 at I/O 0x3f8 (irq = 4, base_baud = 115200) is a 16550A
[    0.564417] 00:08: ttyS1 at I/O 0x2f8 (irq = 3, base_baud = 115200) is a 16550A
[    0.585538] 0000:00:16.3: ttyS4 at I/O 0xf0e0 (irq = 19, base_baud = 115200) is a 16550A
[    0.585760] Linux agpgart interface v0.103
[    0.586613] brd: module loaded
[    0.586989] loop: module loaded
[    0.587124] libphy: Fixed MDIO Bus: probed
[    0.587127] tun: Universal TUN/TAP device driver, 1.6
[    0.587128] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.587159] PPP generic driver version 2.4.2
[    0.587188] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.587193] ehci-pci: EHCI PCI platform driver
[    0.587264] ehci-pci 0000:00:1a.0: EHCI Host Controller
[    0.587268] ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    0.587278] ehci-pci 0000:00:1a.0: debug port 2
[    0.591175] ehci-pci 0000:00:1a.0: cache line size of 64 is not supported
[    0.591186] ehci-pci 0000:00:1a.0: irq 16, io mem 0xf7d3c000
[    0.599448] ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    0.599482] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.599483] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.599484] usb usb1: Product: EHCI Host Controller
[    0.599486] usb usb1: Manufacturer: Linux 3.16.0-31-generic ehci_hcd
[    0.599487] usb usb1: SerialNumber: 0000:00:1a.0
[    0.599578] hub 1-0:1.0: USB hub found
[    0.599581] hub 1-0:1.0: 3 ports detected
[    0.599719] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    0.599723] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.599732] ehci-pci 0000:00:1d.0: debug port 2
[    0.603622] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[    0.603631] ehci-pci 0000:00:1d.0: irq 23, io mem 0xf7d3b000
[    0.615475] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    0.615510] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    0.615511] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.615512] usb usb2: Product: EHCI Host Controller
[    0.615513] usb usb2: Manufacturer: Linux 3.16.0-31-generic ehci_hcd
[    0.615514] usb usb2: SerialNumber: 0000:00:1d.0
[    0.615636] hub 2-0:1.0: USB hub found
[    0.615641] hub 2-0:1.0: 3 ports detected
[    0.615731] ehci-platform: EHCI generic platform driver
[    0.615738] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.615743] ohci-pci: OHCI PCI platform driver
[    0.615751] ohci-platform: OHCI generic platform driver
[    0.615757] uhci_hcd: USB Universal Host Controller Interface driver
[    0.615834] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.615837] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 3
[    0.615910] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[    0.615923] xhci_hcd 0000:00:14.0: irq 41 for MSI/MSI-X
[    0.615964] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[    0.615965] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.615966] usb usb3: Product: xHCI Host Controller
[    0.615967] usb usb3: Manufacturer: Linux 3.16.0-31-generic xhci_hcd
[    0.615968] usb usb3: SerialNumber: 0000:00:14.0
[    0.616114] hub 3-0:1.0: USB hub found
[    0.616130] hub 3-0:1.0: 15 ports detected
[    0.618630] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.618632] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 4
[    0.618660] usb usb4: New USB device found, idVendor=1d6b, idProduct=0003
[    0.618662] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.618663] usb usb4: Product: xHCI Host Controller
[    0.618664] usb usb4: Manufacturer: Linux 3.16.0-31-generic xhci_hcd
[    0.618665] usb usb4: SerialNumber: 0000:00:14.0
[    0.618807] hub 4-0:1.0: USB hub found
[    0.618818] hub 4-0:1.0: 6 ports detected
[    0.619605] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    0.621905] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.621909] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.622083] mousedev: PS/2 mouse device common for all mice
[    0.622274] rtc_cmos 00:02: RTC can wake from S4
[    0.622389] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    0.622411] rtc_cmos 00:02: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    0.622454] device-mapper: uevent: version 1.0.3
[    0.622500] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: dm-devel@redhat.com
[    0.622510] Intel P-state driver initializing.
[    0.622517] Intel pstate controlling: cpu 0
[    0.622543] Intel pstate controlling: cpu 1
[    0.622559] Consider also installing thermald for improved thermal control.
[    0.622562] ledtrig-cpu: registered to indicate activity on CPUs
[    0.622628] TCP: cubic registered
[    0.622699] NET: Registered protocol family 10
[    0.622850] NET: Registered protocol family 17
[    0.622861] Key type dns_resolver registered
[    0.623065] Loading compiled-in X.509 certificates
[    0.623693] Loaded X.509 cert 'Magrathea: Glacier signing key: a112c18a448a560047ef1f4db74d497f61a45099'
[    0.623707] registered taskstats version 1
[    0.624988] Key type trusted registered
[    0.626953] Key type encrypted registered
[    0.626959] AppArmor: AppArmor sha1 policy hashing enabled
[    0.626962] ima: No TPM chip found, activating TPM-bypass!
[    0.626974] evm: HMAC attrs: 0x1
[    0.627283]   Magic number: 7:716:851
[    0.627370] rtc_cmos 00:02: setting system clock to 2015-03-11 20:49:23 UTC (1426106963)
[    0.627408] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.627409] EDD information not available.
[    0.627470] PM: Hibernation image not present or could not be loaded.
[    0.628071] Freeing unused kernel memory: 1360K (ffffffff81d2d000 - ffffffff81e81000)
[    0.628072] Write protecting the kernel read-only data: 12288k
[    0.628835] Freeing unused kernel memory: 436K (ffff880001793000 - ffff880001800000)
[    0.629576] Freeing unused kernel memory: 484K (ffff880001b87000 - ffff880001c00000)
[    0.637107] systemd-udevd[102]: starting version 208
[    0.637383] random: systemd-udevd urandom read with 1 bits of entropy available
[    0.652137] pps_core: LinuxPPS API ver. 1 registered
[    0.652139] pps_core: Software ver. 5.3.6 - Copyright 2005-2007 Rodolfo Giometti <giometti@linux.it>
[    0.654622] PTP clock support registered
[    0.655561] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    0.655725] r8169 0000:04:00.0 (unregistered net_device): not PCI Express
[    0.655959] r8169 0000:04:00.0 eth0: RTL8169sb/8110sb at 0xffffc90000c70000, 00:06:4f:4a:79:a5, XID 10000000 IRQ 19
[    0.655960] r8169 0000:04:00.0 eth0: jumbo features [frames: 7152 bytes, tx checksumming: ok]
[    0.655976] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    0.656028] r8169 0000:04:01.0 (unregistered net_device): not PCI Express
[    0.656241] r8169 0000:04:01.0 eth1: RTL8169sb/8110sb at 0xffffc90004e5e000, 00:06:4f:4a:78:bb, XID 10000000 IRQ 16
[    0.656243] r8169 0000:04:01.0 eth1: jumbo features [frames: 7152 bytes, tx checksumming: ok]
[    0.657434] [drm] Initialized drm 1.1.0 20060810
[    0.659228] ahci 0000:00:1f.2: version 3.0
[    0.659319] ahci 0000:00:1f.2: irq 42 for MSI/MSI-X
[    0.659362] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x3f impl RAID mode
[    0.659364] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part ems apst
[    0.661436] e1000e: Intel(R) PRO/1000 Network Driver - 2.3.2-k
[    0.661438] e1000e: Copyright(c) 1999 - 2014 Intel Corporation.
[    0.662024] wmi: Mapper loaded
[    0.699367] scsi0 : ahci
[    0.703708] scsi1 : ahci
[    0.703784] scsi2 : ahci
[    0.703843] scsi3 : ahci
[    0.703900] scsi4 : ahci
[    0.703955] scsi5 : ahci
[    0.703985] ata1: SATA max UDMA/133 abar m2048@0xf7d3a000 port 0xf7d3a100 irq 42
[    0.703987] ata2: SATA max UDMA/133 abar m2048@0xf7d3a000 port 0xf7d3a180 irq 42
[    0.703988] ata3: SATA max UDMA/133 abar m2048@0xf7d3a000 port 0xf7d3a200 irq 42
[    0.703990] ata4: SATA max UDMA/133 abar m2048@0xf7d3a000 port 0xf7d3a280 irq 42
[    0.703991] ata5: SATA max UDMA/133 abar m2048@0xf7d3a000 port 0xf7d3a300 irq 42
[    0.703993] ata6: SATA max UDMA/133 abar m2048@0xf7d3a000 port 0xf7d3a380 irq 42
[    0.704140] e1000e 0000:00:19.0: Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
[    0.704153] e1000e 0000:00:19.0: irq 43 for MSI/MSI-X
[    0.877625] e1000e 0000:00:19.0 eth2: registered PHC clock
[    0.877628] e1000e 0000:00:19.0 eth2: (PCI Express:2.5GT/s:Width x1) e0:3f:49:84:60:93
[    0.877629] e1000e 0000:00:19.0 eth2: Intel(R) PRO/1000 Network Connection
[    0.877667] e1000e 0000:00:19.0 eth2: MAC: 11, PHY: 12, PBA No: FFFFFF-0FF
[    0.878020] [drm] Memory usable by graphics device = 2048M
[    0.878023] checking generic (e0000000 500000) vs hw (e0000000 10000000)
[    0.878024] fb: switching to inteldrmfb from VESA VGA
[    0.878038] Console: switching to colour dummy device 80x25
[    0.878106] [drm] Replacing VGA console driver
[    0.899408] i915 0000:00:02.0: irq 44 for MSI/MSI-X
[    0.899415] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    0.899416] [drm] Driver supports precise vblank timestamp query.
[    0.899432] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    0.911404] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    0.937437] fbcon: inteldrmfb (fb0) is primary device
[    0.937456] Console: switching to colour frame buffer device 160x64
[    0.937469] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[    0.937470] i915 0000:00:02.0: registered panic notifier
[    0.948347] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    0.948653] acpi device:60: registered as cooling_device7
[    0.948777] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input4
[    0.948837] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    1.023337] ata6: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    1.023353] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.024025] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20140424/psargs-359)
[    1.024028] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT5._GTF] (Node ffff8802170553e8), AE_NOT_FOUND (20140424/psparse-536)
[    1.024526] ata6.00: ATA-9: ST2000DM001-1CH164, CC29, max UDMA/133
[    1.024528] ata6.00: 3907029168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.025045] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20140424/psargs-359)
[    1.025049] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT5._GTF] (Node ffff8802170553e8), AE_NOT_FOUND (20140424/psparse-536)
[    1.025406] ata6.00: configured for UDMA/133
[    1.025698] ata2.00: ATAPI: msi     DVD-RW DH24AS, LM21, max UDMA/100
[    1.026546] ata2.00: configured for UDMA/100
[    1.027326] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    1.027340] ata4: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    1.027362] ata5: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    1.027373] ata3: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    1.027834] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20140424/psargs-359)
[    1.027837] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT2._GTF] (Node ffff880217055280), AE_NOT_FOUND (20140424/psparse-536)
[    1.028114] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20140424/psargs-359)
[    1.028118] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT4._GTF] (Node ffff880217055370), AE_NOT_FOUND (20140424/psparse-536)
[    1.028272] ata3.00: ATA-9: ST2000DM001-1ER164, CC25, max UDMA/133
[    1.028274] ata3.00: 3907029168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.028543] ata4.00: ATA-9: ST2000DM001-1CH164, CC29, max UDMA/133
[    1.028544] ata4.00: 3907029168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.028570] ata5.00: ATA-9: ST2000DM001-1CH164, CC29, max UDMA/133
[    1.028572] ata5.00: 3907029168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.028636] ata1.00: ATA-8: ST500DM002-1BD142, KC48, max UDMA/133
[    1.028638] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.028787] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20140424/psargs-359)
[    1.028790] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT2._GTF] (Node ffff880217055280), AE_NOT_FOUND (20140424/psparse-536)
[    1.029068] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20140424/psargs-359)
[    1.029072] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT4._GTF] (Node ffff880217055370), AE_NOT_FOUND (20140424/psparse-536)
```

dmesg (part 5):
```
[    1.029160] ata3.00: configured for UDMA/133
[    1.029395] ata4.00: configured for UDMA/133
[    1.029411] ata5.00: configured for UDMA/133
[    1.030172] ata1.00: configured for UDMA/133
[    1.030324] scsi 0:0:0:0: Direct-Access     ATA      ST500DM002-1BD14 KC48 PQ: 0 ANSI: 5
[    1.030478] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.030488] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.030489] sd 0:0:0:0: [sda] 4096-byte physical blocks
[    1.030534] sd 0:0:0:0: [sda] Write Protect is off
[    1.030535] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.030546] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.031689] scsi 1:0:0:0: CD-ROM            msi      DVD-RW DH24AS    LM21 PQ: 0 ANSI: 5
[    1.043740] usb 1-1: New USB device found, idVendor=8087, idProduct=8008
[    1.043742] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.044002] hub 1-1:1.0: USB hub found
[    1.044082] hub 1-1:1.0: 6 ports detected
[    1.047881]  sda: sda1 sda2
[    1.048183] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.050103] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.050106] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.050191] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.050226] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.050294] scsi 2:0:0:0: Direct-Access     ATA      ST2000DM001-1ER1 CC25 PQ: 0 ANSI: 5
[    1.050402] sd 2:0:0:0: [sdb] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
[    1.050404] sd 2:0:0:0: [sdb] 4096-byte physical blocks
[    1.050433] sd 2:0:0:0: [sdb] Write Protect is off
[    1.050435] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.050437] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    1.050452] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.050507] scsi 3:0:0:0: Direct-Access     ATA      ST2000DM001-1CH1 CC29 PQ: 0 ANSI: 5
[    1.050594] sd 3:0:0:0: Attached scsi generic sg3 type 0
[    1.050625] sd 3:0:0:0: [sdc] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
[    1.050626] sd 3:0:0:0: [sdc] 4096-byte physical blocks
[    1.050644] scsi 4:0:0:0: Direct-Access     ATA      ST2000DM001-1CH1 CC29 PQ: 0 ANSI: 5
[    1.050651] sd 3:0:0:0: [sdc] Write Protect is off
[    1.050652] sd 3:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    1.050662] sd 3:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.050762] sd 4:0:0:0: Attached scsi generic sg4 type 0
[    1.050790] sd 4:0:0:0: [sdd] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
[    1.050791] sd 4:0:0:0: [sdd] 4096-byte physical blocks
[    1.050809] scsi 5:0:0:0: Direct-Access     ATA      ST2000DM001-1CH1 CC29 PQ: 0 ANSI: 5
[    1.050814] sd 4:0:0:0: [sdd] Write Protect is off
[    1.050815] sd 4:0:0:0: [sdd] Mode Sense: 00 3a 00 00
[    1.050826] sd 4:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.050918] sd 5:0:0:0: Attached scsi generic sg5 type 0
[    1.050946] sd 5:0:0:0: [sde] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
[    1.050947] sd 5:0:0:0: [sde] 4096-byte physical blocks
[    1.050975] sd 5:0:0:0: [sde] Write Protect is off
[    1.050976] sd 5:0:0:0: [sde] Mode Sense: 00 3a 00 00
[    1.050987] sd 5:0:0:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.063888]  sdd: sdd1
[    1.063994] sd 4:0:0:0: [sdd] Attached SCSI disk
[    1.065886]  sdc: unknown partition table
[    1.065973] sd 3:0:0:0: [sdc] Attached SCSI disk
[    1.067702]  sde: sde1 sde2
[    1.067962] sd 5:0:0:0: [sde] Attached SCSI disk
[    1.069707]  sdb: unknown partition table
[    1.069881] sd 2:0:0:0: [sdb] Attached SCSI disk
[    1.099655] md: bind<sdb>
[    1.106089] md: bind<sdc>
[    1.107720] md: raid0 personality registered for level 0
[    1.107851] md/raid0:md127: md_size is 7813533696 sectors.
[    1.107852] md: RAID0 configuration for md127 - 1 zone
[    1.107853] md: zone0=[sdb/sdc]
[    1.107855]       zone-offset=         0KB, device-offset=         0KB, size=3906766848KB

[    1.107861] md127: detected capacity change from 0 to 4000529252352
[    1.135329]  md127: unknown partition table
[    1.155272] usb 2-1: new high-speed USB device number 2 using ehci-pci
[    1.291651] usb 2-1: New USB device found, idVendor=8087, idProduct=8000
[    1.291654] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.291892] hub 2-1:1.0: USB hub found
[    1.291997] hub 2-1:1.0: 8 ports detected
[    1.306299] random: nonblocking pool is initialized
[    1.463153] usb 3-14: new low-speed USB device number 2 using xhci_hcd
[    1.479994] device-mapper: table: 252:0: striped: Couldn't parse stripe destination
[    1.479997] device-mapper: ioctl: error adding target to table
[    1.486093] device-mapper: table: 252:0: striped: Couldn't parse stripe destination
[    1.486096] device-mapper: ioctl: error adding target to table
[    1.519130] tsc: Refined TSC clocksource calibration: 2993.068 MHz
[    1.598572] usb 3-14: New USB device found, idVendor=0557, idProduct=2221
[    1.598575] usb 3-14: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.598576] usb 3-14: Product: UC-10KM V1.3.124
[    1.598577] usb 3-14: Manufacturer: ATEN
[    1.598578] usb 3-14: SerialNumber: USB Composite device
[    1.598728] usb 3-14: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
[    1.598731] usb 3-14: ep 0x82 - rounding interval to 64 microframes, ep desc says 80 microframes
[    1.604594] hidraw: raw HID events driver (C) Jiri Kosina
[    1.614193] usbcore: registered new interface driver usbhid
[    1.614196] usbhid: USB HID core driver
[    1.614950] md: linear personality registered for level -1
[    1.615347] input: ATEN UC-10KM V1.3.124 as /devices/pci0000:00/0000:00:14.0/usb3/3-14/3-14:1.0/0003:0557:2221.0001/input/input6
[    1.616189] hid-generic 0003:0557:2221.0001: input,hidraw0: USB HID v1.10 Keyboard [ATEN UC-10KM V1.3.124] on usb-0000:00:14.0-14/input0
[    1.616262] input: ATEN UC-10KM V1.3.124 as /devices/pci0000:00/0000:00:14.0/usb3/3-14/3-14:1.1/0003:0557:2221.0002/input/input7
[    1.616374] hid-generic 0003:0557:2221.0002: input,hidraw1: USB HID v1.10 Mouse [ATEN UC-10KM V1.3.124] on usb-0000:00:14.0-14/input1
[    1.617507] md: multipath personality registered for level -4
[    1.620143] md: raid1 personality registered for level 1
[    1.687052] raid6: sse2x1    9669 MB/s
[    1.755028] raid6: sse2x2   12217 MB/s
[    1.823004] raid6: sse2x4   14078 MB/s
[    1.823005] raid6: using algorithm sse2x4 (14078 MB/s)
[    1.823006] raid6: using ssse3x2 recovery algorithm
[    1.823820] xor: measuring software checksum speed
[    1.862998]    prefetch64-sse: 20364.000 MB/sec
[    1.902982]    generic_sse: 18341.000 MB/sec
[    1.902983] xor: using function: prefetch64-sse (20364.000 MB/sec)
[    1.903776] async_tx: api initialized (async)
[    1.908329] md: raid6 personality registered for level 6
[    1.908330] md: raid5 personality registered for level 5
[    1.908331] md: raid4 personality registered for level 4
[    1.911858] md: raid10 personality registered for level 10
[    1.967028] Btrfs loaded
[    2.062274] BTRFS: device fsid a3d83995-4f83-46a9-a7da-24296268e25c devid 1 transid 22586 /dev/sda2
[    2.063040] BTRFS: device label NAS devid 1 transid 85 /dev/sdd1
[    2.063719] BTRFS: device label CIRBAK devid 1 transid 1864 /dev/sde1
[    2.064139] BTRFS: device label LCEBAK devid 1 transid 1150 /dev/sde2
[    2.064718] BTRFS: device fsid 254488a9-c64f-41b3-b066-445ce9a93fc2 devid 1 transid 6 /dev/md127
[    2.069053] BTRFS info (device sda2): disk space caching is enabled
[    2.518783] Switched to clocksource tsc
[    2.818776] [drm] Enabling RC6 states: RC6 on, RC6p off, RC6pp off
[    3.074764] init: plymouth-upstart-bridge main process (388) killed by TERM signal
[    8.306789] Adding 15998972k swap on /dev/sda1.  Priority:-1 extents:1 across:15998972k FS
[    8.681293] BTRFS info (device sda2): disk space caching is enabled
[   10.331977] systemd-udevd[675]: starting version 208
[   10.383626] lp: driver loaded but no devices found
[   10.385664] ppdev: user-space parallel port driver
[   10.387333] parport_pc 00:05: reported by Plug and Play ACPI
[   10.387377] parport0: PC-style at 0x378, irq 5 [PCSPP]
[   10.479227] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   10.483988] lp0: using parport0 (interrupt-driven).
[   10.492281] mei_me 0000:00:16.0: irq 45 for MSI/MSI-X
[   10.580798] audit: type=1400 audit(1426106973.452:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=763 comm="apparmor_parser"
[   10.580803] audit: type=1400 audit(1426106973.452:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=763 comm="apparmor_parser"
[   10.580806] audit: type=1400 audit(1426106973.452:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=763 comm="apparmor_parser"
[   10.641508] snd_hda_intel 0000:00:03.0: irq 46 for MSI/MSI-X
[   10.648011] snd_hda_intel 0000:00:1b.0: irq 47 for MSI/MSI-X
[   10.648402] intel_rapl: Found RAPL domain package
[   10.648405] intel_rapl: Found RAPL domain core
[   10.648407] intel_rapl: Found RAPL domain uncore
[   10.648408] intel_rapl: Found RAPL domain dram
[   10.670140] input: HDA Intel HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:03.0/sound/card0/input8
[   10.670187] input: HDA Intel HDMI HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:03.0/sound/card0/input9
[   10.673648] device-mapper: multipath: version 1.7.0 loaded
[   10.674464] sound hdaudioC1D0: autoconfig: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:line
[   10.674466] sound hdaudioC1D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   10.674468] sound hdaudioC1D0:    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0)
[   10.674469] sound hdaudioC1D0:    mono: mono_out=0x0
[   10.674469] sound hdaudioC1D0:    inputs:
[   10.674471] sound hdaudioC1D0:      Front Mic=0x19
[   10.674472] sound hdaudioC1D0:      Rear Mic=0x18
[   10.674473] sound hdaudioC1D0:      Line=0x1a
[   10.691591] input: HDA Intel PCH Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card1/input10
[   10.691670] input: HDA Intel PCH Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card1/input11
[   10.691742] input: HDA Intel PCH Line as /devices/pci0000:00/0000:00:1b.0/sound/card1/input12
[   10.691987] input: HDA Intel PCH Line Out as /devices/pci0000:00/0000:00:1b.0/sound/card1/input13
[   10.692158] input: HDA Intel PCH Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card1/input14
[   10.744307] audit: type=1400 audit(1426106973.616:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=845 comm="apparmor_parser"
[   10.744313] audit: type=1400 audit(1426106973.616:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=845 comm="apparmor_parser"
[   10.744315] audit: type=1400 audit(1426106973.616:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="third_party" pid=845 comm="apparmor_parser"
[   10.785412] Bluetooth: Core ver 2.19
[   10.785426] NET: Registered protocol family 31
[   10.785427] Bluetooth: HCI device and connection manager initialized
[   10.785842] Bluetooth: HCI socket layer initialized
[   10.785844] Bluetooth: L2CAP socket layer initialized
[   10.785850] Bluetooth: SCO socket layer initialized
[   10.795440] Bluetooth: RFCOMM TTY layer initialized
[   10.795448] Bluetooth: RFCOMM socket layer initialized
[   10.795452] Bluetooth: RFCOMM ver 1.11
[   10.821697] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   10.821699] Bluetooth: BNEP filters: protocol multicast
[   10.821706] Bluetooth: BNEP socket layer initialized
[   10.941322] asus_wmi: ASUS WMI generic driver loaded
[   10.943410] asus_wmi: Initialization: 0x0
[   10.943424] asus_wmi: BIOS WMI version: 0.9
[   10.943448] asus_wmi: SFUN value: 0x0
[   10.943675] input: Eee PC WMI hotkeys as /devices/platform/eeepc-wmi/input/input15
[   10.944269] asus_wmi: Backlight controlled by ACPI video driver
[   11.035822] init: cups main process (846) killed by HUP signal
[   11.035828] init: cups main process ended, respawning
[   11.144762] init: failsafe main process (966) killed by TERM signal
[   11.562014] audit: type=1400 audit(1426106974.432:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=1187 comm="apparmor_parser"
[   11.562020] audit: type=1400 audit(1426106974.432:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="chromium" pid=1187 comm="apparmor_parser"
[   11.563064] audit: type=1400 audit(1426106974.432:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=1187 comm="apparmor_parser"
[   11.563069] audit: type=1400 audit(1426106974.432:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1187 comm="apparmor_parser"
[   11.869032] systemd-logind[1217]: New seat seat0.
[   11.869267] systemd-logind[1217]: Watching system buttons on /dev/input/event1 (Power Button)
[   11.869302] systemd-logind[1217]: Watching system buttons on /dev/input/event2 (Video Bus)
[   11.869332] systemd-logind[1217]: Watching system buttons on /dev/input/event0 (Power Button)
[   11.971466] e1000e 0000:00:19.0: irq 43 for MSI/MSI-X
[   12.075352] e1000e 0000:00:19.0: irq 43 for MSI/MSI-X
[   12.075431] IPv6: ADDRCONF(NETDEV_UP): eth2: link is not ready
[   12.083778] r8169 0000:04:00.0 eth0: link down
[   12.083794] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   12.091792] r8169 0000:04:01.0 eth1: link down
[   12.091816] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[   12.798180] init: samba-ad-dc main process (1396) terminated with status 1
[   13.635747] device-mapper: table: 252:1: striped: Couldn't parse stripe destination
[   13.635750] device-mapper: ioctl: error adding target to table
[   13.642895] device-mapper: table: 252:0: striped: Couldn't parse stripe destination
[   13.642898] device-mapper: ioctl: error adding target to table
[   15.128768] systemd-logind[1217]: Failed to start unit user@111.service: Unknown unit: user@111.service
[   15.128773] systemd-logind[1217]: Failed to start user service: Unknown unit: user@111.service
[   15.131122] systemd-logind[1217]: New session c1 of user lightdm.
[   15.131135] systemd-logind[1217]: Linked /tmp/.X11-unix/X0 to /run/user/111/X11-display.
[   15.208473] Fusion MPT base driver 3.04.20
[   15.208475] Copyright (c) 1999-2008 LSI Corporation
[   15.209756] Fusion MPT misc device (ioctl) driver 3.04.20
[   15.209804] mptctl: Registered with Fusion MPT base driver
[   15.209806] mptctl: /dev/mptctl @ (major,minor=10,220)
[   15.631649] e1000e: eth2 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
[   15.631679] IPv6: ADDRCONF(NETDEV_CHANGE): eth2: link becomes ready
[   27.344734] systemd-logind[1217]: Failed to start unit user@1000.service: Unknown unit: user@1000.service
[   27.344739] systemd-logind[1217]: Failed to start user service: Unknown unit: user@1000.service
[   27.364346] systemd-logind[1217]: New session c2 of user administrator.
[   27.364361] systemd-logind[1217]: Linked /tmp/.X11-unix/X0 to /run/user/1000/X11-display.
[   40.840805] audit_printk_skb: 48 callbacks suppressed
[   40.840808] audit: type=1400 audit(1426107003.730:28): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=3329 comm="apparmor_parser"
[   40.840813] audit: type=1400 audit(1426107003.730:29): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=3329 comm="apparmor_parser"
[   40.850136] audit: type=1400 audit(1426107003.742:30): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="third_party" pid=3329 comm="apparmor_parser"
[  129.503055] systemd-logind[1217]: Failed to start unit user@1001.service: Unknown unit: user@1001.service
[  129.503067] systemd-logind[1217]: Failed to start user service: Unknown unit: user@1001.service
[  129.510773] systemd-logind[1217]: New session 1 of user itlce.
[  238.487924] BTRFS info (device md127): disk space caching is enabled
[  361.817474] BTRFS info (device md127): disk space caching is enabled
[65371.671317] systemd-logind[1217]: Failed to start unit user@1031.service: Unknown unit: user@1031.service
[65371.671325] systemd-logind[1217]: Failed to start user service: Unknown unit: user@1031.service
[65371.675988] systemd-logind[1217]: New session c3 of user allyson.
[84844.304311] systemd-logind[1217]: New session 28 of user itlce.
```

---

### Post by erictherev on 2015-03-12
parted:
```
itlce@LCE-NAS:~$ sudo parted **/dev/md127**
GNU Parted 3.2
Using /dev/md127
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) unit GB
(parted) p
**Model: Linux Software RAID Array (md)**
Disk /dev/md127: 4001GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop
Disk Flags:

Number  Start   End     Size    File system  Flags
 1      0.00GB  4001GB  4001GB  btrfs

(parted) q
itlce@LCE-NAS:~$
```

Finally,

fdisk -l
```
Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x88e11e19

Device     Boot    Start       End   Sectors   Size Id Type
/dev/sda1  *        2048  31999999  31997952  15.3G 82 Linux swap / Solaris
/dev/sda2       32000000 976773119 944773120 450.5G 83 Linux

Disk /dev/sdb: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk /dev/sdc: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk /dev/sdd: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0xc5178cc7

Device     Boot Start        End    Sectors  Size Id Type
/dev/sdd1        2048 3907028991 3907026944  1.8T 83 Linux

Disk /dev/sde: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x63bcc82a

Device     Boot      Start        End    Sectors   Size Id Type
/dev/sde1             2048 1953511423 1953509376 931.5G 83 Linux
/dev/sde2       1953511424 3907028991 1953517568 931.5G 83 Linux

Disk /dev/md127: 3.7 TiB, 4000529252352 bytes, 7813533696 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 524288 bytes / 1048576 bytes
```

The drives I am working with are labeled as /dev/sdb and /dev/sdc. The array is labeled as /dev/md127.

I'm not sure what information will help anyone figure out what the issue is, so I posted everything I know of that might help. If more information will be helpful, let me know what is needed.

Thanks for all the help.

*edit: After looking this over again, it seems that Kubuntu believes this is a software RAID array, hence the 'md' designation. This confuses me even more.*

---

### Post by tgalati4 on 2015-03-13
Intel SATA RAID controllers tend to be fakeRAID, so that means you are really using a software RAID even though you configured the RAID in BIOS.  One thing you can try is to take one drive out of the machine.  Boot up and format the single drive as Ext4.  Then swap drives and format the other as Ext4.  Then put the drive back and you will have two identical, Ext4-formatted drives that fdisk can recognize.  

Boot into BIOS and set up the drives as RAID0.  Boot into linux and see if fdisk recognizes the md drive as a RAID0 array.  The fact that it has an md device label would indicate it a managed device (I believe that is where md comes from) and thus a software RAID array.

I don't know if btrfs is compatible with RAID0 or if *mdadm* can handle btrfs.  

You might set up LVM and set up btrfs on each drive and simply link the drives as one LVM.  That will give you more storage, but won't give you the striping speed that you expect.

---

### Post by erictherev on 2015-03-13
OK, cleared everything and starting over from scratch using dmraid (mdadm is too confusing with only 1 cup of coffee.)
```
itlce@LCE-NAS:~$ sudo dmraid -f isw -C rda --type 0 --disk "/dev/sdb /dev/sdc"


     Create a RAID set with ISW metadata format

RAID name:      rda
RAID type:      RAID0
RAID size:      3726G (7814039228 blocks)
RAID strip:     128k (256 blocks)
DISKS:     /dev/sdb, /dev/sdc,


About to create a RAID set with the above settings. Continue ? [y/n] :y
itlce@LCE-NAS:~$
```
That looks good. No errors.
Activate the array.
```
itlce@LCE-NAS:~$ sudo dmraid -ay
RAID set "isw_ihihagdaf_rda" was activated
itlce@LCE-NAS:~$
```
List the devices.
```
itlce@LCE-NAS:~$ sudo dmraid -b
[COLOR="#008000"]/dev/dm-0:   7814039552 total, "N/A"[/COLOR]
/dev/sde:   3907029168 total, "W1E8JAHE"
/dev/sdd:   3907029168 total, "W1E8JBBV"
/dev/sdc:   3907029168 total, "W1E8JAMB"
/dev/sdb:   3907029168 total, "Z4Z0NZ90"
/dev/sda:    976773168 total, "W3TANE4D"
itlce@LCE-NAS:~$
```
OK, fire up KDE Partition Editor.
There it is. OK, create partiton, format and label. Looks good. Let's see what we have.
```
itlce@LCE-NAS:~$ sudo fdisk -l

Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x88e11e19

Device     Boot    Start       End   Sectors   Size Id Type
/dev/sda1  *        2048  31999999  31997952  15.3G 82 Linux swap / Solaris
/dev/sda2       32000000 976773119 944773120 450.5G 83 Linux

Disk /dev/sdb: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x00000000

Device     Boot Start        End    Sectors Size Id Type
/dev/sdb1           1 4294967295 4294967295   2T ee GPT

Partition 2 does not start on physical sector boundary.

[COLOR="#B22222"]The backup GPT table is corrupt, but the primary appears OK, so that will be used.[/COLOR]

Disk /dev/sdc: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: FA533B57-0B76-44A9-965E-FA9495D1AD08


Disk /dev/sdd: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0xc5178cc7

Device     Boot Start        End    Sectors  Size Id Type
/dev/sdd1        2048 3907028991 3907026944  1.8T 83 Linux

Disk /dev/sde: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x63bcc82a

Device     Boot      Start        End    Sectors   Size Id Type
/dev/sde1             2048 1953511423 1953509376 931.5G 83 Linux
/dev/sde2       1953511424 3907028991 1953517568 931.5G 83 Linux

[COLOR="#008000"]Disk /dev/mapper/isw_ihihagdaf_rda: 3.7 TiB, 4000788250624 bytes, 7814039552 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 131072 bytes / 262144 bytes
Disklabel type: gpt
Disk identifier: F58702BC-8D26-4DCA-BE16-77B6F3F8E6AA

Device                         Start        End    Sectors  Size Type
/dev/mapper/isw_ihihagdaf_rda1  2048 7814037503 7814035456  3.7T Linux filesyste[/COLOR]

itlce@LCE-NAS:~$

```

The backup GPT table being corrupt is a bit concerning, but other than that everything looks good.

WOOHOO! Success!

Thanks again for all of the help.

---

### Post by tgalati4 on 2015-03-13
That is a clever solution.  Let us know how long it lasts.

---

