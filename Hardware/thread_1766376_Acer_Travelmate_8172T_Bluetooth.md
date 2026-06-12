---
title: "Acer Travelmate 8172T Bluetooth"
date: 2011-05-24
forum: Hardware
---

### Post by P_Squiddy on 2011-05-24
I have an Acer Travelmate 8172T, which has a Broadcom Wifi/Bluetooth NIC in it that toggles by way of a softkey (no physical switch).  The wireless "just works" but Bluetooth doesn't seem to quite connect.  In 10.04.2 it seems to work when you toggle between the two modes.  In 10.10, the Bluetooth icon appears in the tray when toggled but the device driver doesn't appear to actually load and never allows the service to become active.

The related component (from lspci) seems to be:

```
01:00.0 Network controller: Broadcom Corporation BCM43225 802.11b/g/n (rev 01)
    Subsystem: Foxconn International, Inc. Device e021
    Kernel driver in use: wl
    Kernel modules: wl
```After toggling Bluetooth on, I get this from dmesg:

```
[   59.538625] usb 1-1.3: new full speed USB device using ehci_hcd and address 4
[   59.689303] Bluetooth: Core ver 2.15
[   59.689341] NET: Registered protocol family 31
[   59.689345] Bluetooth: HCI device and connection manager initialized
[   59.689351] Bluetooth: HCI socket layer initialized
[   59.703823] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   59.707189] usbcore: registered new interface driver btusb
[   59.733929] Bluetooth: L2CAP ver 2.14
[   59.733934] Bluetooth: L2CAP socket layer initialized
[   59.742942] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   59.742949] Bluetooth: BNEP filters: protocol multicast
[   59.750248] Bluetooth: SCO (Voice Link) ver 0.6
[   59.750253] Bluetooth: SCO socket layer initialized
```Related modules appear to be:

```
Module                  Size  Used by
sco                     7998  2 
bnep                    9542  2 
l2cap                  37008  3 bnep
btusb                  11001  2 
bluetooth              50500  10 sco,bnep,l2cap,btusb
```Has anyone else experienced this issue and any thoughts on fixing it?

---

