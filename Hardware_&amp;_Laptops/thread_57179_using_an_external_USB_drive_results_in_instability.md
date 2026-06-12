---
title: "using an external USB drive results in instability, uninterruptible process"
date: 2005-08-15
forum: Hardware &amp; Laptops
---

### Post by renick on 2005-08-15
I'm using Ubuntu Hoary, 2.6.10 kernel. My machine is a Pentium 4 2.4 with 756 mb RAM. I've got two external USB 2.0 drives which connect to the USB 2.0 PCI card through an externally-powered hub. The drives mount, and are infrequently navigable. However, sometimes navigating them in ROX-Filer or xffm results in the process accessing the drive becoming uninterruptible. When they are navigable, I can access some small files (view a jpg or read a small text file). However, operations such as playing an mp3 from one of the drives will make the mp3 player uninterruptible. Once this happens, the system becomes unstable, sometimes freezing when closing the session or rebooting. If the drive is then unplugged after a process using the drive goes uninterruptible, a hard freeze results forcing a cold reset.

Output of dmesg shows, beginning with hotplug messages:

```
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
uhci_hcd 0000:00:1d.0: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
PCI: Setting latency timer of device 0000:00:1d.0 to 64
uhci_hcd 0000:00:1d.0: irq 16, io base 0xd800
uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
uhci_hcd 0000:00:1d.1: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
PCI: Setting latency timer of device 0000:00:1d.1 to 64
uhci_hcd 0000:00:1d.1: irq 19, io base 0xd000
uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
uhci_hcd 0000:00:1d.2: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
PCI: Setting latency timer of device 0000:00:1d.2 to 64
uhci_hcd 0000:00:1d.2: irq 18, io base 0xd400
uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
hub 3-0:1.0: USB hub found
hub 3-0:1.0: 2 ports detected
usb 1-2: new full speed USB device using uhci_hcd and address 2
hub 1-2:1.0: USB hub found
hub 1-2:1.0: 4 ports detected
ACPI: PCI interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 23
ehci_hcd 0000:00:1d.7: Intel Corp. 82801DB/DBM (ICH4/ICH4-M) USB 2.0 EHCI Controller
PCI: Setting latency timer of device 0000:00:1d.7 to 64
ehci_hcd 0000:00:1d.7: irq 23, pci mem 0xe2100000
ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
PCI: cache line size of 128 is not supported by device 0000:00:1d.7
ehci_hcd 0000:00:1d.7: USB 2.0 initialized, EHCI 1.00, driver 26 Oct 2004
hub 4-0:1.0: USB hub found
hub 4-0:1.0: 6 ports detected
hub 1-2:1.0: hub_port_status failed (err = -71)
hub 1-2:1.0: connect-debounce failed, port 1 disabled
hub 1-2:1.0: cannot disable port 1 (err = -71)
hub 1-2:1.0: hub_port_status failed (err = -71)
hub 1-2:1.0: hub_port_status failed (err = -71)
hub 1-2:1.0: hub_port_status failed (err = -71)
hub 1-2:1.0: hub_hub_status failed (err = -71)
hub 1-2:1.0: get_hub_status failed
Evaluate _OSC Set fails. Status = 0x0005
pciehp: add_host_bridge: status 5
pciehp: Fails to gain control of native hot-plug
usb 4-2: new high speed USB device using ehci_hcd and address 2
hw_random: RNG not detected
hub 4-2:1.0: USB hub found
hub 4-2:1.0: 4 ports detected
usb 1-2: USB disconnect, address 2
usb 4-2.1: new high speed USB device using ehci_hcd and address 3
8139too Fast Ethernet driver 0.9.27
ACPI: PCI interrupt 0000:02:00.0[A] -> GSI 18 (level, low) -> IRQ 18
eth0: RealTek RTL8139 at 0xc000, 00:40:f4:3a:35:83, IRQ 18
eth0:  Identified 8139 chip type 'RTL-8139C'
usb 4-2.3: new high speed USB device using ehci_hcd and address 4
8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
hub 4-2.3:1.0: USB hub found
hub 4-2.3:1.0: 4 ports detected
Initializing USB Mass Storage driver...
usb 4-2.4: new low speed USB device using ehci_hcd and address 5
scsi0 : SCSI emulation for USB Mass Storage devices
usbcore: registered new driver usb-storage
USB Mass Storage support registered.
usb-storage: device found at 3
usb-storage: waiting for device to settle before scanning
eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
usb 4-2.3.2: new high speed USB device using ehci_hcd and address 6
scsi1 : SCSI emulation for USB Mass Storage devices
usb-storage: device found at 6
usb-storage: waiting for device to settle before scanning
ACPI: PCI interrupt 0000:02:02.0[A] -> GSI 22 (level, low) -> IRQ 22
usb 4-2.3.4: new high speed USB device using ehci_hcd and address 7
ehci_hcd 0000:00:1d.7: qh ebda6400 (#0) state 4
scsi2 : SCSI emulation for USB Mass Storage devices
usbcore: registered new driver hiddev
input: USB HID v1.10 Mouse [Logitech USB Trackball] on usb-0000:00:1d.7-2.4
usbcore: registered new driver usbhid
drivers/usb/input/hid-core.c: v2.0:USB HID core driver
NET: Registered protocol family 17
usb-storage: device found at 7
usb-storage: waiting for device to settle before scanning
gameport: pci0000:02:02.1 speed 1046 kHz
ohci1394: $Rev: 1223 $ Ben Collins <bcollins@debian.org>
ACPI: PCI interrupt 0000:02:03.0[A] -> GSI 16 (level, low) -> IRQ 16
ohci1394: fw-host0: Unexpected PCI resource length of 1000!
ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[16]  MMIO=[e2001000-e20017ff]  Max Packet=[2048]
ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0001990000049a68]
ieee1394: Node added: ID:BUS[0-01:1023]  GUID[000d6c030088cbf0]
usb 4-2.3.4: USB disconnect, address 7
usb 4-2.1: USB disconnect, address 3
NET: Registered protocol family 10
Disabled Privacy Extensions on device c02f0500(lo)
IPv6 over IPv4 tunneling driver
  Vendor: HL-DT-ST  Model: DVDRAM GSA-5120D  Rev: A104
  Type:   CD-ROM                             ANSI SCSI revision: 00
usb-storage: device scan complete
sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
Attached scsi CD-ROM sr0 at scsi1, channel 0, id 0, lun 0
Attached scsi generic sg0 at scsi1, channel 0, id 0, lun 0,  type 5
ACPI: Power Button (FF) [PWRF]
ACPI: Sleep Button (CM) [SLPB]
ibm_acpi: ec object not found
apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
apm: overridden by ACPI.
eth0: no IPv6 routers present
usb 4-2.1: new high speed USB device using ehci_hcd and address 8
scsi3 : SCSI emulation for USB Mass Storage devices
usb-storage: device found at 8
usb-storage: waiting for device to settle before scanning
  Vendor: Maxtor    Model: 6Y080P0           Rev: YAR4
  Type:   Direct-Access                      ANSI SCSI revision: 02
Attached scsi generic sg1 at scsi3, channel 0, id 0, lun 0,  type 0
usb-storage: device scan complete
SCSI device sda: 160082880 512-byte hdwr sectors (81962 MB)
sda: assuming drive cache: write through
SCSI device sda: 160082880 512-byte hdwr sectors (81962 MB)
sda: assuming drive cache: write through
 /dev/scsi/host3/bus0/target0/lun0: p1 p2 p3
Attached scsi disk sda at scsi3, channel 0, id 0, lun 0
usb 4-2.3.4: new high speed USB device using ehci_hcd and address 9
scsi4 : SCSI emulation for USB Mass Storage devices
usb-storage: device found at 9
usb-storage: waiting for device to settle before scanning
  Vendor: WDC WD12  Model: 00BB-00FTA0       Rev: 15.0
  Type:   Direct-Access                      ANSI SCSI revision: 00
SCSI device sdb: 234441648 512-byte hdwr sectors (120034 MB)
sdb: assuming drive cache: write through
SCSI device sdb: 234441648 512-byte hdwr sectors (120034 MB)
sdb: assuming drive cache: write through
 /dev/scsi/host4/bus0/target0/lun0: p1
Attached scsi disk sdb at scsi4, channel 0, id 0, lun 0
Attached scsi generic sg2 at scsi4, channel 0, id 0, lun 0,  type 0
usb-storage: device scan complete
```

/var/log/syslog shows this before such a crash:

```
Aug 16 01:20:52 localhost kernel: drivers/usb/input/hid-core.c: input irq status -71 received
Aug 16 01:20:53 localhost last message repeated 11 times
Aug 16 01:20:53 localhost kernel: usb 4-2: USB disconnect, address 2
Aug 16 01:20:53 localhost kernel: usb 4-2.1: USB disconnect, address 8
Aug 16 01:20:53 localhost kernel: drivers/usb/input/hid-core.c: input irq status -71 received
Aug 16 01:20:53 localhost kernel: drivers/usb/input/hid-core.c: can't resubmit intr, 0000:00:1d.7-2.4/input0, status -19
```

Drives work without error in Windows. Advice?

---

### Post by renick on 2005-08-15
Forgot to mention, I have the same experience with both external drives. One is FAT32, the other is NTFS. 

More var/log/syslog:

```
Aug 16 00:21:30 localhost kernel: NTFS volume version 3.1.
Aug 16 00:21:50 localhost kernel: NTFS-fs error (device sdb1): ntfs_ucstonls(): Unicode name contains characters that cannot be converted to character set cp437.
Aug 16 00:21:51 localhost last message repeated 3 times
Aug 16 00:21:53 localhost anacron[8927]: Job `cron.daily' started
Aug 16 00:21:53 localhost anacron[9339]: Updated timestamp for job `cron.daily' to 2005-08-16
Aug 16 00:21:56 localhost kernel: NTFS-fs error (device sdb1): ntfs_ucstonls(): Unicode name contains characters that cannot be converted to character set cp437.
Aug 16 00:22:30 localhost last message repeated 41 times
Aug 16 00:23:35 localhost last message repeated 78 times
Aug 16 00:24:15 localhost last message repeated 53 times
Aug 16 00:24:39 localhost gconfd (nick-9288): Exiting
Aug 16 00:25:04 localhost gconfd (nick-9601): starting (version 2.10.0), pid 9601 user 'nick'
Aug 16 00:25:04 localhost gconfd (nick-9601): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Aug 16 00:25:04 localhost gconfd (nick-9601): Resolved address "xml:readwrite:/home/nick/.gconf" to a writable configuration source at position 1
Aug 16 00:25:04 localhost gconfd (nick-9601): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Aug 16 00:25:28 localhost gconfd (nick-9601): Exiting
Aug 16 00:25:29 localhost shutdown[9621]: shutting down for system reboot
```

---

### Post by martibs on 2006-02-04
I have the same problem, only with a FireWire disk.

---

### Post by jonrkc on 2006-11-18
I have been having this problem for some time, too--and just now found a solution, at least for me.

Apparently the problem has to do with USB 2.0.  The post I read on a university users' group mailing list, the very last result in two pages of Google results (!), suggested that the problem might not exist if the device was operating on a USB 1.1 interface.

I probably started having the problem with my flash drive when I acquired a new computer that has only USB 2.0 built in.  I do have a hub that's good for both USB 2.0 and USB 1.1, however, so I plugged the drive into it--and it works normally.  

Oddly, if I booted to Knoppix, the device worked normally there, even plugged directly into the computer.  So I'm still mystified.  I guess Knoppix is just better than Ubuntu in this regard.  :)  Seriously, it suggests to me a problem with the kernel version in my Xubuntu installation.

Anyway, now I can use my flash drive again, as long as I plug it into the old hub instead of directly into the computer.  The computer I used before this one was from 1999, and its connection was via USB 1.1, so that's apparently why I had no problem using the flash drive with it.

To recap, if you can get a USB 1.1 connection for the device causing the repeated error messages, the problem may be fixed.

---

