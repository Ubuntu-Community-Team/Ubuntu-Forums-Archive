---
title: "Firewire enclosure don't work"
date: 2005-05-20
forum: Hardware &amp; Laptops
---

### Post by Emerick on 2005-05-20
Hello, i'm new with ubuntu not new with linux. :)
Before i used to work with Mandrake and after that Knoppix.

Here is my problem. I own an old firewire enclosure (bought in 1999), the chipset inside is an Oxford OXFW900. It accepts IDE harddrives and CD/Cdburners.

Before switching to ubuntu this enclosure worked fine with 2.4.x kernel.

I've made several tests and i will show you results after, and i found that my iPod which don't work on ubuntu works great with Knoppix 3.8.2. But my enclosure don't work with Knoppix, i have the same errors for knoppix and ubuntu.

First of all, here is my lspci:
```
emeric@penguin:~$ lspci
0000:00:00.0 Host bridge: Intel Corp. 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 02)
0000:00:01.0 PCI bridge: Intel Corp. 82815 815 Chipset AGP Bridge (rev 02)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 03)
0000:00:1f.0 ISA bridge: Intel Corp. 82801BAM ISA Bridge (LPC) (rev 03)
0000:00:1f.1 IDE interface: Intel Corp. 82801BAM IDE U100 (rev 03)
0000:00:1f.2 USB Controller: Intel Corp. 82801BA/BAM USB (Hub #1) (rev 03)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 Go] (rev b2)
0000:02:03.0 Multimedia audio controller: ESS Technology ES1983S Maestro-3i PCI Audio Accelerator (rev 10)
0000:02:06.0 Network controller: Intel Corp. PRO/Wireless 2200BG (rev 05)
0000:02:0f.0 CardBus bridge: Texas Instruments PCI4451 PC card Cardbus Controller
0000:02:0f.1 CardBus bridge: Texas Instruments PCI4451 PC card Cardbus Controller
0000:02:0f.2 FireWire (IEEE 1394): Texas Instruments PCI4451 IEEE-1394 Controller
0000:07:00.0 Ethernet controller: 3Com Corporation 3cCFE575BT Megahertz 10/100 LAN CardBus [Cyclone] (rev 01) 
```

tail -f /var/log/syslog when i plug-in my enclosure:
```
May 20 12:10:11 localhost kernel: ohci1394: fw-host0: SelfID received, but NodeID invalid (probably new bus reset occurred): 0000FFC0
May 20 12:10:11 localhost kernel: ieee1394: Node added: ID:BUS[0-01:1023]  GUID[0030e000e0008db2]
May 20 12:10:11 localhost kernel: ieee1394: The root node is not cycle master capable; selecting a new root node and resetting...
May 20 12:10:12 localhost kernel: ieee1394: Node changed: 0-01:1023 -> 0-00:1023
May 20 12:10:12 localhost kernel: ieee1394: Node changed: 0-00:1023 -> 0-01:1023
May 20 12:10:12 localhost kernel: scsi1 : SCSI emulation for IEEE-1394 SBP-2 Devices
May 20 12:10:12 localhost ieee1394.agent[11263]: ... no drivers for IEEE1394 product 0x000000/0x000000/0x000000
May 20 12:10:12 localhost ieee1394.agent[11276]:      sbp2: already loaded
May 20 12:10:33 localhost kernel: ieee1394: sbp2: Error logging into SBP-2 device - login timed-out
May 20 12:10:33 localhost kernel: sbp2: probe of 0030e000e0008db2-1 failed with error -16 
```

/var/log/syslog when i plug my iPod.
```
May 20 13:07:56 localhost kernel: ieee1394: Node added: ID:BUS[0-01:1023]  GUID[000a27000277ee30]
May 20 13:07:56 localhost kernel: ieee1394: The root node is not cycle master capable; selecting a new root node and  resetting...
May 20 13:07:56 localhost kernel: ieee1394: Node changed: 0-01:1023 -> 0-00:1023
May 20 13:07:56 localhost kernel: ieee1394: Node changed: 0-00:1023 -> 0-01:1023 
```

And when i unplug it
```
May 20 13:10:23 localhost kernel: ieee1394: Node changed: 0-01:1023 -> 0-00:1023
May 20 13:10:23 localhost kernel: ieee1394: Node suspended: ID:BUS[0-00:1023]  GUID[000a27000277ee30]
```

I've tried with 2.6.11 kernel from ubuntu, and the result is same.  ](*,) 

Anyone have idea for this ?

Sorry if my english isn't as good as it should be, but english isn't my mother language.

EDIT: After some other search on the Internet, i found that i needed ide-scsi module.
Now i can use my iPod through firewire, but my enclosure still don't work.  :?

---

### Post by Emerick on 2005-05-26
I've found that with kernel included in breezy, my enclosure work fine.
But i can't stay with this kernel because the package restricted-modules isn't available for this kernel. And i need it for nvidia drivers.

---

