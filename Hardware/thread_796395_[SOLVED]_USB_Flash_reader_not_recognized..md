---
title: "[SOLVED] USB Flash reader not recognized."
date: 2008-05-16
forum: Hardware
---

### Post by picopir8 on 2008-05-16
My USB flash card reader recently stopped working on my computer.  I works on other computers (both windows and linux) so there is nothing wrong with the reader.  Also, I also have a USB hard drive which still works with my computer, so my USB ports/drivers seem to be functional.  Any ideas of what could be going wrong?

Below is the output of "dmesg | tail -n 50"
```

[   23.784000] ACPI: Video Device [C098] (multi-head: yes  rom: no  post: no)
[   23.868000] wmi_add device=c1a4c800
[   23.868000] calling WQBA
[   23.880000] pcc_acpi: loading...
[   29.244000] ppdev: user-space parallel port driver
[   30.200000] apm: BIOS not found.
[   30.932000] ip_tables: (C) 2000-2006 Netfilter Core Team
[   31.036000] [drm] Initialized drm 1.1.0 20060810
[   31.040000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   31.040000] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   31.096000] Netfilter messages via NETLINK v0.30.
[   31.104000] nf_conntrack version 0.5.0 (8125 buckets, 65000 max)
[   33.716000] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   33.716000] vboxdrv: Successfully done.
[   33.716000] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   33.716000] vboxdrv: Successfully loaded version 1.5.6 (interface 0x00050002).
[   34.332000] Bluetooth: Core ver 2.11
[   34.332000] NET: Registered protocol family 31
[   34.332000] Bluetooth: HCI device and connection manager initialized
[   34.332000] Bluetooth: HCI socket layer initialized
[   34.404000] Bluetooth: L2CAP ver 2.8
[   34.404000] Bluetooth: L2CAP socket layer initialized
[   34.628000] Bluetooth: RFCOMM socket layer initialized
[   34.628000] Bluetooth: RFCOMM TTY layer initialized
[   34.628000] Bluetooth: RFCOMM ver 1.8
[   41.552000] eth0: no IPv6 routers present
[  165.380000] usb 7-1: new high speed USB device using ehci_hcd and address 3
[  165.884000] usb 7-1: new high speed USB device using ehci_hcd and address 4
[  166.388000] usb 7-1: new high speed USB device using ehci_hcd and address 5
[  167.144000] usb 7-1: new high speed USB device using ehci_hcd and address 6
[  167.648000] usb 7-1: new high speed USB device using ehci_hcd and address 7
[  168.152000] usb 7-1: new high speed USB device using ehci_hcd and address 8
[  169.160000] usb 7-1: new high speed USB device using ehci_hcd and address 10
[  171.176000] usb 7-1: new high speed USB device using ehci_hcd and address 14
[  171.932000] usb 7-1: new high speed USB device using ehci_hcd and address 16
[  172.940000] usb 7-1: new high speed USB device using ehci_hcd and address 18
[  173.696000] usb 7-1: new high speed USB device using ehci_hcd and address 20
[  174.568000] hub 7-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[  174.956000] usb 7-1: new high speed USB device using ehci_hcd and address 22
[  176.216000] usb 7-1: new high speed USB device using ehci_hcd and address 23
[  177.476000] usb 7-1: new high speed USB device using ehci_hcd and address 25
[  178.988000] usb 7-1: new high speed USB device using ehci_hcd and address 27
[  179.492000] usb 7-1: new high speed USB device using ehci_hcd and address 28
[  180.364000] hub 7-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[  180.476000] usb 7-1: new high speed USB device using ehci_hcd and address 29
[  181.348000] hub 7-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[  181.460000] usb 7-1: new high speed USB device using ehci_hcd and address 30
[  181.868000] usb 7-1: device not accepting address 30, error -71
[  181.980000] usb 7-1: new high speed USB device using ehci_hcd and address 31
[  182.388000] usb 7-1: device not accepting address 31, error -71

```

Also, here is the output of "lsusb"
```
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 004: ID 08ff:2580 AuthenTec, Inc. 
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

```

---

### Post by nicedude on 2008-05-16
Did this device ever work in your current system and setup & if it did have you done any major upgrades since then? i.e. Gutsy to Hardy etc. 

I see the following errors in your list

[  174.568000] hub 7-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[  180.364000] hub 7-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[  181.348000] hub 7-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[  182.388000] usb 7-1: device not accepting address 31, error -71

I assume this is not your USB reader as it seems to be on bus 3 and the errors are on bus 7 it looks like, am I wrong?
Bus 003 Device 004: ID 08ff:2580 AuthenTec, Inc. 

Here is a command to update your lsusb device list with the newest one
sudo update-usbids
you might try doing that then reposting the new results here along with the model of reader in question.

Also you should try plugging it into a different usb port preferably on a different controller i.e. if in a front usb slot now plug it into a slot on the back.

---

### Post by picopir8 on 2008-05-16
Well I had two card readers, the first one died, so I took this one off another computer.  I do not know if it worked with this computer.  However, shortly after I made my first post, I removed the card reader and it was burning hot (even melted some of the plastic housing).  So my guess is it is a hardware problem with my computer USB ports (or at least it is now!). however its strange since my USB hard drive still works, though I am not connecting it again because I do not want to risk frying any more hardware.

---

