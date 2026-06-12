---
title: "Unable to format a USB pen drive"
date: 2011-05-03
forum: Hardware
---

### Post by lz1dsb on 2011-05-03
I was trying to install the .iso image of Natty Nahrwal on a USB pen drive when the program crashed. After that wasn't able to format it under Linus, so I tried it on my windows machine. Windows tells me I have to format the pen, and 1 sec later tells me  "Windows can't format the drive" or something. Linux tells me it can't  mount the drive.
In the /var/log/messages this is what I see when I plug in my drive:
```
May  4 00:01:49 boyan-laptop kernel: [730951.370157] usb 2-1: new high speed USB device using ehci_hcd and address 17
May  4 00:01:49 boyan-laptop kernel: [730951.524040] usb 2-1: configuration #1 chosen from 1 choice
May  4 00:01:49 boyan-laptop kernel: [730951.528249] scsi17 : SCSI emulation for USB Mass Storage devices
May  4 00:01:54 boyan-laptop kernel: [730956.952188] scsi 17:0:0:0: Direct-Access     Lexar    USB Flash Drive  1100 PQ: 0 ANSI: 0 CCS
May  4 00:01:54 boyan-laptop kernel: [730956.952901] sd 17:0:0:0: Attached scsi generic sg2 type 0
May  4 00:01:54 boyan-laptop kernel: [730956.959780] sd 17:0:0:0: [sdb] 15663104 512-byte logical blocks: (8.01 GB/7.46 GiB)
May  4 00:01:54 boyan-laptop kernel: [730956.960734] sd 17:0:0:0: [sdb] Write Protect is off
May  4 00:01:54 boyan-laptop kernel: [730956.965316]  sdb: unknown partition table
May  4 00:01:54 boyan-laptop kernel: [730956.973815] sd 17:0:0:0: [sdb] Attached SCSI removable disk

```It pretty much looks like the situation described in this thread:
[http://ubuntuforums.org/showthread.php?t=861579](http://ubuntuforums.org/showthread.php?t=861579)

When I try sudo gparted /dev/sdb I get:
```
bsotirov@boyan-laptop:~$ sudo gparted /dev/sdb
======================
libparted : 1.8.8.1.159-1e0e
======================
/dev/sdb: unbekannte Partitionstabelle //unknown partition table

```So apparently the device is visible from the system but the formatting is totally messed up. I guess that this happened when UNbootin crashed while writing on it.
```
bsotirov@boyan-laptop:~$ sudo lsusb -vd 05dc:a768

Bus 002 Device 017: ID 05dc:a768 Lexar Media, Inc. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x05dc Lexar Media, Inc.
  idProduct          0xa768 
  bcdDevice           11.00
  iManufacturer           1 Lexar
  iProduct                2 USB Flash Drive
  iSerial                 3 K5X9K9XVHT6F1QURYNLK
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
```Is there a way to recover the USB pen drive? Something like low level format... I read about some application I can use in order to recover the data on the drive, but I don't need that. I would like to reformat it so that I can continue using it. Is that possible? And is it really possible for an application such as UNbootin to break a USB drive?
Frankly this is the first time such thing happens to me, but off course I don't make Live USBs regularly...

---

### Post by lz1dsb on 2011-05-03
I just forgot to mention that I'm not able to mount the USB pen drive... But I guess it's a bit obvious in this situation...:-s

---

### Post by lz1dsb on 2011-06-08
After a lot of attempts to fix that pen drive I gave up. To me it looks like that the memory partition was totally messed up and only the USB controller was working properly...:(

---

