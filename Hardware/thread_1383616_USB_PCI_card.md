---
title: "USB PCI card"
date: 2010-01-17
forum: Hardware
---

### Post by guiwegian on 2010-01-17
I recently bought a PCI usb card with 5 usb port on it.I already have 6 usb ports on my mother board, but turns out I need some more.
The problem is, I cannot have all USB port working together at the same time, but only from the PCI card.
I mean, I can get the 6 motherboard sub working + another 2 on the PCI(if I plug some more, they disabled another one on the PCI card.
Basically this card allow me to have only two devices/peripheral a time.
Is it an Ubuntu problem or the PCI card??

I did further research and decided to do LSUSB, to identify each sub port:
unfortunately I couldnt get all devices puged-in on the PCI card so I had to do them one by one to identify them.
I finally get that the PCI card has got 4 external usb port on the bus 6 and the internal bus is on the bus 2.
Is there any order to allocate buses????
Another thing is, if I plug in a device on bus 2, I get devices on bus 6 becoming disabled and finally nothing works.If I have more than 2 devices on bus 6 , the first 2 devices will work but the others won't be detected.

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 07d1:3c03 D-Link System DWL-G122 802.11g Adapter [ralink rt73]
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 004: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 065: ID 0bc7:0004 X10 Wireless Technology, Inc. X10 Receiver
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

here is one of my lsusb

Please share your experience and tell me what I could do.
I was wondering If I could change the address of the bus and allocated a different address to them manually??
Any advice would be greatful
Thanks for reading

---

### Post by guiwegian on 2010-01-29
!anybody for me!!!???
Please

---

