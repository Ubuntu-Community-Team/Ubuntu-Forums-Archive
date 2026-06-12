---
title: "Wake up from suspend - Logitech Cordless Desktop Wave Pro"
date: 2013-03-19
forum: Hardware
---

### Post by ak0ska on 2013-03-19
Hello,

I have trouble allowing my computer to be woken up by my usb wireless keyboard (as mentioned in the title, [part of this set]("http://www.logitech.com/en-us/support/4677")).

I tried a few guides, that says it should be enabled in /proc/acpi/wakeup, but I think it already is. It works under Windows (I don't know if thi is relevant or not). My motherboard is an [Asus P5k Pro]("http://www.asus.com/Motherboards/P5K_PRO/"). OS is Xubuntu 12.10.

Output of lsusb:
```
Bus 001 Device 002: ID 0424:2514 Standard Microsystems Corp. USB 2.0 Hub
Bus 001 Device 005: ID 090c:1000 Silicon Motion, Inc. - Taiwan (formerly Feiya Technology Corp.) 64MB QDI U2 DISK
Bus 004 Device 002: ID 045e:0719 Microsoft Corp. Xbox 360 Wireless Adapter
Bus 004 Device 003: ID 046d:c529 Logitech, Inc. diNovo Keyboard for notebooks
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

It seems strange, it appears as a diNovo Keyboard. 

Output of lsusb -t
```
4-1:1.1: No such file or directory
4-1:1.3: No such file or directory
4-1:1.5: No such file or directory
4-1:1.7: No such file or directory
/:  Bus 08.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 07.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 06.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 05.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 04.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
    |__ Port 1: Dev 2, If 0, Class=vend., Driver=xpad, 12M
    |__ Port 1: Dev 2, If 1, Class=vend., Driver=, 12M
    |__ Port 1: Dev 2, If 2, Class=vend., Driver=xpad, 12M
    |__ Port 1: Dev 2, If 3, Class=vend., Driver=, 12M
    |__ Port 1: Dev 2, If 4, Class=vend., Driver=xpad, 12M
    |__ Port 1: Dev 2, If 5, Class=vend., Driver=, 12M
    |__ Port 1: Dev 2, If 6, Class=vend., Driver=xpad, 12M
    |__ Port 1: Dev 2, If 7, Class=vend., Driver=, 12M
    |__ Port 2: Dev 3, If 0, Class=HID, Driver=usbhid, 12M
    |__ Port 2: Dev 3, If 1, Class=HID, Driver=usbhid, 12M
/:  Bus 03.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=ehci_hcd/6p, 480M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci_hcd/6p, 480M
    |__ Port 2: Dev 2, If 0, Class=hub, Driver=hub/4p, 480M
    |__ Port 6: Dev 5, If 0, Class=stor., Driver=usb-storage, 480M
```


cat /sys/bus/usb/devices/4-2/power/wakeup says "Enabled".


Output of dmesg | grep -i logitech
```
[    2.177462] usb 4-2: Manufacturer: Logitech
[    2.193038] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1a.1/usb4/4-2/4-2:1.0/input/input2
[    2.193118] hid-generic 0003:046D:C529.0001: input,hidraw0: USB HID v1.11 Keyboard [Logitech USB Receiver] on usb-0000:00:1a.1-2/input0
[    2.193610] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1a.1/usb4/4-2/4-2:1.1/input/input3
[    2.193727] hid-generic 0003:046D:C529.0002: input,hiddev0,hidraw1: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1a.1-2/input1
```

And the output of cat /proc/acpi/wakeup
```
Device	S-state	  Status   Sysfs node
P0P2	  S4	*disabled  pci:0000:00:01.0
P0P1	  S4	*disabled  pci:0000:00:1e.0
UAR1	  S4	*disabled  pnp:00:09
PS2K	  S4	*enabled   pnp:00:0b
PS2M	  S4	*disabled  pnp:00:0c
EUSB	  S4	*enabled   pci:0000:00:1d.7
USBE	  S4	*enabled   pci:0000:00:1a.7
P0P5	  S4	*disabled  
P0P6	  S4	*disabled  
P0P7	  S4	*disabled  
P0P8	  S4	*disabled  pci:0000:00:1c.4
P0P9	  S4	*disabled  pci:0000:00:1c.5
USB0	  S4	*enabled   pci:0000:00:1d.0
USB1	  S4	*enabled   pci:0000:00:1d.1
USB2	  S4	*enabled   pci:0000:00:1d.2
USB3	  S4	*disabled  
USB4	  S4	*enabled   pci:0000:00:1a.0
USB5	  S4	*enabled   pci:0000:00:1a.1
USB6	  S4	*enabled   pci:0000:00:1a.2
P0P4	  S4	*disabled  pci:0000:00:1c.0

```

Any ideas what should I check or try?

Thanks,

ak0ska

---

