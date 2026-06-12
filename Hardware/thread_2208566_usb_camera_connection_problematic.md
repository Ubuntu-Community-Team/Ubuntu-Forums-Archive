---
title: "usb camera connection problematic"
date: 2014-03-01
forum: Hardware
---

### Post by ksadil2 on 2014-03-01
Hi,

I have just come back from the dark side installing Ubuntu after wiping mint off my system. And I am having difficulty mounting usb connected cameras to my system. The camera does not connect and fdisk -l responds with[INDENT]Partition table entries are not in disk order

Disk /dev/sdc: 8018 MB, 8018460672 bytes
247 heads, 62 sectors/track, 1022 cylinders, total 15661056 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table
[/INDENT]

And gparted cannot seem to install a partition table either. I can get the files using a card reader fine, but the usb cable works on osx. 

This is a fresh install and the same thing was happening on mint. Any assistance or ideas would be appreciated?

---

### Post by mörgæs on 2014-03-02
Hi, welcome to the fora.

Which camera and which version of Ubuntu?

---

### Post by ksadil2 on 2014-03-02
The cameras are the mobius action cam and the 808 keychain cameras. The mobius is new but the 808's have worked for years. My Ubuntu installation is 13.10 64 bit desktop

---

### Post by mörgæs on 2014-03-02
Please also post the output from **lsusb** in CODE tags.

---

### Post by ksadil2 on 2014-03-02
```
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 0603:1001 Novatek Microelectronics Corp. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

it is the novatek entry

---

### Post by mörgæs on 2014-03-03
Sorry, I don't know how to deal with this one and Google does not give many hints.

---

### Post by ksadil2 on 2014-03-04
cool, thanks for trying

---

