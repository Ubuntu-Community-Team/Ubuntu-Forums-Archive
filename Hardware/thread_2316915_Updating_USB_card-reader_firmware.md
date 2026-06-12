---
title: "Updating USB card-reader firmware?"
date: 2016-03-11
forum: Hardware
---

### Post by bcschmerker on 2016-03-11
I am looking into the problem of updating the firmware for the flash-drive component of a Mitsumi® FA404M; the Compact Flash/Microdrive and SecureDigital/MultiMediaCard/MemoryStick interfaces were subcontracted to a Carry Computer Engineering, Ltd., and have their insert slots above that for a standard 3.5" 80T/2S/4D disquette.  A test with an 8 GiB SanDisk® Ultra&#8482; SDHC in the SD/MMC/MS slot came up negative for detection by the Hot Rod gPC, even though the FA404M acknowledged with a dim red activity telltale (normally bright green when the disquette motor runs).

Reported ID by lsusb:
ID 07cc:0301 Carry Computer Eng., Co., Ltd 6-in-1 Card Reader

Detail information in Disk Utility:
/dev/sdc USB2.0 CardReader CF RW
/dev/sdd USB2.0 CardReader Combo RW
Firmware Version: 0814
Serial Number: 392673724128
Connection:  USB at 480.0 Mb/s

From forums for discontinued version of Microsoft® Windows®, it appears that the FA404M required a firmware upgrade to properly handle SDHC and perhaps high-capacity updates of the other physical formats supported.  How does one go about this, given an appropriate new firmware blob in the context of an MS-DOS/WIN Application (courtesy Owltech, Ltd.)?

**Update:**  [s]Owltech may not necessarily be an option, as[/s] FA404M-405MX_SDHC_FW9325.exe, a Windows Installer app, apparently works only in Microsoft® Windows® 5.*n*.  An attempt to update it on the Asus® CM1630-06 running Windows 7.0.8001 (Kernel 6.1.7601) crashed with a device not found error despite the device being recognized by the Windows Device Manager.

**Update 2:**  Archive Manager succeeded in extracting the blob 9325.bin.  What subcommand of sudo will be necessary to write the FA404M[s], assuming I can locate the correct /dev/sg*n*[/s]?

**Update 3: **  The binary dfu-util cannot read or write the Carry Computer microcontroller firmware in the FA404M.  Any workarounds?

---

### Post by bcschmerker on 2016-03-29
Bump!  I have the following detail from sudo lsusb -d 07cc:0301 -v:
```

Bus 002 Device 002: ID 07cc:0301 Carry Computer Eng., Co., Ltd 6-in-1 Card Reader
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x07cc Carry Computer Eng., Co., Ltd
  idProduct          0x0301 6-in-1 Card Reader
  bcdDevice            0.05
  iManufacturer           1         Ltd
  iProduct                2 Winter Ver1.3   
  iSerial                 3 392673724128
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
      bInterfaceProtocol     80 Bulk-Only
      iInterface              4 1.06.69.0630
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
Also, as of 2 April 2016, I found the CF/MD fully functional through at least 16 GiB, using a Duracell® Pro Photo 600X UDMA module.  No such luck on the SD/MMC side yet.

---

