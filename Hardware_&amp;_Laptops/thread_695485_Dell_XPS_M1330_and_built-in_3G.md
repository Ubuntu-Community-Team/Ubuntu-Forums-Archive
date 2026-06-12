---
title: "Dell XPS M1330 and built-in 3G"
date: 2008-02-13
forum: Hardware &amp; Laptops
---

### Post by soan on 2008-02-13
Hi

I just got a Dell XPS M1330 and running Ubuntu 7.10.

Wanted to get the built in 3G working but there did not seem to be any /dev/ttyUSB devices.

Did a lspci and saw nothing meaningful then a lsusb gave the following:

Bus 007 Device 001: ID 0000:0000  
Bus 005 Device 002: ID 0d62:a100 Darfon Electronics Corp. Benq Mouse
Bus 005 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
**Bus 004 Device 002: ID 413c:8138 Dell Computer Corp. **
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 005: ID 0bc2:2000 Seagate RSS LLC 
Bus 002 Device 004: ID 05a9:2640 OmniVision Technologies, Inc. 
Bus 002 Device 001: ID 0000:0000  

Then I did a modprobe like so:

sudo modprobe usbserial vendor=0x413c product=0x8138

Check tail /var/log/messages like so:

tail /var/log/messages
Feb 13 10:53:47 framework kernel: [ 3650.392000] usbcore: registered new interface driver usbserial
Feb 13 10:53:47 framework kernel: [ 3650.392000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
Feb 13 10:53:47 framework kernel: [ 3650.392000] usbserial_generic 4-2:1.0: generic converter detected
Feb 13 10:53:47 framework kernel: [ 3650.392000] usb 4-2: generic converter now attached to ttyUSB0
Feb 13 10:53:47 framework kernel: [ 3650.392000] usbserial_generic 4-2:1.1: generic converter detected
Feb 13 10:53:47 framework kernel: [ 3650.392000] usb 4-2: generic converter now attached to ttyUSB1
Feb 13 10:53:47 framework kernel: [ 3650.392000] usbserial_generic 4-2:1.4: generic converter detected
Feb 13 10:53:47 framework kernel: [ 3650.396000] usb 4-2: generic converter now attached to ttyUSB2
Feb 13 10:53:47 framework kernel: [ 3650.396000] usbcore: registered new interface driver usbserial_generic
Feb 13 10:53:47 framework kernel: [ 3650.396000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial Driver core

:) Now you should have /dev/ttyUSB

Cheers

---

### Post by bo01 on 2008-05-07
Hi!! Sorry if I post in the wrong topic.
I have a Dell XPS 1530 and Ubuntu 7.10.
I try to run the Vodafone Mobile Connect Card driver for Linux, but it doesn't seem to recognise my SIM card. I don't know much from 3G and wireless generally. I tried the modprobe command and still nothing happened. I have to mention that in Vista 3G works.

Thanks in advance.

---

