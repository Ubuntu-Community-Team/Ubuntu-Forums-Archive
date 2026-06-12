---
title: "internal USB card reader not working"
date: 2008-05-12
forum: Hardware
---

### Post by Haf on 2008-05-12
Hello I have a problem with a USB card reader that I've added to my desktop PC, it is connected internally with the mainboard and got several drives for different memory cards. In Windows, the device is working flawlessly.
In Ubuntu Hardy, the LED of the device is flashing all the time and the message log is filled with these messages:
```
[ 2006.422187] usb 1-10: new high speed USB device using ehci_hcd and address 8
[ 2006.749703] usb 1-10: new high speed USB device using ehci_hcd and address 9
[ 2007.078226] usb 1-10: new high speed USB device using ehci_hcd and address 11
[ 2007.404894] usb 1-10: new high speed USB device using ehci_hcd and address 12
[ 2007.732273] usb 1-10: new high speed USB device using ehci_hcd and address 13
[ 2008.059796] usb 1-10: new high speed USB device using ehci_hcd and address 14
[ 2008.388305] usb 1-10: new high speed USB device using ehci_hcd and address 15
[ 2008.715825] usb 1-10: new high speed USB device using ehci_hcd and address 16
[ 2009.043339] usb 1-10: new high speed USB device using ehci_hcd and address 17
[ 2009.370859] usb 1-10: new high speed USB device using ehci_hcd and address 18
```

This goes from address 1 to 127, after that it starts again from address 1.
lsusb of course doesn't show the device because of this and inserting a card into the card reader also won't do anything.
What could I do to fix this?
The mainboard is built by ASUS with an NForce 430 chipset, the BIOS is the newest version.

When I type
```
sudo rmmod ehci-hcd 
```
the card reader is recognized and working until I restart the PC, but of course all USB 2.0 devices only work as USB1.1, which is a bad solution as I also have USB hard drives attached.

I saw a few people in this forums having had similar problems, but the threads didn't give any solutions so far. I hope someone can help me.

---

### Post by Haf on 2008-05-13
Because I couldn't think of anything else, I tried to plug the card reader to another internal USB connector, no change though, the issue is still the same.
I also double-checked the BIOS settings - nothing suspicious there.

---

### Post by gludwig333 on 2009-05-26
Purchase a USB Card Reader here:

http://www.ludwigitservices.com/catalog/index.php?cPath=16_44_32

---

