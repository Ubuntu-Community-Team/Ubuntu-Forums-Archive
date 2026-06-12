---
title: "Sanyo voice recorder as USB storage device not recognised"
date: 2014-09-10
forum: Hardware
---

### Post by linuxed2 on 2014-09-10
I have a sanyo voice recorder...old model ICR-S250RM 128mb i think file system is FAT12 

am running Ubuntu 10.04 on a Dell Dimension desktop

It will not mount nor be recognized except for a couple of seconds when plugged in it will show up "Sanyo corp"  under lsusb command. then it vanishes unless plugged in again

Please give me a solution someone...if it is possible....is a hassle just to dive into Windows just for sake of Linux not seeing this device.

(Sorry I didn't do this earlier) This is output of lsusb -v

```
Bus 001 Device 021: ID 0474:010e Sanyo Electric Co., Ltd 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            8 Mass Storage
  bDeviceSubClass         2 SFF-8020i, MMC-2 (ATAPI)
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0474 Sanyo Electric Co., Ltd
  idProduct          0x010e 
  bcdDevice            0.00
  iManufacturer           1 
  iProduct                2 
  iSerial                 3 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xc0
      Self Powered
    MaxPower              500mA
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
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

```



Under dmesg command (with no other usb devices plugged in except mouse and keyboard) I get :-


```

[35290.137039] usb 1-7: new high speed USB device using ehci_hcd and address 7
[35290.272841] usb 1-7: configuration #1 chosen from 1 choice
[35290.273792] scsi5 : SCSI emulation for USB Mass Storage devices
[35290.274119] usb-storage: device found at 7
[35290.274123] usb-storage: waiting for device to settle before scanning
[35292.274245] usb 1-7: USB disconnect, address 7
[35292.849049] usb 2-7: new full speed USB device using ohci_hcd and address 5
[35293.065120] usb 2-7: configuration #1 chosen from 1 choice
[35293.070139] scsi6 : SCSI emulation for USB Mass Storage devices
[35293.070595] usb-storage: device found at 5
[35293.070599] usb-storage: waiting for device to settle before scanning
[35295.064381] usb 2-7: USB disconnect, address 5
[35323.381050] usb 1-7: new high speed USB device using ehci_hcd and address 9
[35323.515811] usb 1-7: configuration #1 chosen from 1 choice
[35323.520231] scsi7 : SCSI emulation for USB Mass Storage devices
[35323.520698] usb-storage: device found at 9
[35323.520703] usb-storage: waiting for device to settle before scanning
[35325.518233] usb 1-7: USB disconnect, address 9
[35326.094166] usb 2-7: new full speed USB device using ohci_hcd and address 6
[35326.309124] usb 2-7: configuration #1 chosen from 1 choice
[35326.312517] scsi8 : SCSI emulation for USB Mass Storage devices
[35326.312860] usb-storage: device found at 6
[35326.312864] usb-storage: waiting for device to settle before scanning
[35328.308311] usb 2-7: USB disconnect, address 6
[35348.364069] usb 1-7: new high speed USB device using ehci_hcd and address 11
[35348.501074] usb 1-7: configuration #1 chosen from 1 choice
[35348.502611] scsi9 : SCSI emulation for USB Mass Storage devices
[35348.502927] usb-storage: device found at 11
[35348.502931] usb-storage: waiting for device to settle before scanning
[35350.500605] usb 1-7: USB disconnect, address 11
[35351.080079] usb 2-7: new full speed USB device using ohci_hcd and address 7
[35351.296140] usb 2-7: configuration #1 chosen from 1 choice
[35351.300349] scsi10 : SCSI emulation for USB Mass Storage devices
[35351.300727] usb-storage: device found at 7
[35351.300731] usb-storage: waiting for device to settle before scanning
[35353.300790] usb 2-7: USB disconnect, address 7
[37525.556052] usb 1-7: new high speed USB device using ehci_hcd and address 13
[37525.692693] usb 1-7: configuration #1 chosen from 1 choice
[37525.693605] scsi11 : SCSI emulation for USB Mass Storage devices
[37525.695074] usb-storage: device found at 13
[37525.695076] usb-storage: waiting for device to settle before scanning
[37527.694097] usb 1-7: USB disconnect, address 13
[37528.268427] usb 2-7: new full speed USB device using ohci_hcd and address 8
[37528.484133] usb 2-7: configuration #1 chosen from 1 choice
[37528.487216] scsi12 : SCSI emulation for USB Mass Storage devices
[37528.487535] usb-storage: device found at 8
[37528.487539] usb-storage: waiting for device to settle before scanning
[37530.484325] usb 2-7: USB disconnect, address 8
[37568.544060] usb 1-7: new high speed USB device using ehci_hcd and address 15
[37568.681181] usb 1-7: configuration #1 chosen from 1 choice
[37568.682193] scsi13 : SCSI emulation for USB Mass Storage devices
[37568.682396] usb-storage: device found at 15
[37568.682400] usb-storage: waiting for device to settle before scanning
[37570.681737] usb 1-7: USB disconnect, address 15
[37571.257040] usb 2-7: new full speed USB device using ohci_hcd and address 9
[37571.476092] usb 2-7: configuration #1 chosen from 1 choice
[37571.479194] scsi14 : SCSI emulation for USB Mass Storage devices
[37571.479530] usb-storage: device found at 9
[37571.479534] usb-storage: waiting for device to settle before scanning
[37573.471926] usb 2-7: USB disconnect, address 9
[37603.633054] usb 1-7: new high speed USB device using ehci_hcd and address 17
[37603.768050] usb 1-7: configuration #1 chosen from 1 choice
[37603.769053] scsi15 : SCSI emulation for USB Mass Storage devices
[37603.769465] usb-storage: device found at 17
[37603.769471] usb-storage: waiting for device to settle before scanning
[37605.770233] usb 1-7: USB disconnect, address 17
[37606.345798] usb 2-7: new full speed USB device using ohci_hcd and address 10
[37606.561209] usb 2-7: configuration #1 chosen from 1 choice
[37606.564424] scsi16 : SCSI emulation for USB Mass Storage devices
[37606.567147] usb-storage: device found at 10
[37606.567153] usb-storage: waiting for device to settle before scanning
[37608.560390] usb 2-7: USB disconnect, address 10
[37765.864061] usb 1-7: new high speed USB device using ehci_hcd and address 19
[37766.001058] usb 1-7: configuration #1 chosen from 1 choice
[37766.002223] scsi17 : SCSI emulation for USB Mass Storage devices
[37766.002482] usb-storage: device found at 19
[37766.002486] usb-storage: waiting for device to settle before scanning
[37768.002844] usb 1-7: USB disconnect, address 19
[37768.577049] usb 2-7: new full speed USB device using ohci_hcd and address 11
[37768.796109] usb 2-7: configuration #1 chosen from 1 choice
[37768.799193] scsi18 : SCSI emulation for USB Mass Storage devices
[37768.799517] usb-storage: device found at 11
[37768.799521] usb-storage: waiting for device to settle before scanning
[37770.792971] usb 2-7: USB disconnect, address 11
[38934.268908] usb 1-7: new high speed USB device using ehci_hcd and address 21
[38934.403816] usb 1-7: configuration #1 chosen from 1 choice
[38934.415167] scsi19 : SCSI emulation for USB Mass Storage devices
[38934.421860] usb-storage: device found at 21
[38934.421866] usb-storage: waiting for device to settle before scanning
[38936.404742] usb 1-7: USB disconnect, address 21
[38936.986591] usb 2-7: new full speed USB device using ohci_hcd and address 12
[38937.201102] usb 2-7: configuration #1 chosen from 1 choice
[38937.204715] scsi20 : SCSI emulation for USB Mass Storage devices
[38937.206481] usb-storage: device found at 12
[38937.206487] usb-storage: waiting for device to settle before scanning
[38939.204917] usb 2-7: USB disconnect, address 12
[38967.265610] usb 1-8: USB disconnect, address 6
[38967.320125] wlan0: deauthenticating from 40:cb:a8:69:b1:d8 by local choice (reason=3)
[38984.754102] usb 2-5: USB disconnect, address 4
[38984.754418] usblp0: removed
[39038.384116] usb 1-7: new high speed USB device using ehci_hcd and address 23
[39038.520774] usb 1-7: configuration #1 chosen from 1 choice
[39038.522741] scsi21 : SCSI emulation for USB Mass Storage devices
[39038.523065] usb-storage: device found at 23
[39038.523069] usb-storage: waiting for device to settle before scanning

```

---

