---
title: "USB drive not recognized (ubuntu 7.04)"
date: 2007-06-05
forum: Hardware &amp; Laptops
---

### Post by Cyclist on 2007-06-05
Hi,

I plugged in a USB drive that I use often under suse. I don't see the drive symbol appear anywhere, nor can I mount it manually with the command:

mount -t ext3 /dev/sda  /mnt/usbbackup

How do I go from here?

TIA

Cyclist

---

### Post by mainalisuyog on 2007-06-05
type in a terminal: sudo tail -f /var/log/messages
plug in the usb drive and paste the output here.

---

### Post by Cyclist on 2007-06-06
Hi,

I tried something I found elsewhere, but it didn't change anything:

sudo modprobe --remove ehci_hcd

Do I have to reload that module (if so, how?) or will it be reloaded next time I boot the system?


tail /var/log/messages
Jun 6 09:32:18 Mars gconfd (derk-5384): Adres "xml:readonly:/etc/gconf/gconf.xml.defaults" getraceerd naar een alleen-lezen configuratiebron op positie 2
Jun 6 09:32:18 Mars gconfd (derk-5384): Adres "xml:readonly:/var/lib/gconf/debian.defaults" getraceerd naar een alleen-lezen configuratiebron op positie 3
Jun 6 09:32:18 Mars gconfd (derk-5384): Adres "xml:readonly:/var/lib/gconf/defaults" getraceerd naar een alleen-lezen configuratiebron op positie 4
Jun 6 09:32:23 Mars kernel: [ 71.536238] cdrom: hdd: mrw address space DMA selected
Jun 6 09:32:23 Mars kernel: [ 71.655450] cdrom: hdd: mrw address space DMA selected
Jun 6 09:32:26 Mars gconfd (derk-5384): Adres "xml:readwrite:/home/derk/.gconf" getraceerd naar een schrijfbare configuratiebron op positie 0
Jun 6 09:35:10 Mars kernel: [ 238.394817] ehci_hcd 0000:00:10.3: remove, state 4
Jun 6 09:35:10 Mars kernel: [ 238.394908] usb usb4: USB disconnect, address 1
Jun 6 09:35:10 Mars kernel: [ 238.397599] ehci_hcd 0000:00:10.3: USB bus 4 deregistered
Jun 6 09:35:10 Mars kernel: [ 238.398123] ACPI: PCI interrupt for device 0000:00:10.3 disabled

Derk

---

