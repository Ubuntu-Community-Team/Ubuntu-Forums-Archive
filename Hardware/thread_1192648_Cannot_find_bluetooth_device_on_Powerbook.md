---
title: "Cannot find bluetooth device on Powerbook"
date: 2009-06-20
forum: Hardware
---

### Post by mfleonhardt on 2009-06-20
Hello all,

I've got a 15" PowerBook G4 running xubuntu 9.04.  I cannot seem to find the bluetooth device:

```
root@powerbook:~# dmesg | grep Bluetooth
[   29.485920] Bluetooth: Core ver 2.13
[   29.488355] Bluetooth: HCI device and connection manager initialized
[   29.488360] Bluetooth: HCI socket layer initialized
[   29.566298] Bluetooth: L2CAP ver 2.11
[   29.566304] Bluetooth: L2CAP socket layer initialized
[   29.627019] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   29.627025] Bluetooth: BNEP filters: protocol multicast
[   29.729582] Bluetooth: SCO (Voice Link) ver 0.6
[   29.729587] Bluetooth: SCO socket layer initialized
[   29.761412] Bluetooth: RFCOMM socket layer initialized
[   29.761441] Bluetooth: RFCOMM TTY layer initialized
[   29.761444] Bluetooth: RFCOMM ver 1.10
[   30.738142] Bluetooth: Generic Bluetooth USB driver ver 0.3
root@powerbook:~# lspci
0000:00:0b.0 Host bridge: Apple Computer Inc. Intrepid2 AGP Bridge
0000:00:10.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]
0001:10:0b.0 Host bridge: Apple Computer Inc. Intrepid2 PCI Bridge
0001:10:11.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
0001:10:14.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
0001:10:15.0 USB Controller: NEC Corporation USB (rev 43)
0001:10:15.1 USB Controller: NEC Corporation USB (rev 43)
0001:10:15.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
0001:10:17.0 Class ff00: Apple Computer Inc. KeyLargo/Intrepid Mac I/O
0002:24:0b.0 Host bridge: Apple Computer Inc. Intrepid2 PCI Bridge
0002:24:0d.0 Class ff00: Apple Computer Inc. Intrepid2 ATA/100
0002:24:0e.0 FireWire (IEEE 1394): Apple Computer Inc. Intrepid2 Firewire
0002:24:0f.0 Ethernet controller: Apple Computer Inc. Intrepid2 GMAC (Sun GEM)
root@powerbook:~# hcitool dev
Devices:
root@powerbook:~# hcitool scan
Device is not available: No such device   
root@powerbook:~# hid2hci 
No devices in HID mode found

```

Anybody have any idea what to do here?

Matt

---

