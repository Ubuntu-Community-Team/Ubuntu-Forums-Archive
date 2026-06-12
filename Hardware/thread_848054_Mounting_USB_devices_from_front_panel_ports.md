---
title: "Mounting USB devices from front panel ports"
date: 2008-07-03
forum: Hardware
---

### Post by Jamesss on 2008-07-03
Hi,

I have a problem with mounting USB devices on my computer. I have two USB ports on the back of my computer which work fine, however I would like to use the two on the front of the computer as well. I've tried various devices such as an ipod, external hard drive, memory sticks, etc and they all need to be plugged in at the back of the computer. The two ports at the front work fine in Windows XP.

EDIT: actually I just found a device that does work with the front ports! My Archos Jukebox Recorder mounts fine, so why don't the other items?

I'm running -

Ubuntu 8.04 (Hardy)
2.6.24.16
AMD Athlon XP 2400+
VIA KT266a motherboard
512mb RAM

Any help appreciated!

I tried dmesg | tail and this is what i got:

[ 3728.902705] usb 4-3: new high speed USB device using ehci_hcd and address 89
[ 3730.150557] usb 4-3: new high speed USB device using ehci_hcd and address 95
[ 3730.662490] usb 4-3: new high speed USB device using ehci_hcd and address 97
[ 3730.958445] usb 4-3: new high speed USB device using ehci_hcd and address 98
[ 3731.254413] usb 4-3: new high speed USB device using ehci_hcd and address 99
[ 3731.582364] usb 4-3: new high speed USB device using ehci_hcd and address 100
[ 3731.878319] usb 4-3: new high speed USB device using ehci_hcd and address 101
[ 3732.174277] usb 4-3: new high speed USB device using ehci_hcd and address 102
[ 3733.206160] usb 4-3: new high speed USB device using ehci_hcd and address 107
[ 3733.718088] usb 4-3: new high speed USB device using ehci_hcd and address 109

---

### Post by bardophile on 2009-05-01
Just wondering if you've had any luck figuring this out. I'm also trying to sort out front panel USB issues. I can get either of them to work singly, but not both simultaneously.

---

