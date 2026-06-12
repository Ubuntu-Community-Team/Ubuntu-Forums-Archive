---
title: "USB PCI card VIA VT6212L too slow"
date: 2011-01-24
forum: Hardware
---

### Post by c.monty on 2011-01-24
Hello!

I'm running a server installation on my old mainboard [Gigabyte GA-7DXR]("http://www.giga-byte.co.za/Products/Motherboard/Products_Spec.aspx?ProductID=1302:"). This board has only USB 1.1 controller onboard and therefore I added USB 2.0 PCI card (with 4+1 USB ports). This card is using chip VIA VT6212L.

I've disabled onboard USB 1.1 controller in BIOS.

As far as I can see the card is identified correctly:
```

root@pc1-eisfair2:~# lspci | grep USB
00:0c.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
00:0c.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
00:0c.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 65)

```

```

root@pc1-eisfair2:~# lspci -vv
00:0c.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62) (prog-if 00 [UHCI])
        Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32, Cache Line Size: 32 bytes
        Interrupt: pin A routed to IRQ 5
        Region 4: I/O ports at b400 [size=32]
        Capabilities: [80] Power Management version 2
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=375mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:0c.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62) (prog-if 00 [UHCI])
        Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32, Cache Line Size: 32 bytes
        Interrupt: pin B routed to IRQ 11
        Region 4: I/O ports at b800 [size=32]
        Capabilities: [80] Power Management version 2
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=375mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:0c.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 65) (prog-if 20 [EHCI])
        Subsystem: VIA Technologies, Inc. USB 2.0
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32, Cache Line Size: 64 bytes
        Interrupt: pin C routed to IRQ 12
        Region 0: Memory at d8021000 (32-bit, non-prefetchable) [size=256]
        Capabilities: [80] Power Management version 2
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=375mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME+

```

Maybe you find this information from dmesg usefull:
```

root@pc1-eisfair2:~# dmesg | grep -i usb
[   45.628038] uhci_hcd: Unknown symbol usb_hcd_pci_suspend
[   45.628117] uhci_hcd: Unknown symbol usb_hcd_resume_root_hub
[   45.628166] uhci_hcd: Unknown symbol usb_hcd_pci_probe
[   45.628217] uhci_hcd: Unknown symbol usb_hcd_unlink_urb_from_ep
[   45.628347] uhci_hcd: Unknown symbol usb_disabled
[   45.628499] uhci_hcd: Unknown symbol usb_hcd_check_unlink_urb
[   45.628582] uhci_hcd: Unknown symbol usb_calc_bus_time
[   45.628694] uhci_hcd: Unknown symbol usb_hcd_link_urb_to_ep
[   45.628746] uhci_hcd: Unknown symbol usb_hcd_pci_resume
[   45.628862] uhci_hcd: Unknown symbol usb_hcd_giveback_urb
[   45.628935] uhci_hcd: Unknown symbol usb_hcd_poll_rh_status
[   45.629028] uhci_hcd: Unknown symbol usb_hcd_pci_remove
[   45.629094] uhci_hcd: Unknown symbol usb_root_hub_lost_power
[   45.631042] ehci_hcd: Unknown symbol usb_hcd_pci_suspend
[   45.631097] ehci_hcd: Unknown symbol usb_free_urb
[   45.631189] ehci_hcd: Unknown symbol usb_hub_tt_clear_buffer
[   45.631239] ehci_hcd: Unknown symbol usb_hcd_resume_root_hub
[   45.631288] ehci_hcd: Unknown symbol usb_hcd_pci_probe
[   45.631339] ehci_hcd: Unknown symbol usb_hcd_unlink_urb_from_ep
[   45.631647] ehci_hcd: Unknown symbol usb_hcd_check_unlink_urb
[   45.631760] ehci_hcd: Unknown symbol usb_calc_bus_time
[   45.631905] ehci_hcd: Unknown symbol usb_hcd_pci_shutdown
[   45.631981] ehci_hcd: Unknown symbol usb_hcd_link_urb_to_ep
[   45.632033] ehci_hcd: Unknown symbol usb_hcd_pci_resume
[   45.632108] ehci_hcd: Unknown symbol usb_get_urb
[   45.632170] ehci_hcd: Unknown symbol usb_hcd_giveback_urb
[   45.632244] ehci_hcd: Unknown symbol usb_hcd_poll_rh_status
[   45.632293] ehci_hcd: Unknown symbol usb_hcd_pci_remove
[   45.632395] ehci_hcd: Unknown symbol usb_root_hub_lost_power
[   45.644582] usbcore: registered new interface driver usbfs
[   45.644627] usbcore: registered new interface driver hub
[   45.655256] usbcore: registered new device driver usb
[   45.687581] USB Universal Host Controller Interface driver v3.0
[   46.372820] uhci_hcd 0000:00:0c.0: new USB bus registered, assigned bus number 1
[   46.373085] usb usb1: configuration #1 chosen from 1 choice
[   46.373129] hub 1-0:1.0: USB hub found
[   46.481248] uhci_hcd 0000:00:0c.1: new USB bus registered, assigned bus number 2
[   46.481471] usb usb2: configuration #1 chosen from 1 choice
[   46.481521] hub 2-0:1.0: USB hub found
[   55.657492] ehci_hcd 0000:00:0c.2: new USB bus registered, assigned bus number 3
[   55.677204] ehci_hcd 0000:00:0c.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   55.677428] usb usb3: configuration #1 chosen from 1 choice
[   55.677480] hub 3-0:1.0: USB hub found
[   99.241776] usb 3-3: new high speed USB device using ehci_hcd and address 2
[   99.394176] usb 3-3: configuration #1 chosen from 1 choice
[   99.484801] usbcore: registered new interface driver libusual
[   99.510959] Initializing USB Mass Storage driver...
[   99.513542] scsi6 : SCSI emulation for USB Mass Storage devices
[   99.515652] usbcore: registered new interface driver usb-storage
[   99.515668] USB Mass Storage support registered.
[   99.516207] usb-storage: device found at 2
[   99.516213] usb-storage: waiting for device to settle before scanning
[  104.510116] usb-storage: device scan complete

```

Maybe the wrong driver (for USB 1.1) is loaded and therefore any device attached to this card slow.
How can I identify which driver is loaded? And if the wrong driver is loaded, how can I replace it?

THX

---

