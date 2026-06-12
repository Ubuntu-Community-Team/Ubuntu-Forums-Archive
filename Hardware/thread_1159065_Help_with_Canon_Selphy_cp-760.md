---
title: "Help with Canon Selphy cp-760"
date: 2009-05-14
forum: Hardware
---

### Post by Domas on 2009-05-14
Hi all,

Few days ago I got photo printer cp760, till now I am trying to make it work on Ubuntu 9.04, but no chance...I have tried Gutenprint, opengutenprint drivers, non of them works. I only manage to start printer and take the sheet in the middle and then it just hangs. Anyone managed to make it work? I would appreciate any help.

Here are some logs after I turn on the printer:

debug:

May 13 11:53:50 connection hal_lpadmin: Running hal_lpadmin
May 13 11:53:51 connection hal_lpadmin: hal_lpadmin triggered by low-level USB device
May 13 11:53:51 connection hal_lpadmin: Getting device ID from the usblp HAL entry ...
May 13 11:53:52 connection hal_lpadmin: Device ID for /dev/usb/lp0: MFG:Canon;MDL:CP760;DES:Canon CP760;CMD:Raster3;
May 13 11:53:52 connection hal_lpadmin: Written device ID into HAL database entry: MFG:Canon;MDL:CP760;DES:Canon CP760;CMD:Raster3;
May 13 11:53:52 connection hal_lpadmin: add
May 13 11:53:52 connection hal_lpadmin: Printer reported by HAL: Canon CP760 GO08082800006884
May 13 11:53:52 connection hal_lpadmin: URIs: ['usb://Canon/CP760', 'hal:///org/freedesktop/Hal/devices/usb_device_4a9_31ab_GO08082800006884_if0_printer_noserial']
May 13 11:53:52 connection hal_lpadmin: HPLIP Fax URIs: None
May 13 11:53:52 connection hal_lpadmin: Calling GetReady
May 13 11:53:52 connection hal_lpadmin: D-Bus method call failed: org.freedesktop.DBus.Error.ServiceUnknown: The name com.redhat.NewPrinterNotification was not provided by any .service files
May 13 11:54:14 connection hal_lpadmin: Device ID: MFG:Canon;MDL:CP760;DES:Canon CP760;CMD:Raster3; URI:usb://Canon/CP760
May 13 11:54:18 connection hal_lpadmin: PPD: lsb/usr/cups-included/textonly.ppd; Status: 3

daemon.log:

May 13 11:53:50 connection hal_lpadmin: Running hal_lpadmin
May 13 11:53:51 connection hal_lpadmin: hal_lpadmin triggered by low-level USB device
May 13 11:53:51 connection hal_lpadmin: Getting device ID from the usblp HAL entry ...
May 13 11:53:52 connection hal_lpadmin: Device ID for /dev/usb/lp0: MFG:Canon;MDL:CP760;DES:Canon CP760;CMD:Raster3;
May 13 11:53:52 connection hal_lpadmin: Written device ID into HAL database entry: MFG:Canon;MDL:CP760;DES:Canon CP760;CMD:Raster3;
May 13 11:53:52 connection hal_lpadmin: add
May 13 11:53:52 connection hal_lpadmin: Printer reported by HAL: Canon CP760 GO08082800006884
May 13 11:53:52 connection hal_lpadmin: URIs: ['usb://Canon/CP760', 'hal:///org/freedesktop/Hal/devices/usb_device_4a9_31ab_GO08082800006884_if0_printer_noserial']
May 13 11:53:52 connection hal_lpadmin: HPLIP Fax URIs: None
May 13 11:53:52 connection hal_lpadmin: Calling GetReady
May 13 11:53:52 connection hal_lpadmin: D-Bus method call failed: org.freedesktop.DBus.Error.ServiceUnknown: The name com.redhat.NewPrinterNotification was not provided by any .service files
May 13 11:54:14 connection hal_lpadmin: Device ID: MFG:Canon;MDL:CP760;DES:Canon CP760;CMD:Raster3; URI:usb://Canon/CP760
May 13 11:54:18 connection hal_lpadmin: PPD: lsb/usr/cups-included/textonly.ppd; Status: 3
May 13 11:54:18 connection hal_lpadmin: Did not add printer with URI usb://Canon/CP760, no exact model fit found

kern.log:

May 13 11:53:49 connection kernel: [  447.440052] usb 2-2: new full speed USB device using uhci_hcd and address 2
May 13 11:53:50 connection kernel: [  447.626887] usb 2-2: configuration #1 chosen from 1 choice
May 13 11:53:50 connection kernel: [  447.720812] usblp0: USB Bidirectional printer dev 2 if 0 alt 0 proto 2 vid 0x04A9 pid 0x31AB
May 13 11:53:50 connection kernel: [  447.720837] usbcore: registered new interface driver usblp

Regards,

Dom

---

### Post by manuw on 2009-08-04
Hi Dom,

Had to live with the same problem for ages (hence using Virtualbox+XP) until I found out that...IT WORKS 100% using the Gutenprint "Selphy-CP520" driver -as suggested somewhere on the gutenprint sourceforge forum- !
Works fine with Ubuntu Jaunty & latest gutenprint (5.2.4) compiled from source.
Have no idea whether this works with the regular jaunty gutenprint package though.
bye,

Manu

---

