---
title: "[SOLVED] Problem with USB mouse"
date: 2008-11-19
forum: Hardware
---

### Post by Altmerman on 2008-11-19
Hello! I installed Ubuntu 8.10 and my touchpad works fine, but Logitech USB mouse is bad. It doesn't move smoothly, hard to aim. When I unplug it and then plug in again it won't work at all until reboot.
Ubuntu 8.10
kernel 2.6.27-7
mouse - Logitech USB
Notebook BenQ Joybook r31e, VIA PN800

lsusb (after uplug/plug):
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

dmesg | tail after lsusb:

[   54.229246] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   54.356971] NET: Registered protocol family 17
[  458.436322] NET: Registered protocol family 10
[  458.439108] lo: Disabled Privacy Extensions
[  458.441535] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1624.072086] usb 2-1: USB disconnect, address 3
[ 1642.732039] usb 2-1: new low speed USB device using uhci_hcd and address 4
[ 1645.913405] usb 2-1: configuration #1 chosen from 1 choice
[ 1646.645836] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:10.1/usb2/2-1/2-1:1.0/input/input10
[ 1646.672233] input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:10.1-1

dmesg | tail (after unplug/plug,but before lsusb):

[   54.356971] NET: Registered protocol family 17
[  458.436322] NET: Registered protocol family 10
[  458.439108] lo: Disabled Privacy Extensions
[  458.441535] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1624.072086] usb 2-1: USB disconnect, address 3
[ 1642.732039] usb 2-1: new low speed USB device using uhci_hcd and address 4
[ 1645.913405] usb 2-1: configuration #1 chosen from 1 choice
[ 1646.645836] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:10.1/usb2/2-1/2-1:1.0/input/input10
[ 1646.672233] input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:10.1-1
[ 1767.912093] usb 2-1: USB disconnect, address 4

if I print lsusb 2 time in a row, then mouse starts working.This is after second lsusb:

Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 005: ID 046d:c03e Logitech, Inc. Premium Optical Wheel Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

What should I do?

---

### Post by Altmerman on 2008-11-19
Problem solved. I added noapic irqpoll

empthollow
June 18th, 2007, 06:41 AM
the easiest way is to chng the /boot/grub/menu.lst
on the line where you see 
kernel /boot/vmlinuz-2.6.20-16-generic root=UUID=8f487494-dea3-425e-9d51-439f0848b3d8 ro quiet splash 
add noapic irqpoll
mine looks like this but don't copy and paste it because the uuid may be different
kernel /boot/vmlinuz-2.6.20-16-generic root=UUID=8f487494-dea3-425e-9d51-439f0848b3d8 ro quiet splash noapic irqpoll

---

