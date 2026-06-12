---
title: "Problem with Netway/Maxxter Wireless keyboard and mouse"
date: 2019-09-28
forum: Hardware
---

### Post by ragb1 on 2019-09-28
I'm having some issues trying to get work a combo mouse/keyboard wireless device. The mouse works properly, however the keyboard doesn't work. I'm using Ubuntu 18.04.

The model is a **Netway NW780**, but it seems to be manufactured from Maxxter.

The tricky thing is that is working properly in the same computer with Centos 7. If I connect the wireless combo to another computer with Ubuntu 18.04, the same problem occurs.

I've tried to remove and add again the **usbhid** module, but the problem persist:


```
sudo modprobe -r usbhid
```

```
sudo modprobe usbhid
```


I post the output from **hwinfo**:

1.-) **Keyboard**:

> 57: USB 00.1: 10800 Keyboard
  [Created at usb.122]
  Unique ID: x0O1.dFICFZCwlN0
  Parent ID: BSFT.BwiLSoUZ6N9
  SysFS ID: /devices/pci0000:00/0000:00:16.0/usb7/7-3/7-3:1.1
  SysFS BusID: 7-3:1.1
  Hardware Class: keyboard
  Model: "Maxxter Wireless Receiver"
  Hotplug: USB
  Vendor: usb 0x248a "Maxxter"
  Device: usb 0x8367 "Wireless Receiver"
  Revision: "1.00"
  Driver: "usbhid"
  Driver Modules: "usbhid"
  Device File: /dev/input/event5
  Device Files: /dev/input/event5, /dev/input/by-id/usb-Telink_Wireless_Receiver-if01-event-kbd, /dev/input/by-path/pci-0000:00:16.0-usb-0:3:1.1-event-kbd
  Device Number: char 13:69
  Speed: 12 Mbps
  Module Alias: "usb:v248Ap8367d0100dc00dsc00dp00ic03isc01ip01in01"
  Driver Info #0:
    XkbRules: xfree86
    XkbModel: pc104
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #55 (Hub)



2.-) **Mouse**:

> 53: USB 00.0: 10503 USB Mouse
  [Created at usb.122]
  Unique ID: Ur7z.M_nrmne0cTF
  Parent ID: BSFT.BwiLSoUZ6N9
  SysFS ID: /devices/pci0000:00/0000:00:16.0/usb7/7-3/7-3:1.0
  SysFS BusID: 7-3:1.0
  Hardware Class: mouse
  Model: "Maxxter Wireless Receiver"
  Hotplug: USB
  Vendor: usb 0x248a "Maxxter"
  Device: usb 0x8367 "Wireless Receiver"
  Revision: "1.00"
  Compatible to: int 0x0210 0x0025
  Driver: "usbhid"
  Driver Modules: "usbhid"
  Device File: /dev/input/mice (/dev/input/mouse0)
  Device Files: /dev/input/mice, /dev/input/mouse0, /dev/input/event2, /dev/input/by-id/usb-Telink_Wireless_Receiver-event-mouse, /dev/input/by-path/pci-0000:00:16.0-usb-0:3:1.0-event-mouse, /dev/input/by-id/usb-Telink_Wireless_Receiver-mouse, /dev/input/by-path/pci-0000:00:16.0-usb-0:3:1.0-mouse
  Device Number: char 13:63 (char 13:32)
  Speed: 12 Mbps
  Module Alias: "usb:v248Ap8367d0100dc00dsc00dp00ic03isc01ip02in00"
  Driver Info #0:
    Buttons: 5
    Wheels: 2
    XFree86 Protocol: explorerps/2
    GPM Protocol: exps2
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #55 (Hub)

3.-) Hub from is attached (see the previous line)

> 55: USB 00.0: 10a00 Hub
  [Created at usb.122]
  Unique ID: BSFT.BwiLSoUZ6N9
  Parent ID: WnlC.BDXXLZhMRx2
  SysFS ID: /devices/pci0000:00/0000:00:16.0/usb7/7-0:1.0
  SysFS BusID: 7-0:1.0
  Hardware Class: hub
  Model: "Linux Foundation 1.1 root hub"
  Hotplug: USB
  Vendor: usb 0x1d6b "Linux Foundation"
  Device: usb 0x0001 "1.1 root hub"
  Revision: "5.00"
  Serial ID: "0000:00:16.0"
  Driver: "hub"
  Driver Modules: "usbcore"
  Speed: 12 Mbps
  Module Alias: "usb:v1D6Bp0001d0500dc09dsc00dp00ic09isc00ip00in00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #26 (USB Controller)

4.- USB Controller: (#26)

> 26: PCI 16.0: 0c03 USB Controller (OHCI)
  [Created at pci.378]
  Unique ID: WnlC.BDXXLZhMRx2
  SysFS ID: /devices/pci0000:00/0000:00:16.0
  SysFS BusID: 0000:00:16.0
  Hardware Class: usb controller
  Model: "ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller"
  Vendor: pci 0x1002 "ATI Technologies Inc"
  Device: pci 0x4397 "SB7x0/SB8x0/SB9x0 USB OHCI0 Controller"
  SubVendor: pci 0x1002 "ATI Technologies Inc"
  SubDevice: pci 0x4397 
  Driver: "ohci-pci"
  Memory Range: 0xfe205000-0xfe205fff (rw,non-prefetchable)
  IRQ: 22 (3574 events)
  Module Alias: "pci:v00001002d00004397sv00001002sd00004397bc0Csc03i10"
  Driver Info #0:
    Driver Status: ohci-hcd is not active
    Driver Activation Cmd: "modprobe ohci-hcd"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

Anyone could help?

Thanks in advance.

Best regards.

---

