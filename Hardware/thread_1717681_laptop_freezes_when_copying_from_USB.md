---
title: "laptop freezes when copying from USB"
date: 2011-03-30
forum: Hardware
---

### Post by squeakusmaximus on 2011-03-30
Hi
I have been having a problem when trying to copy either large files or large numbers of small files from the USB in Ubuntu. This happens whether i'm copying from the USB ports or from my sd card reader. It also crashes on different devices, such as a webcam. I can browse the devices just fine, it only happens during data transfer. When it crashes the desktop freezes and I cant see anything indicating an error being written to the logs

I know the ports themselves are okay because there are no problems when I copy from USB in my windows partition. I have had this problem since forever (8.04). I am currently running 10.04 on an Acer Aspire 5738. 

This is the dmesg log when I add a device:

[ 8134.228141] usb 1-4: new high speed USB device using ehci_hcd and address 2
[ 8134.373222] usb 1-4: configuration #1 chosen from 1 choice
[ 8134.373595] scsi8 : SCSI emulation for USB Mass Storage devices
[ 8134.373841] usb-storage: device found at 2
[ 8134.373844] usb-storage: waiting for device to settle before scanning
[ 8139.372362] usb-storage: device scan complete
[ 8139.404328] scsi 8:0:0:0: Direct-Access              Patriot Memory   PMAP PQ: 0 ANSI: 0 CCS
[ 8139.405233] sd 8:0:0:0: Attached scsi generic sg2 type 0
[ 8141.967902] sd 8:0:0:0: [sdb] 31326208 512-byte logical blocks: (16.0 GB/14.9 GiB)
[ 8141.968406] sd 8:0:0:0: [sdb] Write Protect is off
[ 8141.968411] sd 8:0:0:0: [sdb] Mode Sense: 23 00 00 00
[ 8141.968415] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[ 8141.971907] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[ 8141.971914]  sdb: sdb1
[ 8142.018769] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[ 8142.018777] sd 8:0:0:0: [sdb] Attached SCSI removable disk

and details from lsusb:

Bus 001 Device 002: ID 13fe:1e00 Kingston Technology Company Inc. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x13fe Kingston Technology Company Inc.
  idProduct          0x1e00 
  bcdDevice            1.10
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
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              200mA
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
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)


Any help sorting this out would be greatly appreciated!

---

### Post by squeakusmaximus on 2011-03-31
If anyone could even give me an idea of how to add more logging or anywhere else I should be looking for errors, then I could make an attempt at fixing this. At the moment i'm looking at a vertical cliff of a problem with no hand holds, an error message at least would be a starting point

---

### Post by squeakusmaximus on 2011-05-18
I have gone through every log and it records nothing at the moment that it hangs, any ideas?

---

