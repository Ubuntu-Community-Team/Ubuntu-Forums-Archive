---
title: "NTFS partitioned USB drive"
date: 2009-01-05
forum: Hardware
---

### Post by kumarnarain on 2009-01-05
Hai
I have an NTFS partitioned USB drive that just refuses to mount...I am pasting the response of tail -f /var/log/messages
*****************************************************************

Jan  4 22:43:38 kumarHome kernel: [ 3163.475825] usb 1-1.4: new full speed USB device using uhci_hcd and address 6
Jan  4 22:43:42 kumarHome kernel: [ 3167.882462] usb 1-1.4: not running at top speed; connect to a high speed hub
Jan  4 22:43:43 kumarHome kernel: [ 3167.905587] usb 1-1.4: configuration #1 chosen from 1 choice
Jan  4 22:43:43 kumarHome kernel: [ 3168.017670] usbcore: registered new interface driver libusual
Jan  4 22:43:43 kumarHome kernel: [ 3168.044255] Initializing USB Mass Storage driver...
Jan  4 22:43:43 kumarHome kernel: [ 3168.044496] scsi4 : SCSI emulation for USB Mass Storage devices
Jan  4 22:43:43 kumarHome kernel: [ 3168.044662] usbcore: registered new interface driver usb-storage
Jan  4 22:43:43 kumarHome kernel: [ 3168.044666] USB Mass Storage support registered.
Jan  4 22:43:53 kumarHome kernel: [ 3178.605854] usb 1-1.4: reset full speed USB device using uhci_hcd and address 6
Jan  4 22:44:08 kumarHome kernel: [ 3193.083530] usb 1-1.4: reset full speed USB device using uhci_hcd and address 6
Jan  4 22:44:28 kumarHome kernel: [ 3213.547278] usb 1-1.4: reset full speed USB device using uhci_hcd and address 6
Jan  4 22:44:33 kumarHome kernel: [ 3218.031842] usb 1-1.4: reset full speed USB device using uhci_hcd and address 6
Jan  4 22:44:47 kumarHome kernel: [ 3232.500519] usb 1-1.4: reset full speed USB device using uhci_hcd and address 6
Jan  4 22:44:52 kumarHome kernel: [ 3236.913162] scsi 4:0:0:0: Device offlined - not ready after error recovery

*****************************************************************

Any ideas??

Kumar

---

### Post by kumarnarain on 2009-01-05
EDIT

Ok I have ntfs-3g installed and I am converstant with its command line.......but here I dont see any sda or sdb against the disk. Other usb drives with ntfs mount on plugging instantly. Strangely this USB drive connects to my laptop instantly

---

