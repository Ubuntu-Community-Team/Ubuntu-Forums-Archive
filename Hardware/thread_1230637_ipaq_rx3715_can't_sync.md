---
title: "ipaq rx3715 can't sync"
date: 2009-08-03
forum: Hardware
---

### Post by Supr-me on 2009-08-03
Hello everyone,

I've got some trouble setting up my pocketpc for synce.
I get the following output from the commands listed beneath:

dmesg:
> 
[10188.008102] usb 3-1: USB disconnect, address 3
[10412.628069] usb 3-1: new full speed USB device using uhci_hcd and address 4
[10412.780301] usb 3-1: configuration #2 chosen from 1 choice
[10412.783511] ipaq 3-1:2.0: PocketPC PDA converter detected
[10412.783526] ipaq: active config #2 != 1 ??
[10412.783541] ipaq: probe of 3-1:2.0 failed with error -5

normally it should say something like: 
> 
usb 3-1: PocketPC PDA converter now attached to ttyUSB0
usbcore: registered new driver ipaq

at the end, am I right?

lsusb:
> 
[..]
Bus 003 Device 005: ID 03f0:1016 Hewlett-Packard Jornada 548 / iPAQ HW6515 Pocket PC
[..]


synce-pls
> 
** Message: Hal reports no devices connected
** Message: Odccm is not running, ignoring
synce-pls: Could not find configuration at path '(Default)'


Is there anyone that is experiencing the same trouble while trying to connect his ipaq or perhaps someone that already solved this matter?

Or could someone else please put some light on this matter?


Thanks in advance!

---

