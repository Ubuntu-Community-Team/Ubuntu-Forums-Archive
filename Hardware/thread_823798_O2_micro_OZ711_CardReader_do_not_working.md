---
title: "O2 micro OZ711 CardReader do not working"
date: 2008-06-09
forum: Hardware
---

### Post by ravensun on 2008-06-09
Hello 
I have some problem.
My Laptop MSI M655 with ubuntu 8.04 and internal card reader o2 micro OZ711 do not working when i put any type of multimedia flash cards to cardreader.
I have this lspci, lsusb, uname -r, dmesg | grep -i usb statements:
lspci:[   33.515760] usbcore: registered new interface driver usbfs
[   33.515785] usbcore: registered new interface driver hub
[   33.522981] usbcore: registered new device driver usb
[   33.532829] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   33.533281] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[   33.590998] usb usb1: configuration #1 chosen from 1 choice
[   33.591021] hub 1-0:1.0: USB hub found
[   33.695211] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[   33.754813] usb usb2: configuration #1 chosen from 1 choice
[   33.754836] hub 2-0:1.0: USB hub found
[   33.859168] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[   33.870496] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   33.870602] usb usb3: configuration #1 chosen from 1 choice
[   33.870623] hub 3-0:1.0: USB hub found
[  310.159411] usb 1-1: new low speed USB device using ohci_hcd and address 2
[  310.242247] usb 1-1: configuration #1 chosen from 1 choice
[  310.339590] usbcore: registered new interface driver hiddev
[  310.341799] input: Genius Optical Mouse as /devices/pci0000:00/0000:00:13.0/usb1/1-1/1-1:1.0/input/input9
[  310.351192] input,hidraw0: USB HID v1.10 Mouse [Genius Optical Mouse] on usb-0000:00:13.0-1
[  310.353988] usbcore: registered new interface driver usbhid
[  310.353993] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[  561.087856] usb 3-6: new high speed USB device using ehci_hcd and address 3
[  561.141593] usb 3-6: configuration #1 chosen from 1 choice
[  561.232758] usbcore: registered new interface driver libusual
[  561.276302] Initializing USB Mass Storage driver...
[  561.277413] scsi2 : SCSI emulation for USB Mass Storage devices
[  561.278379] usbcore: registered new interface driver usb-storage
[  561.278759] USB Mass Storage support registered.
[  561.279116] usb-storage: device found at 3
[  561.279119] usb-storage: waiting for device to settle before scanning
[  563.275597] usb-storage: device scan complete
[  810.756824] usb 3-6: USB disconnect, address 3
[  810.854151] usb 3-6: new high speed USB device using ehci_hcd and address 4
[  817.650338] usb 1-2: new full speed USB device using ohci_hcd and address 3
[  817.743928] usb 1-2: configuration #1 chosen from 1 choice
[  817.955765] Bluetooth: HCI USB driver ver 2.9
[  817.956944] usbcore: registered new interface driver hci_usb
[  824.807011] usb 1-2: USB disconnect, address 3
[ 1810.997886] usb 1-2: new full speed USB device using ohci_hcd and address 4
[ 1811.091631] usb 1-2: configuration #1 chosen from 1 choice
[ 1811.390959] usb 1-2: USB disconnect, address 4
[ 1839.700368] usb 3-6: new high speed USB device using ehci_hcd and address 7
[ 1839.813678] usb 3-6: configuration #1 chosen from 1 choice
[ 1840.046753] usbcore: registered new interface driver rt73usb
[ 1840.072919] usbcore: registered new interface driver rt2500usb

00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
00:02.0 PCI bridge: ATI Technologies Inc RS480 PCI-X Root Port
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc M56P [Radeon Mobility X1600]
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
05:04.0 CardBus bridge: O2 Micro, Inc. OZ711MP1/MS1 MemoryCardBus Controller (rev 21)
05:04.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 01)
05:04.3 Bridge: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)
05:04.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
05:09.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)

lsusb:
Bus 003 Device 007: ID 148f:2573 Ralink Technology, Corp. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 0458:003a KYE Systems Corp. (Mouse Systems) 
Bus 001 Device 001: ID 0000:0000  

uname -r:
2.6.24-16-generic

dmesg | grep -i usb:
[   33.515760] usbcore: registered new interface driver usbfs
[   33.515785] usbcore: registered new interface driver hub
[   33.522981] usbcore: registered new device driver usb
[   33.532829] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   33.533281] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[   33.590998] usb usb1: configuration #1 chosen from 1 choice
[   33.591021] hub 1-0:1.0: USB hub found
[   33.695211] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[   33.754813] usb usb2: configuration #1 chosen from 1 choice
[   33.754836] hub 2-0:1.0: USB hub found
[   33.859168] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[   33.870496] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   33.870602] usb usb3: configuration #1 chosen from 1 choice
[   33.870623] hub 3-0:1.0: USB hub found
[  310.159411] usb 1-1: new low speed USB device using ohci_hcd and address 2
[  310.242247] usb 1-1: configuration #1 chosen from 1 choice
[  310.339590] usbcore: registered new interface driver hiddev
[  310.341799] input: Genius Optical Mouse as /devices/pci0000:00/0000:00:13.0/usb1/1-1/1-1:1.0/input/input9
[  310.351192] input,hidraw0: USB HID v1.10 Mouse [Genius Optical Mouse] on usb-0000:00:13.0-1
[  310.353988] usbcore: registered new interface driver usbhid
[  310.353993] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[  561.087856] usb 3-6: new high speed USB device using ehci_hcd and address 3
[  561.141593] usb 3-6: configuration #1 chosen from 1 choice
[  561.232758] usbcore: registered new interface driver libusual
[  561.276302] Initializing USB Mass Storage driver...
[  561.277413] scsi2 : SCSI emulation for USB Mass Storage devices
[  561.278379] usbcore: registered new interface driver usb-storage
[  561.278759] USB Mass Storage support registered.
[  561.279116] usb-storage: device found at 3
[  561.279119] usb-storage: waiting for device to settle before scanning
[  563.275597] usb-storage: device scan complete
[  810.756824] usb 3-6: USB disconnect, address 3
[  810.854151] usb 3-6: new high speed USB device using ehci_hcd and address 4
[  817.650338] usb 1-2: new full speed USB device using ohci_hcd and address 3
[  817.743928] usb 1-2: configuration #1 chosen from 1 choice
[  817.955765] Bluetooth: HCI USB driver ver 2.9
[  817.956944] usbcore: registered new interface driver hci_usb
[  824.807011] usb 1-2: USB disconnect, address 3
[ 1810.997886] usb 1-2: new full speed USB device using ohci_hcd and address 4
[ 1811.091631] usb 1-2: configuration #1 chosen from 1 choice
[ 1811.390959] usb 1-2: USB disconnect, address 4
[ 1839.700368] usb 3-6: new high speed USB device using ehci_hcd and address 7
[ 1839.813678] usb 3-6: configuration #1 chosen from 1 choice
[ 1840.046753] usbcore: registered new interface driver rt73usb
[ 1840.072919] usbcore: registered new interface driver rt2500usb

Thanks for any advice. Johnnys

---

### Post by Miraculix on 2009-11-19
There are still no linux kernel drivers available for the 
integrated O2 Micro MS/xD Controller [1217:7130], as far 
as I know.  Unfortunately.

However, what about the idea to use some of the m$ windows 
xp drivers, e.g. system32/o2media.sys, system32/o2sd.sys, 
via 'wine'?  

Not that I have ever read or heard of someone successfully
tried this yet, but hey, these are just my 2p on this.

Hence, any hints are greatly appreciated!!!

---

