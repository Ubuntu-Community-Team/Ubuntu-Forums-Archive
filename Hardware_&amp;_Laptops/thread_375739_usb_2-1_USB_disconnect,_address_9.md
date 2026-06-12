---
title: "usb 2-1: USB disconnect, address 9"
date: 2007-03-04
forum: Hardware &amp; Laptops
---

### Post by bilbothebaggins on 2007-03-04
Hello,

As soon as I plug my USB-Stick in, it seemingly gets immediately disconnected ...

/var/log/messages:
Mar 3 17:40:17 auenland kernel: [17183637.528000] usb 2-1: new high speed USB device using ehci_hcd and address 9
Mar 3 17:40:19 auenland kernel: [17183637.664000] usb 2-1: configuration #1 chosen from 1 choice
Mar 3 17:40:19 auenland kernel: [17183637.664000] scsi9 : SCSI emulation for USB Mass Storage devices
Mar 3 17:40:19 auenland kernel: [17183637.792000] usb 2-1: USB disconnect, address 9

I've not found any other messages :/

any help appreciated,
br,
Martin

OT: I posted this problem yesterday but since noone replied and the topic is already on page 6 I think it's ok for me to repost it. If I misunderstood how these forums are read, and there is still a chance that someone'd read that, I apologize.

---

### Post by mwells on 2007-03-30
Hi there, 

I seem to have a very similar problem with a wireless ubs adaptor, did you ever resolve this issue?

Many thanks

Matt

---

### Post by juzna on 2008-05-13
Hello,

when i removed kernel module ehci_hcd, it became working:

sudo modprobe -r ehci_hcd

---

