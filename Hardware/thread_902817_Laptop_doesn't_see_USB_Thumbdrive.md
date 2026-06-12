---
title: "Laptop doesn't see USB Thumbdrive"
date: 2008-08-27
forum: Hardware
---

### Post by jpeery on 2008-08-27
Not sure why this thumbdrive isn't being recognized when I plug it in.  It recognizes my mouse just fine, so the USB works, but it doesn't ever mount or see my thumbdrive????
Here's a listing from lsusb:

root@CaddieWompus:/home/jason# lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 001 Device 001: ID 0000:0000  


I know this stick works, my Ubuntu PC sees it fine, my MAC sees it fine, but this laptop doesn't...  Scratching my head - help?
Thanks!
JP

---

### Post by damis648 on 2008-08-27
What if you tail dmesg and plug it in?
```
dmesg | tail -f
```

---

### Post by jpeery on 2008-08-27
Doesn't look good:

root@CaddieWompus:/home/jason# dmesg |tail -f
[ 4663.187012] usb 2-2: new high speed USB device using ehci_hcd and address 12
[ 4665.078162] atkbd.c: Unknown key pressed (translated set 2, code 0xd8 on isa0060/serio0).
[ 4665.078170] atkbd.c: Use 'setkeycodes e058 <keycode>' to make it known.
[ 4670.966735] usb 2-2: device not accepting address 12, error -110
[ 4671.022731] usb 2-2: new high speed USB device using ehci_hcd and address 13
[ 4678.800494] usb 2-2: device not accepting address 13, error -110
[ 4678.856486] usb 2-2: new high speed USB device using ehci_hcd and address 14
[ 4684.710993] usb 2-2: device not accepting address 14, error -110
[ 4684.766983] usb 2-2: new high speed USB device using ehci_hcd and address 15
[ 4690.622041] usb 2-2: device not accepting address 15, error -110

---

### Post by damis648 on 2008-08-28
> **jpeery said:**
> Doesn't look good:

root@CaddieWompus:/home/jason# dmesg |tail -f
[ 4663.187012] usb 2-2: new high speed USB device using ehci_hcd and address 12
[ 4665.078162] atkbd.c: Unknown key pressed (translated set 2, code 0xd8 on isa0060/serio0).
[ 4665.078170] atkbd.c: Use 'setkeycodes e058 <keycode>' to make it known.
[ 4670.966735] usb 2-2: device not accepting address 12, error -110
[ 4671.022731] usb 2-2: new high speed USB device using ehci_hcd and address 13
[ 4678.800494] usb 2-2: device not accepting address 13, error -110
[ 4678.856486] usb 2-2: new high speed USB device using ehci_hcd and address 14
[ 4684.710993] usb 2-2: device not accepting address 14, error -110
[ 4684.766983] usb 2-2: new high speed USB device using ehci_hcd and address 15
[ 4690.622041] usb 2-2: device not accepting address 15, error -110

Wierd... I tried a google search on this error (110) but I couldn't find anything so far. I will keep looking.

---

### Post by jpeery on 2008-08-28
Thanks, doing the same.

---

