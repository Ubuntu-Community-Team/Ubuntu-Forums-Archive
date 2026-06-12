---
title: "Intel Integrated Graphics Problem"
date: 2010-04-15
forum: Hardware
---

### Post by andylondonuk on 2010-04-15
Hi There,

I have a desktop machine running Ubuntu 9.04 which has integrated Intel Graphics. My monitor is slow to refresh and will not go to the full resolution. From what I can tell, it seems to be using some standard default driver and not the Intel one.

My knowledge of Linux in this area is a bit limited, as I've never had any display issues before, so any help would be greatly appreciated.

Output form hwinfo:
```

34: PCI 02.0: 0300 VGA compatible controller (VGA)
  [Created at pci.314]
  UDI: /org/freedesktop/Hal/devices/pci_8086_42
  Unique ID: _Znp.zzcQ04R5msE
  SysFS ID: /devices/pci0000:00/0000:00:02.0
  SysFS BusID: 0000:00:02.0
  Hardware Class: graphics card
  Model: "Intel VGA compatible controller"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x0042 
  SubVendor: pci 0x1458 "Giga-byte Technology"
  SubDevice: pci 0xd000 
  Revision: 0x12
  Memory Range: 0xfb800000-0xfbbfffff (rw,non-prefetchable)
  Memory Range: 0xe0000000-0xefffffff (rw,prefetchable)
  I/O Ports: 0xff00-0xff07 (rw)
  IRQ: 10 (no events)
  I/O Ports: 0x3c0-0x3df (rw)
  Module Alias: "pci:v00008086d00000042sv00001458sd0000D000bc03sc00i00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
```

Output from lshw:
```

*-display UNCLAIMED
  description: VGA compatible controller
  product: Auburndale/Havendale Integrated Graphics Controller
  vendor: Intel Corporation
  physical id: 2
  bus info: pci@0000:00:02.0
  version: 12
  width: 64 bits
  clock: 33MHz
  capabilities: msi pm bus_master cap_list
  configuration: latency=0
```

Output from lspci:
```

00:02.0 VGA compatible controller: Intel Corporation Auburndale/Havendale Integrated Graphics Controller (rev 12)
```

Thanks a lot,
Andy.

---

