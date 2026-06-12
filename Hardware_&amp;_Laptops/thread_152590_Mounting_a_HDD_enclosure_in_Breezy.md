---
title: "Mounting a HDD enclosure in Breezy"
date: 2006-03-30
forum: Hardware &amp; Laptops
---

### Post by Spleenie on 2006-03-30
I have a 2.5" HDD in a USB to IDE enclosure. I am able to mount the drive in XP without drama.

My Breezy system seems to detect the connection of the drive without problems. It appears in System-->Administration-->Disks (although with no information associated with it), in the Device Manager (as a USB 2.0 IDE adaptor) and the following is returned from 'lsusb'

```
:/etc/init.d$ lsusb

Bus 003 Device 001: ID 0000:0000

Bus 002 Device 007: ID 04b4:6830 Cypress Semiconductor Corp. USB-2.0 IDE Adapter

Bus 002 Device 006: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical

Bus 002 Device 005: ID 058f:9254 Alcor Micro Corp. Hub

Bus 002 Device 001: ID 0000:0000

Bus 001 Device 001: ID 0000:0000
```

No variation of sd** seems to work using the following command:

```
sudo mount -t vfat /dev/sd** /media/usbhdd
```

The usb hdd has one fat32 partition.

I have noted a few threads on the subject but nothing definitive. Any help on mounting this drive would be appreciated.

Cheers, S.

---

