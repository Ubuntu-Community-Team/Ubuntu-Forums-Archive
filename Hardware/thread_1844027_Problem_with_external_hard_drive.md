---
title: "Problem with external hard drive"
date: 2011-09-14
forum: Hardware
---

### Post by Xanfer on 2011-09-14
Hi! I have a problem with connecting external TRANSCEND StoreJet 25H2P 1tb to my system. When it is connected before powering on the computer - it works fine, but once it was unplugged and plugged again - it is not recognised by the system on new connection.

/var/log/messages:
```

Sep 14 19:01:23 acer kernel: [ 3243.464645] usb 1-1.2: new high speed USB device number 6 using ehci_hcd
Sep 14 19:01:23 acer kernel: [ 3243.558604] usb 1-1.2: New USB device found, idVendor=152d, idProduct=2329
Sep 14 19:01:23 acer kernel: [ 3243.558611] usb 1-1.2: New USB device strings: Mfr=1, Product=11, SerialNumber=5
Sep 14 19:01:23 acer kernel: [ 3243.558616] usb 1-1.2: Product: StoreJet Transcend
Sep 14 19:01:23 acer kernel: [ 3243.558619] usb 1-1.2: Manufacturer: JMicron
Sep 14 19:01:23 acer kernel: [ 3243.558623] usb 1-1.2: SerialNumber: WD5WXA1A6163812
Sep 14 19:01:23 acer kernel: [ 3243.559337] scsi5 : usb-storage 1-1.2:1.0
Sep 14 19:01:23 acer mtp-probe: checking bus 1, device 6: "/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2"
Sep 14 19:01:23 acer mtp-probe: bus: 1, device: 6 was not an MTP device

```

and dmesg
```

[ 3243.464645] usb 1-1.2: new high speed USB device number 6 using ehci_hcd
[ 3243.558604] usb 1-1.2: New USB device found, idVendor=152d, idProduct=2329
[ 3243.558611] usb 1-1.2: New USB device strings: Mfr=1, Product=11, SerialNumber=5
[ 3243.558616] usb 1-1.2: Product: StoreJet Transcend
[ 3243.558619] usb 1-1.2: Manufacturer: JMicron
[ 3243.558623] usb 1-1.2: SerialNumber: WD5WXA1A6163812
[ 3243.559337] scsi5 : usb-storage 1-1.2:1.0

```

OS: Ubuntu 11.04 and Debian Wheezy

---

### Post by Xanfer on 2011-09-16
No One has any ideas? :(

---

