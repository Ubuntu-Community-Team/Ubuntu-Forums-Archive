---
title: "usb 2.0 / firewire cardbus + feisty"
date: 2007-06-21
forum: Hardware &amp; Laptops
---

### Post by coverup on 2007-06-21
Hello all,

I needed USB 2.0 ports on my Dell Inspiron 2650 laptop (which works great aside from this under Ubuntu Studio / Feisty!) so I decided to buy a Cables Unlimited USB 2.0 / Firewire PCMCIA card.  The cardbus works fine for trivial USB devices (mouse, keyboard) but not so well for my external drive and mp3 player, which I why I needed USB 2.0 in the first place.

The hard drive, for example, mounts and appears to work, but transfers stall and it seems intermittent whether or not it's working.  Sometimes it loses connectivity entirely.  I am using the cardbus with the specified power adaptor to give the devices enough power, so that shouldn't be the problem - the hard drive is powered anyway.

The real manufacturer for the pcmcia guts seems to be ALi.

Here is the lspci output when I plug in the cardbus:
02:04.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller
03:00.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
03:00.1 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
03:00.3 USB Controller: ALi Corporation USB 2.0 Controller (rev 01)
03:00.4 FireWire (IEEE 1394): ALi Corporation M5253 P1394 OHCI 1.1 Controller

Here is the dmesg output:
[  268.543000] pccard: CardBus card inserted into slot 0
[  268.719000] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[  268.720000] PCI: Enabling device 0000:03:00.0 (0000 -> 0002)
[  268.721000] ACPI: PCI Interrupt 0000:03:00.0[B] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[  268.721000] ohci_hcd 0000:03:00.0: OHCI Host Controller
[  268.722000] ohci_hcd 0000:03:00.0: new USB bus registered, assigned bus number 3
[  268.723000] ohci_hcd 0000:03:00.0: irq 10, io mem 0x28000000
[  268.777000] usb usb3: configuration #1 chosen from 1 choice
[  268.778000] hub 3-0:1.0: USB hub found
[  268.778000] hub 3-0:1.0: 2 ports detected
[  268.880000] PCI: Enabling device 0000:03:00.1 (0000 -> 0002)
[  268.880000] ACPI: PCI Interrupt 0000:03:00.1[B] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[  268.880000] ohci_hcd 0000:03:00.1: OHCI Host Controller
[  268.880000] ohci_hcd 0000:03:00.1: new USB bus registered, assigned bus number 4
[  268.881000] ohci_hcd 0000:03:00.1: irq 10, io mem 0x28001000
[  268.934000] usb usb4: configuration #1 chosen from 1 choice
[  268.934000] hub 4-0:1.0: USB hub found
[  268.934000] hub 4-0:1.0: 2 ports detected
[  268.937000] ieee1394: Initialized config rom entry `ip1394'
[  269.107000] PCI: Enabling device 0000:03:00.4 (0000 -> 0002)
[  269.107000] ACPI: PCI Interrupt 0000:03:00.4[C] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[  269.107000] PCI: Setting latency timer of device 0000:03:00.4 to 64
[  269.158000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[10]  MMIO=[28002000-280027ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[  269.195000] PCI: Enabling device 0000:03:00.3 (0000 -> 0002)
[  269.195000] ACPI: PCI Interrupt 0000:03:00.3[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[  269.196000] ehci_hcd 0000:03:00.3: EHCI Host Controller
[  269.196000] ehci_hcd 0000:03:00.3: new USB bus registered, assigned bus number 5
[  269.196000] ehci_hcd 0000:03:00.3: debug port 1
[  269.197000] PCI: cache line size of 128 is not supported by device 0000:03:00.3
[  269.218000] ehci_hcd 0000:03:00.3: irq 10, io mem 0x28002800
[  269.218000] ehci_hcd 0000:03:00.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[  269.219000] usb usb5: configuration #1 chosen from 1 choice
[  269.219000] hub 5-0:1.0: USB hub found
[  269.219000] hub 5-0:1.0: 6 ports detected
[  270.415000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0090e63900000764]


Thanks in advance!  I really hope someone can help me with this.

---

### Post by ukripper on 2007-06-21
can you post output of the following commands:

```
dmesg | grep usb
```

```
lsusb
```

```
cat /proc/bus/usb/devices
```

---

### Post by coverup on 2007-06-22
Hello, thanks for responding.  Here's the info:

```
:~$ dmesg | grep usb
[   16.063530] usbcore: registered new interface driver usbfs
[   16.063572] usbcore: registered new interface driver hub
[   16.063617] usbcore: registered new device driver usb
[   16.065701] usb usb1: configuration #1 chosen from 1 choice
[   16.167133] usb usb2: configuration #1 chosen from 1 choice
[   16.372275] usb 1-1: new low speed USB device using uhci_hcd and address 2
[    4.748000] usb 1-1: configuration #1 chosen from 1 choice
[    4.957000] usb 2-1: new full speed USB device using uhci_hcd and address 2
[    5.095000] usb 2-1: configuration #1 chosen from 1 choice
[    5.384000] usb 2-1.1: new low speed USB device using uhci_hcd and address 3
[    5.534000] usb 2-1.1: configuration #1 chosen from 1 choice
[    5.542000] usbcore: registered new interface driver hiddev
[    5.555000] input: USB HID v1.10 Mouse [Logitech USB Optical Mouse] on usb-0000:00:1d.0-1
[    5.575000] input: USB HID v1.00 Keyboard [Alps Electric M2452] on usb-0000:00:1d.1-1.1
[    5.575000] usbcore: registered new interface driver usbhid
[    5.575000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   26.750000] usb usb3: configuration #1 chosen from 1 choice
[   26.904000] usb usb4: configuration #1 chosen from 1 choice
[   27.026000] usb usb5: configuration #1 chosen from 1 choice
```

```
~$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 05ac:0201 Apple Computer, Inc. iMac Keyboard [ALPS M2452]
Bus 002 Device 002: ID 0409:55ab NEC Corp. Hub [iMac/iTouch kbd]
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 046d:c00c Logitech, Inc. Optical Wheel Mouse
Bus 001 Device 001: ID 0000:0000  

```

```
~$ cat /proc/bus/usb/devices

T:  Bus=05 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 6
B:  Alloc=  0/800 us ( 0%), #Int=  0, #Iso=  0
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.20-16-lowlatency ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:03:00.3
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   4 Ivl=256ms

T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
B:  Alloc=  0/900 us ( 0%), #Int=  0, #Iso=  0
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.20-16-lowlatency ohci_hcd
S:  Product=OHCI Host Controller
S:  SerialNumber=0000:03:00.1
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=255ms

T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
B:  Alloc=  0/900 us ( 0%), #Int=  0, #Iso=  0
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.20-16-lowlatency ohci_hcd
S:  Product=OHCI Host Controller
S:  SerialNumber=0000:03:00.0
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=255ms

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
B:  Alloc=129/900 us (14%), #Int=  2, #Iso=  0
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.20-16-lowlatency uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.1
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=255ms

T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=12  MxCh= 4
D:  Ver= 1.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=0409 ProdID=55ab Rev= 1.00
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   1 Ivl=255ms

T:  Bus=02 Lev=02 Prnt=02 Port=00 Cnt=01 Dev#=  3 Spd=1.5 MxCh= 0
D:  Ver= 1.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=05ac ProdID=0201 Rev= 1.01
S:  Manufacturer=Alps Electric
S:  Product=M2452
C:* #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=01 Driver=usbhid
E:  Ad=81(I) Atr=03(Int.) MxPS=   8 Ivl=10ms

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
B:  Alloc= 93/900 us (10%), #Int=  1, #Iso=  0
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.20-16-lowlatency uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.0
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=255ms

T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=1.5 MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=046d ProdID=c00c Rev=21.10
S:  Manufacturer=Logitech
S:  Product=USB Optical Mouse
C:* #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid
E:  Ad=81(I) Atr=03(Int.) MxPS=   4 Ivl=10ms
```

Let me know if you need me to do this, for example, with the external hard drive attached - these are all with no devices attached to it.

---

### Post by ukripper on 2007-06-22
Please do all of the above with devices attached . 

Thanks.

---

### Post by coverup on 2007-06-22
Here you go - this is with my MP3 player (Sansa e260) and external HD (Western Digital MyBook 320 GB) plugged in to the two USB ports on the cardbus.

```
~$ dmesg | grep usb
[   16.847315] usbcore: registered new interface driver usbfs
[   16.847358] usbcore: registered new interface driver hub
[   16.847404] usbcore: registered new device driver usb
[   16.849511] usb usb1: configuration #1 chosen from 1 choice
[   16.950656] usb usb2: configuration #1 chosen from 1 choice
[   17.155771] usb 1-1: new low speed USB device using uhci_hcd and address 2
[    4.747000] usb 1-1: configuration #1 chosen from 1 choice
[    4.956000] usb 2-1: new full speed USB device using uhci_hcd and address 2
[    5.094000] usb 2-1: configuration #1 chosen from 1 choice
[    5.383000] usb 2-1.1: new low speed USB device using uhci_hcd and address 3
[    5.533000] usb 2-1.1: configuration #1 chosen from 1 choice
[    5.541000] usbcore: registered new interface driver hiddev
[    5.554000] input: USB HID v1.10 Mouse [Logitech USB Optical Mouse] on usb-0000:00:1d.0-1
[    5.575000] input: USB HID v1.00 Keyboard [Alps Electric M2452] on usb-0000:00:1d.1-1.1
[    5.575000] usbcore: registered new interface driver usbhid
[    5.576000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   26.697000] usb usb3: configuration #1 chosen from 1 choice
[   26.851000] usb usb4: configuration #1 chosen from 1 choice
[   26.974000] usb usb5: configuration #1 chosen from 1 choice
[   46.405000] usb 5-2: new high speed USB device using ehci_hcd and address 2
[   46.521000] usb 5-2: configuration #1 chosen from 1 choice
[   46.754000] usbcore: registered new interface driver libusual
[   46.918000] usbcore: registered new interface driver usb-storage
[   46.919000] usb-storage: device found at 2
[   46.919000] usb-storage: waiting for device to settle before scanning
[   51.925000] usb-storage: device scan complete
[  145.155000] usb 5-1: new high speed USB device using ehci_hcd and address 3
[  146.032000] usb 5-1: configuration #128 chosen from 1 choice
[  146.370000] usb-storage: device found at 3
[  146.370000] usb-storage: waiting for device to settle before scanning
[  151.370000] usb-storage: device scan complete
[  152.673000] usb 5-1: reset high speed USB device using ehci_hcd and address 3
[  182.914000] usb 5-1: reset high speed USB device using ehci_hcd and address 3
[  193.156000] usb 5-1: reset high speed USB device using ehci_hcd and address 3
[  209.395000] usb 5-1: reset high speed USB device using ehci_hcd and address 3
[  209.634000] usb 5-1: reset high speed USB device using ehci_hcd and address 3
[  219.868000] usb 5-1: reset high speed USB device using ehci_hcd and address 3
[  220.921000] usb 5-1: reset high speed USB device using ehci_hcd and address 3
[  221.040000] usb 5-1: can't restore configuration #128 (error=-71)
[  221.041000] usb 5-1: USB disconnect, address 3
[  221.139000] usb 5-2: reset high speed USB device using ehci_hcd and address 2
[  221.253000] usb 5-2: device firmware changed
[  221.355000] usb 5-1: new high speed USB device using ehci_hcd and address 4
[  221.473000] usb 5-1: configuration #128 chosen from 1 choice
[  221.493000] usb 5-2: USB disconnect, address 2
[  221.498000] usb-storage: device found at 4
[  221.498000] usb-storage: waiting for device to settle before scanning
[  221.600000] usb 5-2: new high speed USB device using ehci_hcd and address 5
[  221.717000] usb 5-2: configuration #1 chosen from 1 choice
[  221.718000] usb-storage: device found at 5
[  221.718000] usb-storage: waiting for device to settle before scanning
[  226.499000] usb-storage: device scan complete
[  226.719000] usb-storage: device scan complete
[  230.081000] usb 5-1: reset high speed USB device using ehci_hcd and address 4
[  230.200000] usb 5-1: can't restore configuration #128 (error=-71)
[  230.200000] usb 5-1: USB disconnect, address 4
[  230.299000] usb 5-2: reset high speed USB device using ehci_hcd and address 5
[  231.366000] usb 5-2: device firmware changed
[  231.467000] usb 5-1: new high speed USB device using ehci_hcd and address 6
[  231.588000] usb 5-1: configuration #128 chosen from 1 choice
[  231.608000] usb 5-2: USB disconnect, address 5
[  231.609000] usb-storage: device found at 6
[  231.609000] usb-storage: waiting for device to settle before scanning
[  231.711000] usb 5-2: new high speed USB device using ehci_hcd and address 7
[  231.829000] usb 5-2: configuration #1 chosen from 1 choice
[  231.829000] usb-storage: device found at 7
[  231.829000] usb-storage: waiting for device to settle before scanning
[  236.610000] usb-storage: device scan complete
[  236.829000] usb-storage: device scan complete
[  237.519000] usb 5-2: reset high speed USB device using ehci_hcd and address 7
[  238.687000] usb 5-1: reset high speed USB device using ehci_hcd and address 6
[  238.807000] usb 5-1: can't restore configuration #128 (error=-71)
[  238.807000] usb 5-1: USB disconnect, address 6
[  238.906000] usb 5-2: reset high speed USB device using ehci_hcd and address 7
[  239.021000] usb 5-2: device firmware changed
[  239.122000] usb 5-1: new high speed USB device using ehci_hcd and address 8
[  239.243000] usb 5-1: configuration #128 chosen from 1 choice
[  239.263000] usb 5-2: USB disconnect, address 7
[  239.264000] usb-storage: device found at 8
[  239.264000] usb-storage: waiting for device to settle before scanning
[  239.366000] usb 5-2: new high speed USB device using ehci_hcd and address 9
[  239.485000] usb 5-2: configuration #1 chosen from 1 choice
[  239.485000] usb-storage: device found at 9
[  239.485000] usb-storage: waiting for device to settle before scanning
[  244.265000] usb-storage: device scan complete
[  244.277000]  sda:<7>usb-storage: device scan complete
[  274.379000] usb 5-1: reset high speed USB device using ehci_hcd and address 8
[  284.620000] usb 5-1: reset high speed USB device using ehci_hcd and address 8
[  300.859000] usb 5-1: reset high speed USB device using ehci_hcd and address 8
[  301.098000] usb 5-1: reset high speed USB device using ehci_hcd and address 8
[  311.331000] usb 5-1: reset high speed USB device using ehci_hcd and address 8
[  341.570000] usb 5-1: reset high speed USB device using ehci_hcd and address 8
[  351.802000] usb 5-1: reset high speed USB device using ehci_hcd and address 8
[  368.040000] usb 5-1: reset high speed USB device using ehci_hcd and address 8
[  368.279000] usb 5-1: reset high speed USB device using ehci_hcd and address 8
[  378.513000] usb 5-1: reset high speed USB device using ehci_hcd and address 8

```

```
~$ lsusb
Bus 005 Device 009: ID 1058:0910 Western Digital Technologies, Inc. 
Bus 005 Device 008: ID 0781:7421 SanDisk Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 05ac:0201 Apple Computer, Inc. iMac Keyboard [ALPS M2452]
Bus 002 Device 002: ID 0409:55ab NEC Corp. Hub [iMac/iTouch kbd]
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 046d:c00c Logitech, Inc. Optical Wheel Mouse
Bus 001 Device 001: ID 0000:0000
```

```
~$ cat /proc/bus/usb/devices

T:  Bus=05 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 6
B:  Alloc=  0/800 us ( 0%), #Int=  0, #Iso=  0
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.20-16-lowlatency ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:03:00.3
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   4 Ivl=256ms

T:  Bus=05 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  8 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0781 ProdID=7421 Rev= 7.20
S:  Manufacturer=SanDisk
S:  Product=Sansa e260
S:  SerialNumber=00000000-00000000-7182b394-ed07f606-00000000
C:* #Ifs= 1 Cfg#=128 Atr=c0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
E:  Ad=01(O) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=82(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms

T:  Bus=05 Lev=01 Prnt=01 Port=01 Cnt=02 Dev#=  9 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1058 ProdID=0910 Rev= 1.06
S:  Manufacturer=Western Digital 
S:  Product=External HDD    
S:  SerialNumber=574341505A30323736353934
C:* #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=  2mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
E:  Ad=81(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=02(O) Atr=02(Bulk) MxPS= 512 Ivl=0ms

T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
B:  Alloc=  0/900 us ( 0%), #Int=  0, #Iso=  0
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.20-16-lowlatency ohci_hcd
S:  Product=OHCI Host Controller
S:  SerialNumber=0000:03:00.1
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=255ms

T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
B:  Alloc=  0/900 us ( 0%), #Int=  0, #Iso=  0
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.20-16-lowlatency ohci_hcd
S:  Product=OHCI Host Controller
S:  SerialNumber=0000:03:00.0
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=255ms

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
B:  Alloc=129/900 us (14%), #Int=  2, #Iso=  0
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.20-16-lowlatency uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.1
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=255ms

T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=12  MxCh= 4
D:  Ver= 1.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=0409 ProdID=55ab Rev= 1.00
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   1 Ivl=255ms

T:  Bus=02 Lev=02 Prnt=02 Port=00 Cnt=01 Dev#=  3 Spd=1.5 MxCh= 0
D:  Ver= 1.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=05ac ProdID=0201 Rev= 1.01
S:  Manufacturer=Alps Electric
S:  Product=M2452
C:* #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=01 Driver=usbhid
E:  Ad=81(I) Atr=03(Int.) MxPS=   8 Ivl=10ms

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
B:  Alloc= 93/900 us (10%), #Int=  1, #Iso=  0
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.20-16-lowlatency uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.0
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=255ms

T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=1.5 MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=046d ProdID=c00c Rev=21.10
S:  Manufacturer=Logitech
S:  Product=USB Optical Mouse
C:* #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid
E:  Ad=81(I) Atr=03(Int.) MxPS=   4 Ivl=10ms

```

Hope this gives you some more info - the devices were behaving badly like they normally do when they're plugged into this cardbus...

---

### Post by ukripper on 2007-06-24
I suspect too many devices when connected to the cardbus and transferring data to storage devices attached to it probably having some kind of conflict in Interrupt  assignment. 

If you just connect 1 storage device (usb hdd) to card bus and then try transferring does that make any difference?

---

### Post by coverup on 2007-06-24
Unfortunately it doesn't make any difference.  I would be happy if I could have one at a time working.  Any other ideas about what it could be?  Any information at all is helpful.

---

### Post by coverup on 2007-07-30
Just wanted to say that after posting to linux-usb-users and the like, I was able to get this fixed... by purchasing another USB 2.0 cardbus adaptor.  I purchased a Dynex model which cost twice as much but works beautifully *out of the box*.

I'm keeping the Cables Unlimited around just in case the firewire works by some chance... haven't had a chance to try it on firewire yet.  Another reminder not to go cheap just because it's inexpensive, or try before you buy and make sure there's a return policy.

---

### Post by ukripper on 2007-08-02
> **coverup said:**
> Just wanted to say that after posting to linux-usb-users and the like, I was able to get this fixed... by purchasing another USB 2.0 cardbus adaptor.  I purchased a Dynex model which cost twice as much but works beautifully *out of the box*.

I'm keeping the Cables Unlimited around just in case the firewire works by some chance... haven't had a chance to try it on firewire yet.  Another reminder not to go cheap just because it's inexpensive, or try before you buy and make sure there's a return policy.

Good job mate...That is the spirit never give up.

---

