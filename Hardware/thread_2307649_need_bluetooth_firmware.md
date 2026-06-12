---
title: "need bluetooth firmware"
date: 2015-12-27
forum: Hardware
---

### Post by virgosun on 2015-12-27
dmesg -k | bluetooth

```


[   13.679157] Bluetooth: hci0: BCM: chip id 86
[   13.679162] Bluetooth: hci0: BCM (003.001.009) build 0115
[   13.679174] bluetooth hci0: Direct firmware load for brcm/BCM.hcd failed with error -2
[   13.679176] Bluetooth: hci0: BCM: Patch brcm/BCM.hcd not found


```

lsusb -v | grep bluetooth

```


Bus 001 Device 003: ID 0489:e079 Foxconn / Hon Hai 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass          255 Vendor Specific Class
  bDeviceSubClass         1 
  bDeviceProtocol         1 
  bMaxPacketSize0        64
  idVendor           0x0489 Foxconn / Hon Hai
  idProduct          0xe079 
  bcdDevice            1.12
  iManufacturer           1 Broadcom Corp
  iProduct                2 BCM2045A0
  iSerial                 3 40B89AF8538E
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          218
    bNumInterfaces          4
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      1 
      bInterfaceProtocol      1 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      1 
      bInterfaceProtocol      1 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       1
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      1 
      bInterfaceProtocol      1 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0009  1x 9 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0009  1x 9 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       2
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      1 
      bInterfaceProtocol      1 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0011  1x 17 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0011  1x 17 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       3
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      1 
      bInterfaceProtocol      1 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0019  1x 25 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0019  1x 25 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       4
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      1 
      bInterfaceProtocol      1 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0021  1x 33 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0021  1x 33 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       5
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      1 
      bInterfaceProtocol      1 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0031  1x 49 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0031  1x 49 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0020  1x 32 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x04  EP 4 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0020  1x 32 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        3
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass       254 Application Specific Interface
      bInterfaceSubClass      1 Device Firmware Update
      bInterfaceProtocol      1 
      iInterface              0 
      Device Firmware Upgrade Interface Descriptor:
        bLength                             9
        bDescriptorType                    33
        bmAttributes                        5
          Will Not Detach
          Manifestation Tolerant
          Upload Unsupported
          Download Supported
        wDetachTimeout                   5000 milliseconds
        wTransferSize                      64 bytes
        bcdDFUVersion                   1.10
Device Status:     0x0001
  Self Powered


```

---

### Post by jeremy31 on 2015-12-27
[http://askubuntu.com/questions/632336/bluetooth-broadcom-43142-isnt-working-on-ubuntu/632348#632348](http://askubuntu.com/questions/632336/bluetooth-broadcom-43142-isnt-working-on-ubuntu/632348#632348)
Search the bcbtums inf file from the post for e079 until you see [RAMUSBE079.CopyList]
Below that should be a file name followed by .hex find the same file in the folder that had the bcbtums and use Jesse Sung's hex2hcd program to convert it to BCM.hcd
Then ```
sudo cp BCM.hcd /lib/firmware/brcm/BCM.hcd
sudo modprobe -r btusb
sudo modprobe btusb
```

Bluetooth should work

---

### Post by virgosun on 2015-12-27
I am having a Win 10 hex on my dual boot system but not work. Will try your Win 81 tomorrow thanks

---

### Post by virgosun on 2015-12-27
> **jeremy31 said:**
> [http://askubuntu.com/questions/632336/bluetooth-broadcom-43142-isnt-working-on-ubuntu/632348#632348](http://askubuntu.com/questions/632336/bluetooth-broadcom-43142-isnt-working-on-ubuntu/632348#632348)
Search the bcbtums inf file from the post for e079 until you see [RAMUSBE079.CopyList]
Below that should be a file name followed by .hex find the same file in the folder that had the bcbtums and use Jesse Sung's hex2hcd program to convert it to BCM.hcd
Then ```
sudo cp BCM.hcd /lib/firmware/brcm/BCM.hcd
sudo modprobe -r btusb
sudo modprobe btusb
```

Bluetooth should work


found section and file 
```

;;;;;;;;;;;;;RAMUSBE079;;;;;;;;;;;;;;;;; 
 
[RAMUSBE079.CopyList] 
bcbtums.sys 
btwampfl.sys 
BCM4335C0_003.001.009.0066.0115.hex 


```

not work 

# hciconfig
```

hci0:    Type: BR/EDR  Bus: USB
    BD Address: 40:B8:9A:F8:53:8E  ACL MTU: 1021:8  SCO MTU: 64:1
    DOWN 
    RX bytes:4628 acl:0 sco:0 events:628 errors:0
    TX bytes:77388 acl:0 sco:0 commands:626 errors:0

```

# hciconfig hci0 up
```

Can't init device hci0: Invalid request code (56)

```

#hcidump
```

# hcidump
HCI sniffer - Bluetooth packet analyzer ver 5.35
device: hci0 snap_len: 1500 filter: 0xffffffffffffffff
< HCI Command: Reset (0x03|0x0003) plen 0
> HCI Event: Command Complete (0x0e) plen 4
    Reset (0x03|0x0003) ncmd 1
    status 0x00
< HCI Command: Read Local Version Information (0x04|0x0001) plen 0
> HCI Event: Command Complete (0x0e) plen 12
    Read Local Version Information (0x04|0x0001) ncmd 1
    status 0x00
    HCI Version: 4.1 (0x7) HCI Revision: 0x73
    LMP Version: 4.1 (0x7) LMP Subversion: 0x6109
    Manufacturer: Broadcom Corporation (15)
< HCI Command: Vendor (0x3f|0x0079) plen 0
> HCI Event: Command Complete (0x0e) plen 10
    Vendor (0x3f|0x0079) ncmd 1
< HCI Command: Vendor (0x3f|0x002e) plen 0
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x002e) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 139
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 36
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 92
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 8
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 5
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 5
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 5
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 5
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 5
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 6
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 6
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 5
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 5
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 5
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 8
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 5
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 5
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 5
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 8
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 8
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 8
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 158
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 202
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 80
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 130
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 188
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 80
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 144
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 254
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 46
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 170
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 102
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 55
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 18
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 59
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 102
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 140
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 64
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 168
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 18
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 26
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 88
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 42
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 46
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 132
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 190
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 244
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 18
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 148
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 106
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 49
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 214
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 248
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 148
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 68
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 248
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 54
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 30
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 126
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 74
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 130
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 48
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 42
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 32
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 24
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 28
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 218
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 66
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 248
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 98
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 112
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 6
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 32
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 44
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 72
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 100
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 164
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 48
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 132
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 24
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 24
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 8
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 12
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 32
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 12
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 60
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 114
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 221
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 192
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 23
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 148
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 38
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 255
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 147
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 28
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 12
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 12
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 12
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 36
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 36
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 16
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 44
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 36
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 24
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 20
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 80
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 128
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 28
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 12
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 36
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 16
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 104
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 36
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 22
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 22
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 12
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 12
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 8
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 12
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 20
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 40
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 12
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 28
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 52
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 68
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 12
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 28
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 8
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 20
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 16
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 16
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 14
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 12
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 18
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 18
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 14
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 16
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 32
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 12
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 22
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 34
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 24
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 40
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 40
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 8
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 28
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 48
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 16
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 12
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 12
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 12
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 12
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 26
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 22
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 18
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 14
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 12
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 60
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 24
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 20
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 32
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 40
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 12
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004c) plen 16
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004c) ncmd 1
< HCI Command: Vendor (0x3f|0x004e) plen 4
> HCI Event: Command Complete (0x0e) plen 4
    Vendor (0x3f|0x004e) ncmd 1
> HCI Event: Vendor (0xff) plen 2
< HCI Command: Reset (0x03|0x0003) plen 0
> HCI Event: Command Complete (0x0e) plen 4
    Reset (0x03|0x0003) ncmd 1
    status 0x00
< HCI Command: Read Local Version Information (0x04|0x0001) plen 0
> HCI Event: Command Complete (0x0e) plen 12
    Read Local Version Information (0x04|0x0001) ncmd 1
    status 0x00
    HCI Version: 4.1 (0x7) HCI Revision: 0x73
    LMP Version: 4.1 (0x7) LMP Subversion: 0x6109
    Manufacturer: Broadcom Corporation (15)
< HCI Command: Read BD ADDR (0x04|0x0009) plen 0
> HCI Event: Command Complete (0x0e) plen 10
    Read BD ADDR (0x04|0x0009) ncmd 1
    status 0x00 bdaddr 40:B8:9A:F8:53:8E
< HCI Command: Reset (0x03|0x0003) plen 0
> HCI Event: Command Complete (0x0e) plen 4
    Reset (0x03|0x0003) ncmd 1
    status 0x00
< HCI Command: Read Local Supported Features (0x04|0x0003) plen 0
> HCI Event: Command Complete (0x0e) plen 12
    Read Local Supported Features (0x04|0x0003) ncmd 1
    status 0x00
    Features: 0xbf 0xfe 0xcf 0xfe 0xdb 0xff 0x7b 0x8f
< HCI Command: Read Local Version Information (0x04|0x0001) plen 0
> HCI Event: Command Complete (0x0e) plen 12
    Read Local Version Information (0x04|0x0001) ncmd 1
    status 0x00
    HCI Version: 4.1 (0x7) HCI Revision: 0x73
    LMP Version: 4.1 (0x7) LMP Subversion: 0x6109
    Manufacturer: Broadcom Corporation (15)
< HCI Command: Read BD ADDR (0x04|0x0009) plen 0
> HCI Event: Command Complete (0x0e) plen 10
    Read BD ADDR (0x04|0x0009) ncmd 1
    status 0x00 bdaddr 40:B8:9A:F8:53:8E
< HCI Command: Read Buffer Size (0x04|0x0005) plen 0
> HCI Event: Command Complete (0x0e) plen 11
    Read Buffer Size (0x04|0x0005) ncmd 1
    status 0x00
    ACL MTU 1021:8 SCO MTU 64:1
< HCI Command: Read Class of Device (0x03|0x0023) plen 0
> HCI Event: Command Complete (0x0e) plen 7
    Read Class of Device (0x03|0x0023) ncmd 1
    status 0x00 class 0x000000
< HCI Command: Read Local Name (0x03|0x0014) plen 0
> HCI Event: Command Complete (0x0e) plen 252
    Read Local Name (0x03|0x0014) ncmd 1
    status 0x00 name 'BCM4339 40 MHz USB Class 1 fcbga_YP'
< HCI Command: Read Voice Setting (0x03|0x0025) plen 0
> HCI Event: Command Complete (0x0e) plen 6
    Read Voice Setting (0x03|0x0025) ncmd 1
    status 0x00 voice setting 0x0060
< HCI Command: Read Number of Supported IAC (0x03|0x0038) plen 0
> HCI Event: Command Complete (0x0e) plen 5
    Read Number of Supported IAC (0x03|0x0038) ncmd 1
< HCI Command: Read Current IAC LAP (0x03|0x0039) plen 0
> HCI Event: Command Complete (0x0e) plen 8
    Read Current IAC LAP (0x03|0x0039) ncmd 1
    IAC 0x9e8b33 (General Inquiry Access Code)
< HCI Command: Set Event Filter (0x03|0x0005) plen 1
    type 0 condition 0
    Clear all filters
> HCI Event: Command Complete (0x0e) plen 4
    Set Event Filter (0x03|0x0005) ncmd 1
    status 0x00
< HCI Command: Write Connection Accept Timeout (0x03|0x0016) plen 2
    timeout 32000
> HCI Event: Command Complete (0x0e) plen 4
    Write Connection Accept Timeout (0x03|0x0016) ncmd 1
    status 0x00
< HCI Command: LE Read Buffer Size (0x08|0x0002) plen 0
> HCI Event: Command Complete (0x0e) plen 7
    LE Read Buffer Size (0x08|0x0002) ncmd 1
    status 0x00 pktlen 0x001b maxpkt 0x0f
< HCI Command: LE Read Local Supported Features (0x08|0x0003) plen 0
> HCI Event: Command Complete (0x0e) plen 12
    LE Read Local Supported Features (0x08|0x0003) ncmd 1
    status 0x00 features 0x0f00000000000000 (Link Layer supports LE Encryption)
< HCI Command: LE Read Supported States (0x08|0x001c) plen 0
> HCI Event: Command Complete (0x0e) plen 12
    LE Read Supported States (0x08|0x001c) ncmd 1
< HCI Command: LE Read White List Size (0x08|0x000f) plen 0
> HCI Event: Command Complete (0x0e) plen 5
    LE Read White List Size (0x08|0x000f) ncmd 1
< HCI Command: LE Clear White List (0x08|0x0010) plen 0
> HCI Event: Command Complete (0x0e) plen 4
    LE Clear White List (0x08|0x0010) ncmd 1
    status 0x00
< HCI Command: Read Local Supported Commands (0x04|0x0002) plen 0
> HCI Event: Command Complete (0x0e) plen 68
    Read Local Supported Commands (0x04|0x0002) ncmd 1
    status 0x00
    Commands: ffffff03ccffefffffffec1ff20fe8fe3ff78fff1c00040061f7ffff7ff81f00
              fe3f
< HCI Command: Write Extended Inquiry Response (0x03|0x0052) plen 241
    fec 0x00
> HCI Event: Command Complete (0x0e) plen 4
    Write Extended Inquiry Response (0x03|0x0052) ncmd 1
    status 0x00
< HCI Command: Write Inquiry Mode (0x03|0x0045) plen 1
    mode 2
> HCI Event: Command Complete (0x0e) plen 4
    Write Inquiry Mode (0x03|0x0045) ncmd 1
    status 0x00
< HCI Command: Read Inquiry Response Transmit Power Level (0x03|0x0058) plen 0
> HCI Event: Command Complete (0x0e) plen 5
    Read Inquiry Response Transmit Power Level (0x03|0x0058) ncmd 1
    status 0x00 level 0
< HCI Command: Read Local Extended Features (0x04|0x0004) plen 1
    page 1
> HCI Event: Command Complete (0x0e) plen 14
    Read Local Extended Features (0x04|0x0004) ncmd 1
    status 0x00 page 1 max 2
    Features: 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00
< HCI Command: Set Event Mask (0x03|0x0001) plen 8
    Mask: 0xfffffbff07f8bf3d
> HCI Event: Command Complete (0x0e) plen 4
    Set Event Mask (0x03|0x0001) ncmd 1
    status 0x00
< HCI Command: Read Stored Link Key (0x03|0x000d) plen 7
    bdaddr 00:00:00:00:00:00 all 1
> HCI Event: Command Complete (0x0e) plen 8
    Read Stored Link Key (0x03|0x000d) ncmd 1
    status 0x00 max 1 num 0
< HCI Command: Write Default Link Policy Settings (0x02|0x000f) plen 2
    policy 0x05
    Link policy: RSWITCH SNIFF 
> HCI Event: Command Complete (0x0e) plen 4
    Write Default Link Policy Settings (0x02|0x000f) ncmd 1
    status 0x00
< HCI Command: Read Page Scan Activity (0x03|0x001b) plen 0
> HCI Event: Command Complete (0x0e) plen 8
    Read Page Scan Activity (0x03|0x001b) ncmd 1
    status 0x00 interval 2048 window 18
< HCI Command: Read Page Scan Type (0x03|0x0046) plen 0
> HCI Event: Command Complete (0x0e) plen 5
    Read Page Scan Type (0x03|0x0046) ncmd 1
< HCI Command: LE Set Event Mask (0x08|0x0001) plen 8
    mask 0x3f00000000000000 (Reserved)
> HCI Event: Command Complete (0x0e) plen 4
    LE Set Event Mask (0x08|0x0001) ncmd 1
    status 0x00
< HCI Command: LE Read Advertising Channel Tx Power (0x08|0x0007) plen 0
> HCI Event: Command Complete (0x0e) plen 5
    LE Read Advertising Channel Tx Power (0x08|0x0007) ncmd 1
    status 0x00 level 0xc (dBm)
< HCI Command: Read Local Extended Features (0x04|0x0004) plen 1
    page 2
> HCI Event: Command Complete (0x0e) plen 14
    Read Local Extended Features (0x04|0x0004) ncmd 1
    status 0x00 page 2 max 2
    Features: 0x30 0x08 0x00 0x00 0x00 0x00 0x00 0x00
< HCI Command: Delete Stored Link Key (0x03|0x0012) plen 7
    bdaddr 00:00:00:00:00:00 all 1
> HCI Event: Command Complete (0x0e) plen 6
    Delete Stored Link Key (0x03|0x0012) ncmd 1
    status 0x00 deleted 0
< HCI Command: Set Event Mask Page 2 (0x03|0x0063) plen 8
    Mask: 0x0000000000000000
> HCI Event: Command Complete (0x0e) plen 4
    Set Event Mask Page 2 (0x03|0x0063) ncmd 1
    status 0x01
    Error: Unknown HCI Command

```

bluetoothctl
```

# show
No default controller available
# scan on
No default controller available

```

---

### Post by jeremy31 on 2015-12-28
You need to copy BCM4335C0_003.001.009.0066.0115.hex into hex2hcd folder that you create with
```
git clone git://github.com/jessesung/hex2hcd.git
cd hex2hcd
make
```
Use hex2hcd to convert
```
cd ~/hex2hcd
./hex2hcd BCM*.hex BCM.hcd
sudo cp BCM.hcd /lib/firmware/brcm/BCM.hcd
```

Then with the firmware converted, bluetooth should work after
```
sudo modprobe -r btusb
sudo modprobe btusb
```

---

### Post by virgosun on 2015-12-28
> **jeremy31 said:**
> You need to copy BCM4335C0_003.001.009.0066.0115.hex into hex2hcd folder that you create with
```
git clone git://github.com/jessesung/hex2hcd.git
cd hex2hcd
make
```
Use hex2hcd to convert
```
cd ~/hex2hcd
./hex2hcd BCM*.hex BCM.hcd
sudo cp BCM.hcd /lib/firmware/brcm/BCM.hcd
```

Then with the firmware converted, bluetooth should work after
```
sudo modprobe -r btusb
sudo modprobe btusb
```

Hi Jeremy, I do exactly the same as above.

Before
```

#dmesg
[   13.679157] Bluetooth: hci0: BCM: chip id 86
[   13.679162] Bluetooth: hci0: BCM (003.001.009) build 0115
[   13.679174] bluetooth hci0: Direct firmware load for brcm/BCM.hcd failed with error -2
[   13.679176] Bluetooth: hci0: BCM: Patch brcm/BCM.hcd not found


```

After
```

#dmesg  | grep Bluetooth
[   11.114601] Bluetooth: Core ver 2.20
[   11.114623] Bluetooth: HCI device and connection manager initialized
[   11.114629] Bluetooth: HCI socket layer initialized
[   11.114634] Bluetooth: L2CAP socket layer initialized
[   11.114644] Bluetooth: SCO socket layer initialized
[   11.363157] Bluetooth: hci0: BCM: chip id 86
[   11.363161] Bluetooth: hci0: BCM (003.001.009) build 0000
[   13.064259] Bluetooth: hci0 sending frame failed (-19)
[   15.066215] Bluetooth: hci0 command 0x0c03 tx timeout
[   23.078243] Bluetooth: hci0: BCM: Reset failed (-110)
[   24.867447] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   24.867450] Bluetooth: BNEP filters: protocol multicast
[   24.867456] Bluetooth: BNEP socket layer initialized



```

Is there some thing missing, some more module is needed?

---

### Post by jeremy31 on 2015-12-28
Shut down the computer and see if it works after a cold boot

---

### Post by virgosun on 2016-04-04
> **jeremy31 said:**
> Shut down the computer and see if it works after a cold boot
Hackintosh guys found that this card request a slightly different to upload firmware.
Or boot to Windows then boot back and firmware upload is not needed.
Ubuntu lack such ability to detect good firmware
See this. [http://www.tonymacx86.com/network/150661-brcmpatchram-upload-firmware-into-broadcom-bluetooth-usb-devices-58.html#post1231644](http://www.tonymacx86.com/network/150661-brcmpatchram-upload-firmware-into-broadcom-bluetooth-usb-devices-58.html#post1231644)
I confirm the card work under Hackintosh without upload firmware

---

