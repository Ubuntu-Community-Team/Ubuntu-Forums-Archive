---
title: "flash drive error"
date: 2011-01-26
forum: Hardware
---

### Post by Ptj91 on 2011-01-26
I let files copying  to flash drive and gone to the city, when I  returned I found copy manager in half and asks whether to skip, a flash  was unmonted.... linux do not see the flash. Windows is seeing, but can  not access it. hp format tool can not format and instead of 0MB, windows  is seeing 16GB and does not see Kingston, but generic drive (or  something like that) ... even with the cmd i did not have luck because  it was printing ioclt error. i really  dont know what to do with it! 

 linux coud not mount my flash, even mountmanager and gparted does not see it.
```

ptj@MarE ~ $ lspci
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation GT218 [GeForce 210] (rev a2)
01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
02:02.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
02:02.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
02:04.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8110SC/8169SC Gigabit Ethernet (rev 10)

ptj@MarE ~ $ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 007: ID 0e8f:0023 GreenAsia Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 0951:1607 Kingston Technology DataTraveler 100
Bus 001 Device 004: ID 19d2:0031 ONDA Communication S.p.A. ZTE MF636
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

sudo lsusb -v (I cut it):
Bus 001 Device 005: ID 0951:1607 Kingston Technology DataTraveler 100
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0951 Kingston Technology
  idProduct          0x1607 DataTraveler 100
  bcdDevice            1.00
  iManufacturer           1 Kingston
  iProduct                2 DataTraveler 2.0
  iSerial                 3 0014780F9951F96165820AB1
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk (Zip)
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval             255
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval             255
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0000
  (Bus Powered)

```

---

### Post by gordintoronto on 2011-01-26
Time to buy a replacement.

---

### Post by Ptj91 on 2011-01-27
> **gordintoronto said:**
> Time to buy a replacement.

Is it definitive, or you made guess?

---

### Post by gordintoronto on 2011-01-27
I would need to plug the drive into my own computers to be definitive, but you are describing a flash drive which is probably dead.

---

### Post by Ptj91 on 2011-01-28
Yes, but did you read post before where writes "sudo lsub -v" ? I think it is pretty clear that kernel reconize flash. beside windows sees it, but coud not work with it because sees it as raw.

---

