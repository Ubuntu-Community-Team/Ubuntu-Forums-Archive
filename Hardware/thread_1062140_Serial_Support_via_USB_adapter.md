---
title: "Serial Support via USB adapter"
date: 2009-02-06
forum: Hardware
---

### Post by fhsm on 2009-02-06
I've got an obscure bit of scientific hardware that I'm trying to get at using 8.10.  I need to connect via serial; however, my laptop doesn't have a serial port.  I've connected a USB/Serial adapter to the system and it looks like it's working.  lsusb:
```
Bus 003 Device 006: ID 050d:0109 Belkin Components F5U109/F5U409 PDA Adapter
```

dmesg shows: ```

usb 3-2: new full speed USB device using uhci_hcd and address 6
usb 3-2: configuration #1 chosen from 1 choice
mct_u232 3-2:1.0: MCT U232 converter detected
usb 3-2: MCT U232 converter now attached to ttyUSB0

```

/dev/ttyUSB0 does show up but I don't see a /dev/ttyS0.  I'm wondering if I've there is some generic tool to just poke around the serial port(s) / devices and see what's out there.  Unfortunately the hardware's controller program is windows only so I'm trying to run it in wine.  Which isn't working.  I'm trying to debug the problem from either end.

---

### Post by markbuntu on 2009-02-06
Sounds like you need a serial terminal program to talk with the serial port. There are a number of them in the repos

gtkterm
cutecom
cereal for automated logging

to name a few. Just open one up and aim it at /dev/tty/USBO

---

