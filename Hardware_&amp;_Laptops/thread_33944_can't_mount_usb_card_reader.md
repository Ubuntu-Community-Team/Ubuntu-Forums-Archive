---
title: "can't mount usb card reader"
date: 2005-05-12
forum: Hardware &amp; Laptops
---

### Post by johnistpropaganda on 2005-05-12
For some strange reason, i can't mount my card reader.  I've poked around the forums but can't seem to find a solution.

When i try "lsusb" i get :
```
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
``` 

"dmesg" gives me the following:
```
est: I/O error, dev hdc, sector 16
Buffer I/O error on device hdc, logical block 2
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x54
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 24
Buffer I/O error on device hdc, logical block 3
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x54
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 32
Buffer I/O error on device hdc, logical block 4
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x54
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 40
Buffer I/O error on device hdc, logical block 5
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x54
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 48
Buffer I/O error on device hdc, logical block 6
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x54
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 56
Buffer I/O error on device hdc, logical block 7
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x54
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 0
Buffer I/O error on device hdc, logical block 0
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x54
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 0
cdrom: open failed.
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x54
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 0
cdrom: open failed.
Real Time Clock Driver v1.12
input: PC Speaker
inserting floppy driver for 2.6.10-5-386
Floppy drive(s): fd0 is 1.44M
FDC 0 is a post-1991 82077
Linux agpgart interface v0.100 (c) Dave Jones
agpgart: Detected SiS 730 chipset
agpgart: Maximum main memory to use for agp memory: 564M
agpgart: AGP aperture is 64M @ 0xd0000000
usbcore: registered new driver usbfs
usbcore: registered new driver hub
ohci_hcd: 2004 Nov 08 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
PCI: setting IRQ 11 as level-triggered
ACPI: PCI interrupt 0000:00:01.2[D] -> GSI 11 (level, low) -> IRQ 11
ohci_hcd 0000:00:01.2: Silicon Integrated Systems [SiS] USB 1.0 Controller
ohci_hcd 0000:00:01.2: irq 11, pci mem 0xd8001000
ohci_hcd 0000:00:01.2: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 3 ports detected
ACPI: PCI interrupt 0000:00:01.3[D] -> GSI 11 (level, low) -> IRQ 11
ohci_hcd 0000:00:01.3: Silicon Integrated Systems [SiS] USB 1.0 Controller (#2)
ohci_hcd 0000:00:01.3: irq 11, pci mem 0xd8002000
ohci_hcd 0000:00:01.3: new USB bus registered, assigned bus number 2
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 3 ports detected
ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 3
PCI: setting IRQ 3 as level-triggered
ACPI: PCI interrupt 0000:00:01.4[B] -> GSI 3 (level, low) -> IRQ 3
MC'97 1 converters and GPIO not ready (0x411)
cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
pciehp: acpi_pciehprm:\_SB_.PCI0 evaluate _BBN fail=0x5
pciehp: acpi_pciehprm:get_device PCI ROOT HID fail=0x5
8139too Fast Ethernet driver 0.9.27
ACPI: PCI interrupt 0000:00:0d.0[A] -> GSI 11 (level, low) -> IRQ 11
eth0: RealTek RTL8139 at 0xe400, 00:07:95:fd:00:61, IRQ 11
eth0:  Identified 8139 chip type 'RTL-8139C'
8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
NET: Registered protocol family 17
NET: Registered protocol family 10
Disabled Privacy Extensions on device c02f0500(lo)
IPv6 over IPv4 tunneling driver
ACPI: Power Button (FF) [PWRF]
ACPI: Sleep Button (CM) [FUTS]
ibm_acpi: ec object not found
apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
apm: overridden by ACPI.
eth0: no IPv6 routers present
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x54
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 64
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x54
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 880868
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x54
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 879844
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x54
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 879620
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x54
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 880860
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x54
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 879836
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x54
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 879612
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x54
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 880268
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x54
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 879244
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x54
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 879020
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x54
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 880260
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x54
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 879236
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x54
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 879012
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x54
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 722780
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x54
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 721756
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x54
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 721532
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x54
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 722772
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x54
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 721748
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x54
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 721524
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x54
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 722180
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x54
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 721156
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x54
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 720932
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x54
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 722172
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x54
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 721148
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x54
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 720924
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x54
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 1248
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x54
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 1024
UDF-fs: No partition found (1)
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x54
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 64
isofs_fill_super: bread failed, dev=hdc, iso_blknum=16, block=16
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x54
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 64
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x54
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 880868
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x54
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 879844
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x54
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 879620
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x54
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 880860
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x54
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 879836
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x54
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 879612
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x54
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 880268
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x54
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 879244
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x54
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 879020
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x54
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 880260
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x54
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 879236
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x54
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 879012
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x54
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 722780
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x54
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 721756
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x54
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 721532
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x54
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 722772
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x54
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 721748
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x54
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 721524
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x54
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 722180
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x54
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 721156
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x54
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 720932
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x54
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 722172
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x54
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 721148
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x54
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 720924
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x54
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 1248
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x54
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 1024
UDF-fs: No partition found (1)
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x54
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 64
isofs_fill_super: bread failed, dev=hdc, iso_blknum=16, block=16
ohci_hcd 0000:00:01.2: remove, state 1
usb usb1: USB disconnect, address 1
ohci_hcd 0000:00:01.2: USB bus 1 deregistered
ohci_hcd 0000:00:01.3: remove, state 1
usb usb2: USB disconnect, address 1
ohci_hcd 0000:00:01.3: USB bus 2 deregistered
usbcore: deregistering driver usbfs
usbcore: deregistering driver hub
usbcore: registered new driver usbfs
usbcore: registered new driver hub
ohci_hcd: 2004 Nov 08 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
ACPI: PCI interrupt 0000:00:01.2[D] -> GSI 11 (level, low) -> IRQ 11
ohci_hcd 0000:00:01.2: Silicon Integrated Systems [SiS] USB 1.0 Controller
ohci_hcd 0000:00:01.2: irq 11, pci mem 0xd8001000
ohci_hcd 0000:00:01.2: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 3 ports detected
ACPI: PCI interrupt 0000:00:01.3[D] -> GSI 11 (level, low) -> IRQ 11
ohci_hcd 0000:00:01.3: Silicon Integrated Systems [SiS] USB 1.0 Controller (#2)
ohci_hcd 0000:00:01.3: irq 11, pci mem 0xd8002000
ohci_hcd 0000:00:01.3: new USB bus registered, assigned bus number 2
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 3 ports detected
shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
pciehp: acpi_pciehprm:\_SB_.PCI0 evaluate _BBN fail=0x5
pciehp: acpi_pciehprm:get_device PCI ROOT HID fail=0x5
hub 2-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
hub 2-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
```

I have two rear ports and two front ports, and none of them seem to recognize it.
The reader works on my roomate's windows pc so i know the cable's not bad.
Any help with this would be appreciated, and with my hdc errors if you're feeling generous (my dvd drive seems to work fine despite the errors).

---

### Post by WirelessMike on 2006-12-04
Is there some way we can make this a feature request for the next upgrade?  This used to just work.  There was a kernel upgrade back in Dapper from 2.6.15-23 and now it won't seem to work for anyone.

Where can we post this to make it either a feature request or a known bug for Edgy?

Just doesn't seem right for something like autodetection of flash memory cards in a usb card reader to have worked all this time and now it just won't, and all we can seem to associate with the change is a kernel upgrade.

---

### Post by johnmart on 2006-12-08
Sorry, forgot to include url-  [http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/15776-how-mount-usb-flash-drives-linux.html](http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/15776-how-mount-usb-flash-drives-linux.html)

---

### Post by johnmart on 2006-12-08
This is embarrassing, but this goes before the above-
Following the advice in that link worked for me. Not sure what distro it was referring to but my dapper responded with all my files on sd card. btw as a precaution I backed up fstab before making any changes. In the end I put a link on my desktop via rt click/add new device/camera device, choosing sd1 & it worked! Hope it works for you!

---

