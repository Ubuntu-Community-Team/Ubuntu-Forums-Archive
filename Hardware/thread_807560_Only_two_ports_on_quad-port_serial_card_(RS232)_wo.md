---
title: "Only two ports on quad-port serial card (RS232) working"
date: 2008-05-25
forum: Hardware
---

### Post by terencekent on 2008-05-25
I have several 4 port serial PCIe cards that I have to get working on Ubuntu 8.04 Server. After physically installing the cards, two of the ports work perfectly , but I can't see the other two at all. 

Here is my symptom:
On boot, I always get the same 4 serial device entries, /dev/ttyS[0-3], where /dev/ttyS0 and /dev/ttyS1 are always used by the two system serial devices. When the PCIe card is installed,  /dev/ttyS2 and /dev/ttyS3 are the first two ports on the PCIe card. Both ttyS2 and ttyS3 work perfectly, but /dev/ttyS4 and /dev/ttyS5 entries are created to access with the two additional ports.

My first guess is that I just need to use something to force more device entries to be created at boot, but I'm not sure how to do that, or if that's even the right answer.


Any help would be greatly appreciated!

Thanks,
Terence.

Here is a link to an advertisement for the card I have...
[http://qualitycables.com/productdetails1.cfm?sku=CM-4SRS232&cats=99172](http://qualitycables.com/productdetails1.cfm?sku=CM-4SRS232&cats=99172)


Here is the output from hwinfo

15: PCI 900.0: 0700 Serial controller (16950)
  [Created at pci.296]
  Unique ID: x1VA.X6OsFKAdrtA
  Parent ID: GBI1.kPe8RsCV5kE
  SysFS ID: /devices/pci0000:00/0000:00:02.0/0000:04:00.0/0000:05:01.0/0000:08:00.0/0000:09:00.0
  SysFS BusID: 0000:09:00.0
  Hardware Class: unknown
  Model: "Oxford OX16PCI954 (Quad 16950 UART) function 0"
  Vendor: pci 0x1415 "Oxford Semiconductor Ltd"
  Device: pci 0x9501 "OX16PCI954 (Quad 16950 UART) function 0"
  SubVendor: pci 0x1415 "Oxford Semiconductor Ltd"
  SubDevice: pci 0x0000 
  Driver: "serial"
  I/O Ports: 0xdce0-0xdcff (rw)
  Memory Range: 0xd5eff000-0xd5efffff (rw,non-prefetchable)
  I/O Ports: 0xdca0-0xdcbf (rw)
  Memory Range: 0xd5efe000-0xd5efefff (rw,non-prefetchable)
  IRQ: 17 (86 events)
  Module Alias: "pci:v00001415d00009501sv00001415sd00000000bc07sc00i06"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #16 (PCI bridge)

---

### Post by lswb on 2008-05-26
Install the setserial package, I think you'll need it. The man pages that come with it should help.

---

### Post by terencekent on 2008-05-26
I've installed the set serial package, whose manpage suggests that's the right path to follow...

(from the manpage....)
> 
During  the  normal bootup process, only COM ports 1-4 are initialized,
using the default I/O ports and IRQ values, as listed below.  In  order
to  initialize  any  additional  serial ports, or to change the COM 1-4
ports to a nonstandard configuration, the setserial program  should  be
 used.


But I am at a loss on how to proceed. I read the setserial init script and was pointed to the configuration file /var/lib/setserial/autoserial.conf. This file contained the following entries:

```

/dev/ttyS0 uart 16550A port 0x03f8 irq 12 baud_base 115200 spd_normal skip_test
/dev/ttyS1 uart 16550A port 0x02f8 irq 3 baud_base 115200 spd_normal skip_test
/dev/ttyS2 uart 16950/954 port 0xdce0 irq 17 baud_base 115200 spd_normal skip_test
/dev/ttyS3 uart 16950/954 port 0xdce8 irq 17 baud_base 115200 spd_normal skip_test

```

and so I added the these lines in a blind attempt to get it working, with no luck. (Of course, I used mknod to create the device entries first...)
```

/dev/ttyS4 uart 16950/954 port 0xdcf0 irq 17 baud_base 115200 spd_normal skip_test
/dev/ttyS5 uart 16950/954 port 0xdcf8 irq 17 baud_base 115200 spd_normal skip_test

```

I'm finding this surprisingly complex, I hope somebody who has done this before can point me in the right direction!

Thanks again,
Terence.

---

