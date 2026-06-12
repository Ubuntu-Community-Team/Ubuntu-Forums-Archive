---
title: "pl2303 USB to Serial"
date: 2008-07-31
forum: General Help
---

### Post by byroncheng on 2008-07-31
I'm trying to install a usb-serial connector.  I have drivers but they're for redhat and windows only =\

I've searched on the forums but i can't seem to find anything really "recent" or conclusive about how to do this.  Also, i appear to have some odd errors appear.

lsusb:
```
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 413c:8103 Dell Computer Corp. Wireless 350 Bluetooth
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 067b:2303 Prolific Technology, Inc. PL2303 Serial Port
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

```
At least this looks ok

these next two give me odd things that i haven't seen anywhere else...
dmesg when i plug the adapter in:
```
[13205.404883] usb 2-1: new full speed USB device using uhci_hcd and address 3
[13207.343725] usb 2-1: configuration #1 chosen from 1 choice
[13205.626114] usbserial: version magic '2.6.23-ARCH SMP preempt mod_unload 686 ' should be '2.6.24-19-generic SMP mod_unload 586 '
[13205.627113] pl2303: version magic '2.6.23-ARCH SMP preempt mod_unload 686 ' should be '2.6.24-19-generic SMP mod_unload 586 '

```
sudo modprobe usbserial vendor=0x067b product=0x2303 (found from another post somewhere):
```
FATAL: Error inserting usbserial (/lib/modules/2.6.24-19-generic/kernel/drivers/usb/serial/usbserial.ko): Invalid module format

```

Would appreciate any assistance i could get.  If it helps any, i'm trying to use PuTTY to access a wireless router for console access.

---

### Post by kbf on 2008-08-03
Hi

I am trying to resolve the same problem.

---

