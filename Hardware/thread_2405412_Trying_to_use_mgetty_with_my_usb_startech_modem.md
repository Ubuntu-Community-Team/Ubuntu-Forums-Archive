---
title: "Trying to use mgetty with my usb startech modem"
date: 2018-11-05
forum: Hardware
---

### Post by jeromelemay on 2018-11-05
Hi, 

I'm quite new to Linux/Ubuntu and I'm tring to figure out how to configure my usb modem (startech) with mgetty. I need to specify which serial port my modem is connected on in the voice.conf file, but I can't find the answer in the /dev directory.

When I use the lsusb i got this result : 

Bus 002 Device 003: ID 05ac:8502 Apple, Inc. Built-in iSight
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 002: ID 05ac:8242 Apple, Inc. Built-in IR Receiver
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 045e:07f8 Microsoft Corp. Wired Keyboard 600 (model 1576)
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 0572:1329 Conexant Systems (Rockwell), Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 046d:c534 Logitech, Inc. Unifying Receiver
Bus 003 Device 004: ID 05ac:8206 Apple, Inc. Bluetooth HCI
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

When I browse the /dev directory, i can't find any device under ttyUSB*. All I could find is one device named ttyACM0 and i'm pretty sure it refers to my Modem (but i'm not sure)

what are the step to make my modem recognized as a serial modem over a usb connection?

Thanks!

---

### Post by ajgreeny on 2018-11-06
Is your machine Apple hardware?

Please let us know as we can move it to the Apple hardware section when it may get more response from Apple users; most of us do not use Apple hardware and the differences between Apple and standard PC can be  very important.

**Please don't create a new thread**; we will move this one.

---

