---
title: "Problems with my pendrive."
date: 2008-10-03
forum: Hardware
---

### Post by enriqueaf on 2008-10-03
I am having problems with my pendrive. When I connect it to the computer, It doesn't matter in which OS I connect it or computer, It doesn't work. I have tried also connecting an other pendrives in my computer, and all of them works with out any problem, also pendrives of the same brand. My pendrive is:

*Kingston Data Traveler - 4GB*

Finally I was looking for the solution in internet but I can't find anything.

When I type *"dmesg | tail"* after plug it in appears:
```
$ dmesg | tail
[ 2656.406261] usb 5-5: new high speed USB device using ehci_hcd and address 106
[ 2657.293722] usb 5-5: new high speed USB device using ehci_hcd and address 110
[ 2658.808797] usb 5-5: new high speed USB device using ehci_hcd and address 117
[ 2659.485375] usb 5-5: new high speed USB device using ehci_hcd and address 120
[ 2661.167409] usb 5-5: new high speed USB device using ehci_hcd and address 2
[ 2662.282676] usb 5-5: new high speed USB device using ehci_hcd and address 7
[ 2662.979346] usb 5-5: new high speed USB device using ehci_hcd and address 10
[ 2663.278085] usb 5-5: new high speed USB device using ehci_hcd and address 11
[ 2663.577898] usb 5-5: new high speed USB device using ehci_hcd and address 12
[ 2663.878704] usb 5-5: new high speed USB device using ehci_hcd and address 13
```

Each time that I enter it, always appear the same like an infinitive bucle. I have tried unplugin the pendrive and removing the module "ehci_hcd" with:

```
$ sudo modprobe -r ehci_hcd
```

After I plug the pendrive again It doesn't work, And I type again:

```
$ dmesg | tail
[  132.696457] usb 5-3: new high speed USB device using ehci_hcd and address 31
[  132.802416] usb 5-3: new high speed USB device using ehci_hcd and address 34
[  133.008517] usb 5-3: new high speed USB device using ehci_hcd and address 37
[  133.125640] usb 5-3: new high speed USB device using ehci_hcd and address 40
[  133.229013] usb 5-3: new high speed USB device using ehci_hcd and address 42
[  133.315554] usb 5-3: new high speed USB device using ehci_hcd and address 43
[  137.787096] ehci_hcd 0000:00:1d.7: remove, state 4
[  137.787110] usb usb5: USB disconnect, address 1
[  137.791350] ehci_hcd 0000:00:1d.7: USB bus 5 deregistered
[  137.791405] ACPI: PCI interrupt for device 0000:00:1d.7 disabled

```

In both cases: with the module active and desactivated I type "lsusb" after plug in the pendrive and this is the output:

```
$ lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000
```

My hardware is:

```
$ lscpi
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc M56P [Radeon Mobility X1600]
03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller (rev 10)
04:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
06:04.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
```

It stopped of working after pass an antivirus over it in a computer with windows installed in it, I don't remenber of unplug it without unmount it before.

If you have any idea of what It is happening I will be very gratefull of reading it.

Thank you very much.
Enrique

P.D: If you can't understand something asked me because my english it is *not* perfect.

---

### Post by sombraGuerrero on 2008-10-03
Hello, this is bobertdos from the #ubuntu.
A quicker way to find the Windows partitioner: Start->Run and type diskmgmt.msc

---

### Post by enriqueaf on 2008-10-03
Thank you for the information bobertdos, but when launch the application, it only shows the information of my main hard disk and **not** about the pendrive.

Do you have any other idea??

Thank you very much
Enriqueaf

---

