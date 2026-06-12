---
title: "Trying to mount creative zen mp3 on ubuntu"
date: 2015-09-07
forum: Hardware
---

### Post by mikki2 on 2015-09-07
I've just installed ubuntu on my laptop and love it. One minor thing I'd like to get
working is have it mount my ancient mp3 player st I can push/pull songs. I've
installed ntfs-3g and usbmount. 
When I plug in the device on the usb port, sylog sees it:

Sep  6 09:44:56 ubu kernel: [ 4380.963601] usb 1-2: new high-speed USB device number 2 using xhci_hcd
Sep  6 09:44:56 ubu kernel: [ 4381.092397] usb 1-2: New USB device found, idVendor=041e, idProduct=411b
Sep  6 09:44:56 ubu kernel: [ 4381.092400] usb 1-2: New USB device strings: Mfr=1, Product=2, SerialNum
ber=3
Sep  6 09:44:56 ubu kernel: [ 4381.092402] usb 1-2: Product: Creative Zen Touch
Sep  6 09:44:56 ubu kernel: [ 4381.092404] usb 1-2: Manufacturer: Creative Technology
Sep  6 09:44:56 ubu kernel: [ 4381.092405] usb 1-2: SerialNumber: 01012551B703931C
Sep  6 09:44:56 ubu mtp-probe: checking bus 1, device 2: "/sys/devices/pci0000:00/0000:00:14.0/usb1/1-2
"
Sep  6 09:44:56 ubu mtp-probe: bus: 1, device: 2 was not an MTP device

Not sure how to reference the device in a mount command. I would think something like
mount -t ntfs /dev/usb /media/usb1     (having created /media/usb1)   or
ntfs-3g  /dev/usb /media/usb1


Any ideas?

Thanks

---

### Post by coffeecat on 2015-09-07
Duplicate of: [http://ubuntuforums.org/showthread.php?t=2293638](http://ubuntuforums.org/showthread.php?t=2293638)

Please do not create duplicates. Thread closed.

---

