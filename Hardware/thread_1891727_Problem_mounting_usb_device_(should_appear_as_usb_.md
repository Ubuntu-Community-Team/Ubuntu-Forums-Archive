---
title: "Problem mounting usb device (should appear as usb storage)"
date: 2011-12-06
forum: Hardware
---

### Post by nigelross on 2011-12-06
I am having problems mounting an OWL wireless electricity meter,
that should be seen as a usb storage device, at least on windows.
I would like to be able to access the data on the device to monitor my generated electricity, but want to do this from ubuntu, not windows.
However, it seems that it is not being recognised, and I do not know how to proceed, as the messages provided in dmesg etc seem to stop before providing the name of the device so that I can try & mount.

Below I include the output from dmesg, /var/log/syslog, lsusb & ls /dev/disk, as this might help.
I am running 11.04, but would really want to be able to do this from a server with an previous version of ubuntu too.
uname -a
Linux nigel-laptop 2.6.38-13-generic #53-Ubuntu SMP Mon Nov 28 19:23:39 UTC 2011 i686 i686 i386 GNU/Linux

Any guidance gratefully received...

dmesg:
[28733.944151] usb 5-1: USB disconnect, address 2
[28735.844095] usb 5-1: new full speed USB device using uhci_hcd and address 3
/var/log/syslog:
Dec  6 13:17:17 nigel-laptop kernel: [28733.944151] usb 5-1: USB disconnect, address 2
Dec  6 13:17:19 nigel-laptop kernel: [28735.844095] usb 5-1: new full speed USB device using uhci_hcd and address 3

lsusb does detect the device:
nigel@nigel-laptop:~/Downloads$ sudo lsusb -v -s 5:3
[sudo] password for nigel: 

Bus 005 Device 003: ID 0fde:ca05  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0fde 
  idProduct          0xca05 
  bcdDevice            1.00
  iManufacturer           1 Silicon Labs
  iProduct                2 OWL Wireless Electricity Monitor USB version is connected
  iSerial                 3 001EDB84
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
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              2 OWL Wireless Electricity Monitor USB version is connected
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
Device Status:     0x0000
  (Bus Powered)



finally, nothing shows up looking at /dev/disk....
nigel@nigel-laptop:~$ ls -laR /dev/disk
/dev/disk:
total 0
drwxr-xr-x  6 root root  120 2011-12-05 10:03 .
drwxr-xr-x 19 root root 4560 2011-12-06 12:39 ..
drwxr-xr-x  2 root root  620 2011-12-06 12:39 by-id
drwxr-xr-x  2 root root  120 2011-12-05 22:47 by-label
drwxr-xr-x  2 root root  260 2011-12-06 12:39 by-path
drwxr-xr-x  2 root root  180 2011-12-06 11:48 by-uuid

/dev/disk/by-id:
total 0
drwxr-xr-x 2 root root 620 2011-12-06 12:39 .
drwxr-xr-x 6 root root 120 2011-12-05 10:03 ..
lrwxrwxrwx 1 root root   9 2011-12-06 11:20 ata-HL-DT-ST_DVDRAM_GSA-T40N_K0184J03659 -> ../../sr0
lrwxrwxrwx 1 root root   9 2011-12-05 10:04 ata-TOSHIBA_MK1646GSX_58R4P6EAT -> ../../sda
lrwxrwxrwx 1 root root  10 2011-12-05 10:04 ata-TOSHIBA_MK1646GSX_58R4P6EAT-part1 -> ../../sda1
lrwxrwxrwx 1 root root  10 2011-12-05 10:04 ata-TOSHIBA_MK1646GSX_58R4P6EAT-part2 -> ../../sda2
lrwxrwxrwx 1 root root  10 2011-12-05 10:04 ata-TOSHIBA_MK1646GSX_58R4P6EAT-part3 -> ../../sda3
lrwxrwxrwx 1 root root  10 2011-12-05 10:04 ata-TOSHIBA_MK1646GSX_58R4P6EAT-part4 -> ../../sda4
lrwxrwxrwx 1 root root  10 2011-12-05 10:04 ata-TOSHIBA_MK1646GSX_58R4P6EAT-part5 -> ../../sda5
lrwxrwxrwx 1 root root  10 2011-12-05 10:04 ata-TOSHIBA_MK1646GSX_58R4P6EAT-part6 -> ../../sda6
lrwxrwxrwx 1 root root  10 2011-12-05 10:04 ata-TOSHIBA_MK1646GSX_58R4P6EAT-part7 -> ../../sda7
lrwxrwxrwx 1 root root  10 2011-12-05 10:04 ata-TOSHIBA_MK1646GSX_58R4P6EAT-part8 -> ../../sda8
lrwxrwxrwx 1 root root   9 2011-12-05 10:04 scsi-SATA_TOSHIBA_MK1646G_58R4P6EAT -> ../../sda
lrwxrwxrwx 1 root root  10 2011-12-05 10:04 scsi-SATA_TOSHIBA_MK1646G_58R4P6EAT-part1 -> ../../sda1
lrwxrwxrwx 1 root root  10 2011-12-05 10:04 scsi-SATA_TOSHIBA_MK1646G_58R4P6EAT-part2 -> ../../sda2
lrwxrwxrwx 1 root root  10 2011-12-05 10:04 scsi-SATA_TOSHIBA_MK1646G_58R4P6EAT-part3 -> ../../sda3
lrwxrwxrwx 1 root root  10 2011-12-05 10:04 scsi-SATA_TOSHIBA_MK1646G_58R4P6EAT-part4 -> ../../sda4
lrwxrwxrwx 1 root root  10 2011-12-05 10:04 scsi-SATA_TOSHIBA_MK1646G_58R4P6EAT-part5 -> ../../sda5
lrwxrwxrwx 1 root root  10 2011-12-05 10:04 scsi-SATA_TOSHIBA_MK1646G_58R4P6EAT-part6 -> ../../sda6
lrwxrwxrwx 1 root root  10 2011-12-05 10:04 scsi-SATA_TOSHIBA_MK1646G_58R4P6EAT-part7 -> ../../sda7
lrwxrwxrwx 1 root root  10 2011-12-05 10:04 scsi-SATA_TOSHIBA_MK1646G_58R4P6EAT-part8 -> ../../sda8
lrwxrwxrwx 1 root root   9 2011-12-06 12:39 usb-HTC_Android_Phone_SH0B7RT00652-0:0 -> ../../sdb
lrwxrwxrwx 1 root root   9 2011-12-05 10:04 wwn-0x50000391023068b1 -> ../../sda
lrwxrwxrwx 1 root root  10 2011-12-05 10:04 wwn-0x50000391023068b1-part1 -> ../../sda1
lrwxrwxrwx 1 root root  10 2011-12-05 10:04 wwn-0x50000391023068b1-part2 -> ../../sda2
lrwxrwxrwx 1 root root  10 2011-12-05 10:04 wwn-0x50000391023068b1-part3 -> ../../sda3
lrwxrwxrwx 1 root root  10 2011-12-05 10:04 wwn-0x50000391023068b1-part4 -> ../../sda4
lrwxrwxrwx 1 root root  10 2011-12-05 10:04 wwn-0x50000391023068b1-part5 -> ../../sda5
lrwxrwxrwx 1 root root  10 2011-12-05 10:04 wwn-0x50000391023068b1-part6 -> ../../sda6
lrwxrwxrwx 1 root root  10 2011-12-05 10:04 wwn-0x50000391023068b1-part7 -> ../../sda7
lrwxrwxrwx 1 root root  10 2011-12-05 10:04 wwn-0x50000391023068b1-part8 -> ../../sda8

/dev/disk/by-label:
total 0
drwxr-xr-x 2 root root 120 2011-12-05 22:47 .
drwxr-xr-x 6 root root 120 2011-12-05 10:03 ..
lrwxrwxrwx 1 root root  10 2011-12-05 10:04 ACER -> ../../sda2
lrwxrwxrwx 1 root root  10 2011-12-05 10:04 DATA -> ../../sda3
lrwxrwxrwx 1 root root  10 2011-12-05 10:04 PQSERVICE -> ../../sda1
lrwxrwxrwx 1 root root   9 2011-12-06 11:20 Ubuntu\x2010.04.3\x20LTS\x20i386 -> ../../sr0

/dev/disk/by-path:
total 0
drwxr-xr-x 2 root root 260 2011-12-06 12:39 .
drwxr-xr-x 6 root root 120 2011-12-05 10:03 ..
lrwxrwxrwx 1 root root   9 2011-12-06 12:39 pci-0000:00:1d.7-usb-0:5:1.0-scsi-0:0:0:0 -> ../../sdb
lrwxrwxrwx 1 root root   9 2011-12-06 11:20 pci-0000:00:1f.1-scsi-0:0:0:0 -> ../../sr0
lrwxrwxrwx 1 root root   9 2011-12-05 10:04 pci-0000:00:1f.2-scsi-0:0:0:0 -> ../../sda
lrwxrwxrwx 1 root root  10 2011-12-05 10:04 pci-0000:00:1f.2-scsi-0:0:0:0-part1 -> ../../sda1
lrwxrwxrwx 1 root root  10 2011-12-05 10:04 pci-0000:00:1f.2-scsi-0:0:0:0-part2 -> ../../sda2
lrwxrwxrwx 1 root root  10 2011-12-05 10:04 pci-0000:00:1f.2-scsi-0:0:0:0-part3 -> ../../sda3
lrwxrwxrwx 1 root root  10 2011-12-05 10:04 pci-0000:00:1f.2-scsi-0:0:0:0-part4 -> ../../sda4
lrwxrwxrwx 1 root root  10 2011-12-05 10:04 pci-0000:00:1f.2-scsi-0:0:0:0-part5 -> ../../sda5
lrwxrwxrwx 1 root root  10 2011-12-05 10:04 pci-0000:00:1f.2-scsi-0:0:0:0-part6 -> ../../sda6
lrwxrwxrwx 1 root root  10 2011-12-05 10:04 pci-0000:00:1f.2-scsi-0:0:0:0-part7 -> ../../sda7
lrwxrwxrwx 1 root root  10 2011-12-05 10:04 pci-0000:00:1f.2-scsi-0:0:0:0-part8 -> ../../sda8

/dev/disk/by-uuid:
total 0
drwxr-xr-x 2 root root 180 2011-12-06 11:48 .
drwxr-xr-x 6 root root 120 2011-12-05 10:03 ..
lrwxrwxrwx 1 root root  10 2011-12-05 10:04 409ef84c-585c-4b41-a58c-7f258f83e8b0 -> ../../sda7
lrwxrwxrwx 1 root root  10 2011-12-05 10:04 474f6140-099b-45f2-84bf-93603d4513a5 -> ../../sda6
lrwxrwxrwx 1 root root  10 2011-12-05 10:04 52825BE4825BCADD -> ../../sda3
lrwxrwxrwx 1 root root  10 2011-12-05 10:04 58B83ABFB83A9C06 -> ../../sda2
lrwxrwxrwx 1 root root  10 2011-12-05 10:04 7b02a250-49b0-40af-a8b5-def21d558739 -> ../../sda5
lrwxrwxrwx 1 root root  10 2011-12-05 10:04 A20A-9608 -> ../../sda1
lrwxrwxrwx 1 root root  10 2011-12-05 10:04 b40867ed-4584-40fa-b64a-9138ad630b52 -> ../../sda8
nigel@nigel-laptop:~$

---

