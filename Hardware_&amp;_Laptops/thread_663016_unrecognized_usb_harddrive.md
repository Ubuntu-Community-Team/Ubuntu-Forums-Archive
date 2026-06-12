---
title: "unrecognized usb harddrive"
date: 2008-01-09
forum: Hardware &amp; Laptops
---

### Post by kylebaked on 2008-01-09
i've had my external hard drive for a while and it was mounting fine, but it suddenly stopped. demsg gives me following output:

[HTML]Jan  9 17:28:18 kylebaked kernel: [21139.656000] usb 5-5: new high speed USB device using ehci_hcd and address 2
Jan  9 17:28:18 kylebaked kernel: [21139.788000] usb 5-5: configuration #1 chosen from 1 choice
Jan  9 17:28:19 kylebaked kernel: [21140.036000] usbcore: registered new interface driver libusual
Jan  9 17:28:19 kylebaked kernel: [21140.068000] Initializing USB Mass Storage driver...
Jan  9 17:28:19 kylebaked kernel: [21140.068000] scsi2 : SCSI emulation for USB Mass Storage devices
Jan  9 17:28:19 kylebaked kernel: [21140.068000] usbcore: registered new interface driver usb-storage
Jan  9 17:28:19 kylebaked kernel: [21140.068000] USB Mass Storage support registered.
Jan  9 17:28:29 kylebaked kernel: [21150.680000] usb 5-5: reset high speed USB device using ehci_hcd and address 2
Jan  9 17:28:35 kylebaked kernel: [21156.424000] usb 5-5: reset high speed USB device using ehci_hcd and address 2
Jan  9 17:28:41 kylebaked kernel: [21162.168000] usb 5-5: reset high speed USB device using ehci_hcd and address 2
Jan  9 17:28:46 kylebaked kernel: [21167.912000] usb 5-5: reset high speed USB device using ehci_hcd and address 2[/HTML]

it will keep repeating the last few lines untill it eventually stops. the same thing happens when i replug it in. it doesn't mount by itself, and i don't know how to do it manually since its not recognized. has anyone had this problem before?

---

### Post by jmiguel77 on 2008-01-09
hi

i am having the same problem with ubuntu 7.10
what i am doing (for now) is to unload the ehci_hcd module from the kernel

sudo modprobe -r ehci_hcd

and then unplug / plug the drive again

the problem is that ehci_hcd is the module for USB 2.0 devices, so the plugged devices are read/write at USB 1.0 speed (wich is considerably lower)

the bottom line is... is there any fix for that module ???

hope it helps

---

### Post by kylebaked on 2008-01-12
what is weird is that it was working just fine for the longest time, but recently quit working. what could have happened to cause this?

---

### Post by kylebaked on 2008-01-12
I tried doing what you said, but it still will not allow me to access my drive. dmesg gives me the following similiar (but different) message :
> [  380.972000] usb 4-1: new full speed USB device using uhci_hcd and address 3
[  381.132000] usb 4-1: configuration #1 chosen from 1 choice
[  381.136000] scsi4 : SCSI emulation for USB Mass Storage devices
[  381.136000] usb-storage: device found at 3
[  381.136000] usb-storage: waiting for device to settle before scanning
[  386.136000] usb-storage: device scan complete
[  391.748000] usb 4-1: reset full speed USB device using uhci_hcd and address 3
[  397.508000] usb 4-1: reset full speed USB device using uhci_hcd and address 3
[  403.268000] usb 4-1: reset full speed USB device using uhci_hcd and address 3
[  409.028000] usb 4-1: reset full speed USB device using uhci_hcd and address 3


it appears to be recognizing the device as a usb-storage device, but for some reason i cannot access it

---

