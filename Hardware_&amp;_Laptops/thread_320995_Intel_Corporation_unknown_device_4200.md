---
title: "Intel Corporation unknown device 4200"
date: 2006-12-18
forum: Hardware &amp; Laptops
---

### Post by ecarreras on 2006-12-18
Hi,
I can't configure my wireless card, the lspci output is:
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 21)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 21)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]
**02:04.0 Network controller: Intel Corporation Unknown device 4200 (rev 05)**
02:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
02:09.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
02:09.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller

I load ipw2200 but eth1 device is not created :(

Somebody  can help me? thanks

---

### Post by rbalfour on 2006-12-18
> **ecarreras said:**
> Hi,
**02:04.0 Network controller: Intel Corporation Unknown device 4200 (rev 05)**


Do you know what the device is suppose to be? Is this a laptop or Desktop?
What is the model and series number?

---

### Post by ecarreras on 2006-12-18
Well, before was an intel 2200bg, I sent the laptop to de benq store because I've a problem with the screen, and I think that they changed the motherboard :s but they didn't say me anything :(

Before to sent the laptop to Benq store I load ipw2200 and the wireless card worked. Now I load the ipw2200 driver and no eth1 is created.

P.S. Sorry for my english.


Thanks

hal-device says:
52: udi = '/org/freedesktop/Hal/devices/pci_8086_4200'
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_4200'  (string)
  linux.subsystem = 'pci'  (string)
  linux.hotplug_type = 1  (0x1)  (int)
  pci.subsys_product = 'Unknown (0x2701)'  (string)
  pci.subsys_vendor = 'Intel Corporation'  (string)
  info.product = 'Unknown (0x4200)'  (string)
  pci.product = 'Unknown (0x4200)'  (string)
  info.vendor = 'Intel Corporation'  (string)
  pci.vendor = 'Intel Corporation'  (string)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 128  (0x80)  (int)
  pci.device_class = 2  (0x2)  (int)
  pci.subsys_vendor_id = 32902  (0x8086)  (int)
  pci.subsys_product_id = 9985  (0x2701)  (int)
  pci.vendor_id = 32902  (0x8086)  (int)
  pci.product_id = 16896  (0x4200)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1e.0/0000:02:04.0'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_2448'  (string)
  info.bus = 'pci'  (string)
  linux.sysfs_path_device = '/sys/devices/pci0000:00/0000:00:1e.0/0000:02:04.0'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1e.0/0000:02:04.0'  (string)

---

### Post by rbalfour on 2006-12-18
> **ecarreras said:**
> Well, before was an intel 2200bg, I sent the laptop to de benq store because I've a problem with the screen, and I think that they changed the motherboard :s but they didn't say me anything :(

Before to sent the laptop to Benq store I load ipw2200 and the wireless card worked. Now I load the ipw2200 driver and no eth1 is created.

P.S. Sorry for my english.


Thanks

hal-device says:
52: udi = '/org/freedesktop/Hal/devices/pci_8086_4200'
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_4200'  (string)
  linux.subsystem = 'pci'  (string)
  linux.hotplug_type = 1  (0x1)  (int)
  pci.subsys_product = 'Unknown (0x2701)'  (string)
  pci.subsys_vendor = 'Intel Corporation'  (string)
  info.product = 'Unknown (0x4200)'  (string)
  pci.product = 'Unknown (0x4200)'  (string)
  info.vendor = 'Intel Corporation'  (string)
  pci.vendor = 'Intel Corporation'  (string)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 128  (0x80)  (int)
  pci.device_class = 2  (0x2)  (int)
  pci.subsys_vendor_id = 32902  (0x8086)  (int)
  pci.subsys_product_id = 9985  (0x2701)  (int)
  pci.vendor_id = 32902  (0x8086)  (int)
  pci.product_id = 16896  (0x4200)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1e.0/0000:02:04.0'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_2448'  (string)
  info.bus = 'pci'  (string)
  linux.sysfs_path_device = '/sys/devices/pci0000:00/0000:00:1e.0/0000:02:04.0'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1e.0/0000:02:04.0'  (string)

If it worked BEFORE it went for repairs. Maybe some else broke or the card isn't connect properly. Maybe send it back and tell them the wireless is now broken.

---

