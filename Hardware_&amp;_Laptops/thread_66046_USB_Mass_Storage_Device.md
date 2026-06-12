---
title: "USB Mass Storage Device"
date: 2005-09-15
forum: Hardware &amp; Laptops
---

### Post by mzhang on 2005-09-15
root@ubuntu:/home/ming# modprobe usb-storage

root@ubuntu:/home/ming# mount -t vfat /dev/sda1 /mnt/sda1
mount: special device /dev/sda1 does not exist

root@ubuntu:/home/ming# mount -t vfat /dev/sdb1 /mnt/sda1
mount: special device /dev/sdb1 does not exist

root@ubuntu:/home/ming# dmesg|grep usb
[4294671.654000] usbcore: registered new driver usbfs
[4294671.654000] usbcore: registered new driver hub
[4294672.702000] usb 2-1: new full speed USB device using uhci_hcd and address 2[4294672.775000] usb 2-1: device descriptor read/64, error -71
[4294672.948000] usb 2-1: device descriptor read/64, error -71
[4294673.111000] usb 2-1: new full speed USB device using uhci_hcd and address 3[4294673.184000] usb 2-1: device descriptor read/64, error -71
[4294673.358000] usb 2-1: device descriptor read/64, error -71
[4294673.521000] usb 2-1: new full speed USB device using uhci_hcd and address 4[4294673.929000] usb 2-1: device not accepting address 4, error -71
[4294673.991000] usb 2-1: new full speed USB device using uhci_hcd and address 5[4294674.489000] usb 2-1: device not accepting address 5, error -71
[4294703.968000] usbcore: registered new driver usb-storage
[4297937.140000] usb 1-2: new full speed USB device using uhci_hcd and address 2[4297937.217000] usb 1-2: device descriptor read/64, error -71
[4297937.391000] usb 1-2: device descriptor read/64, error -71
[4297937.559000] usb 1-2: new full speed USB device using uhci_hcd and address 3[4297937.646000] usb 1-2: device descriptor read/64, error -71
[4297937.820000] usb 1-2: device descriptor read/64, error -71
[4297937.988000] usb 1-2: new full speed USB device using uhci_hcd and address 4[4297938.396000] usb 1-2: device not accepting address 4, error -71
[4297938.458000] usb 1-2: new full speed USB device using uhci_hcd and address 5[4297938.869000] usb 1-2: device not accepting address 5, error -71



If anyone hasn't figured it out, I can't seem to get a mass storage device to be mounted on "Linux ubuntu 2.6.12-8-386 #1 Tue Aug 30 22:41:30 BST 2005 i686 GNU/Linux", which is the new "Breezy". Can I possibly make the drive work without a recompile?

---

