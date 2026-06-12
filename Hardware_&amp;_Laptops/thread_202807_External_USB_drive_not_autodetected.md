---
title: "External USB drive not autodetected"
date: 2006-06-24
forum: Hardware &amp; Laptops
---

### Post by aktiv on 2006-06-24
I have an external WD Mediacenter 250gig USB/FW with a fat32 partition on it
It was running just fine under 5.10, mounting it as /dev/sda1

When I upgraded to 6.06, it was autodetected during install, but then my
logitech wireless mouse/keys wouldnt work. After a while, for no obvious reason, the mouse/keys started working again, while the disk went missing. 
My /dev/ contained no sdXn.
My dmesg gave me error 71 on the device. I tried disabling acpi but no luck.
( I have no idea what error 71 indicates btw )

After reading some forums and trying without getting anywhere, I re-installed 5.10,
but now I have the exact same problems there, even though I unplugged a couple of rarely used usb-devices and installed with noacpi nolacpi.

I know there is no problems with the disk itself since it works just fine on my winxp comp.

Does anyone have any good ideas, I have all my music on that disk, and I'm going crazy without it :)

PS. I'm kinda new to Linux so please don't RTFM me if there is a real simple solution to this :) I've been reading and trying and failing for a couple of days now ](*,)

From dmesg on 5.10:
[4294677.427000] ohci_hcd 0000:00:02.0: nVidia Corporation nForce2 USB Controller
[4294677.450000] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[4294677.450000] ohci_hcd 0000:00:02.0: irq 5, io mem 0xea087000
[4294677.503000] hub 1-0:1.0: USB hub found
[4294677.503000] hub 1-0:1.0: 3 ports detected
[4294677.506000] ACPI: PCI Interrupt Link [LUBB] enabled at IRQ 11                          # I thought I had in disabled during install ??
[4294677.506000] PCI: setting IRQ 11 as level-triggered
[4294677.506000] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [LUBB] -> GSI 11 (l evel, low) -> IRQ 11
[4294677.506000] PCI: Setting latency timer of device 0000:00:02.1 to 64
[4294677.506000] ohci_hcd 0000:00:02.1: nVidia Corporation nForce2 USB Controlle r (#2)
[4294677.529000] ohci_hcd 0000:00:02.1: new USB bus registered, assigned bus num ber 2
[4294677.529000] ohci_hcd 0000:00:02.1: irq 11, io mem 0xea082000
[4294677.582000] hub 2-0:1.0: USB hub found                                                         # the WD media center is a 3 port usb HUB
[4294677.582000] hub 2-0:1.0: 3 ports detected
[4294677.609000] ACPI: PCI Interrupt Link [LUB2] enabled at IRQ 5
[4294677.609000] ACPI: PCI Interrupt 0000:00:02.2[C] -> Link [LUB2] -> GSI 5 (le vel, low) -> IRQ 5
[4294677.609000] PCI: Setting latency timer of device 0000:00:02.2 to 64
[4294677.609000] ehci_hcd 0000:00:02.2: nVidia Corporation nForce2 USB Controlle r
[4294677.609000] ehci_hcd 0000:00:02.2: debug port 1
[4294677.609000] ehci_hcd 0000:00:02.2: new USB bus registered, assigned bus num ber 3
[4294677.609000] ehci_hcd 0000:00:02.2: irq 5, io mem 0xea083000
[4294677.609000] PCI: cache line size of 64 is not supported by device 0000:00:0 2.2
[4294677.609000] ehci_hcd 0000:00:02.2: park 0
[4294677.609000] ehci_hcd 0000:00:02.2: USB 2.0 initialized, EHCI 1.00, driver 1 0 Dec 2004
[4294677.609000] hub 3-0:1.0: USB hub found
[4294677.609000] hub 3-0:1.0: 6 ports detected
[4294677.642000] forcedeth.c: Reverse Engineered nForce ethernet driver. Version  0.41.
[4294677.643000] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 11
[4294677.643000] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [LMAC] -> GSI 11 (l evel, low) -> IRQ 11
[4294677.643000] PCI: Setting latency timer of device 0000:00:04.0 to 64
[4294678.112000] usb 3-2: new high speed USB device using ehci_hcd and address 2
[4294678.155000] eth0: forcedeth.c: subsystem: 01043:80a7 bound to 0000:00:04.0
[4294678.184000] usb 3-2: device descriptor read/64, error -71                                            # error 71, no idea what it means
[4294678.246000] sata_sil version 0.9
[4294678.247000] ACPI: PCI Interrupt Link [LNK3] enabled at IRQ 11
[4294678.247000] ACPI: PCI Interrupt 0000:01:0b.0[A] -> Link [LNK3] -> GSI 11 (l evel, low) -> IRQ 11
[4294678.247000] ata1: SATA max UDMA/100 cmd 0xF88FC080 ctl 0xF88FC08A bmdma 0xF 88FC000 irq 11
[4294678.247000] ata2: SATA max UDMA/100 cmd 0xF88FC0C0 ctl 0xF88FC0CA bmdma 0xF 88FC008 irq 11
[4294678.347000] usb 3-2: device descriptor read/64, error -71
[4294678.448000] ata1: no device found (phy stat 00000000)
[4294678.448000] scsi0 : sata_sil
[4294678.510000] usb 3-2: new high speed USB device using ehci_hcd and address 3
[4294678.572000] usb 3-2: device descriptor read/64, error -71
[4294678.649000] ata2: no device found (phy stat 00000000)
[4294678.649000] scsi1 : sata_sil
[4294678.664000] ACPI: PCI Interrupt Link [L3CM] enabled at IRQ 5
[4294678.664000] ACPI: PCI Interrupt 0000:02:01.0[A] -> Link [L3CM] -> GSI 5 (le vel, low) -> IRQ 5
[4294678.664000] 3c59x: Donald Becker and others. [www.scyld.com/network/vortex.h](www.scyld.com/network/vortex.h) tml
[4294678.664000] 0000:02:01.0: 3Com PCI 3c920 Tornado at 0xc000. Vers LK1.1.19
[4294678.750000] usb 3-2: device descriptor read/64, error -71
[4294678.913000] usb 3-2: new high speed USB device using ehci_hcd and address 4
[4294679.315000] usb 3-2: device not accepting address 4, error -71
[4294679.377000] usb 3-2: new high speed USB device using ehci_hcd and address 5
[4294679.779000] usb 3-2: device not accepting address 5, error -71
[4294679.934000] ohci_hcd 0000:00:02.1: wakeup
[4294680.046000] ohci_hcd 0000:00:02.0: wakeup
[4294680.274000] usb 2-2: new full speed USB device using ohci_hcd and address 2
[4294680.486000] hub 2-2:1.0: USB hub found
[4294680.514000] hub 2-2:1.0: 5 ports detected
[4294680.806000] usb 1-3: new low speed USB device using ohci_hcd and address 2
[4294680.990000] usb 2-2.1: new full speed USB device using ohci_hcd and address  3
[4294681.291000] ACPI: CPU0 (power states: C1[C1])
[4294681.510000] usb 2-2.2: new low speed USB device using ohci_hcd and address 

from lsusb:
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 006: ID 08ca:0010 Aiptek International, Inc. Tablet
Bus 002 Device 005: ID 03f0:2811 Hewlett-Packard PSC-2100
Bus 002 Device 004: ID 046d:c50b Logitech, Inc.
Bus 002 Device 003: ID 04a8:0404 Multivideo Labs, Inc.                # This is what the system thinks the disk is. It used to say Western Digital something 
Bus 002 Device 002: ID 04a8:0303 Multivideo Labs, Inc.                # I thought the problem could be with some new system updates but the problem is the same even before upgrading
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 002: ID 05e3:000b Genesys Logic, Inc. Mouse
Bus 001 Device 001: ID 0000:0000

---

