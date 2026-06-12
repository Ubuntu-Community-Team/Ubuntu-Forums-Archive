---
title: "PCI Device Help Please: Connect x3270 through Forvus coax PCI card?"
date: 2010-01-13
forum: Hardware
---

### Post by buttertoad on 2010-01-13
I am trying to connect to a S/390 mainframe by way of Terminal Control Units. The cable I have to use for the connection is coax. I have a Forvus PCI adapter card which allows me to connect to the coax but I don't know how to get the terminal emulator x3270 to use that connection.

I can see the card in Ubuntu with the lspci command but all the system seems to do is assign the card io ports.

lspci
```
04:01.0 Communication controller: FORVUS RESEARCH Inc Device 0001
```
dmesg
```
[    0.276221] pci 0000:04:01.0: reg 10 io port: [0xcc80-0xccff]
[    0.276230] pci 0000:04:01.0: reg 14 io port: [0xcc70-0xcc7f]
[    0.276239] pci 0000:04:01.0: reg 18 32bit mmio: [0xdfafe000-0xdfafffff]
```

I've done a lot of searching for device drivers or other people that have used the card in Linux and I have found a couple mentions of the device but no one has said how they got it to work.

This may be crazy but I tried the setserial command to try assigning one of the io ports that are mentioned to /dev/ttyS3. Then I used ser2net to map the serial device to a TCP port. I was not able to get any data across the connection but I'm not sure which io port out of the range I should use.

Would this card act more like a modem then a serial port?

If anyone has any insight into how to use this card I would greatly appreciate it.

---

