---
title: "External HD won't mount"
date: 2009-06-14
forum: Hardware
---

### Post by Locutuslaser on 2009-06-14
I know it is discussed a lot more, but with all try outs i can not get any further.

Had first 64bit 8.10 and formatted an external 500G usb HD to EXT3 for data backup. But did'nt have rights to write on it, yes for a short moment:(

After system upgrade to 9.04 i even cannot read the external HD anymore.

How can i mount the external drive?

---

### Post by nick125 on 2009-06-14
When you plug the hard drive in, do you get any messages in dmesg? If so, can you please paste them?

---

### Post by Locutuslaser on 2009-06-14
Thanks for reply Nick

Is there a way to post a huge dmesg list?

---

### Post by nick125 on 2009-06-14
You only need the last 20-30 lines.

---

### Post by Locutuslaser on 2009-06-14
OK:




[ 3892.090592] scsi10 : SCSI emulation for USB Mass Storage devices
[ 3892.090714] usb-storage: device found at 8
[ 3892.090715] usb-storage: waiting for device to settle before scanning
[ 3897.088192] usb-storage: device scan complete
[ 3897.088687] scsi 10:0:0:0: Direct-Access     WD       5000AAV External 1.05 PQ: 0 ANSI: 4
[ 3897.089919] sd 10:0:0:0: [sdb] 976773168 512-byte hardware sectors: (500 GB/465 GiB)
[ 3897.095954] sd 10:0:0:0: [sdb] Write Protect is off
[ 3897.095957] sd 10:0:0:0: [sdb] Mode Sense: 21 00 00 00
[ 3897.095959] sd 10:0:0:0: [sdb] Assuming drive cache: write through
[ 3897.096668] sd 10:0:0:0: [sdb] 976773168 512-byte hardware sectors: (500 GB/465 GiB)
[ 3898.207040] sd 10:0:0:0: [sdb] Write Protect is off
[ 3898.207043] sd 10:0:0:0: [sdb] Mode Sense: 21 00 00 00
[ 3898.207046] sd 10:0:0:0: [sdb] Assuming drive cache: write through
[ 3898.207050]  sdb: sdb1
[ 3898.221155] sd 10:0:0:0: [sdb] Attached SCSI disk
[ 3898.221221] sd 10:0:0:0: Attached scsi generic sg2 type 0
[ 3898.361015] usb 1-4: reset high speed USB device using ehci_hcd and address 8
[ 3898.656016] usb 1-4: reset high speed USB device using ehci_hcd and address 8
[ 3899.036011] usb 1-4: reset high speed USB device using ehci_hcd and address 8
[ 3899.304012] usb 1-4: reset high speed USB device using ehci_hcd and address 8
jwo@jwo-desktop:~$

---

### Post by mhgsys on 2009-06-14
you could also open a terminal and type:

```

tail -f /var/log/dmesg

```

and plug in the drive, 
this will get you the info asked for and allow you monitoring changes.

also: when posting a huge tex file you can use the 
" [code] " text..blabla. " [/ code] " commands without the " and space between it.

---

### Post by Locutuslaser on 2009-06-14
Then i get this:

jwo@jwo-desktop:~$ tail -f /var/log/dmesg
[   11.774456] type=1505 audit(1245012526.476:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2307
[   11.774481] type=1505 audit(1245012526.476:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2307
[   11.774505] type=1505 audit(1245012526.476:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2307
[   11.840446] type=1505 audit(1245012526.540:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2312
[   11.840573] type=1505 audit(1245012526.544:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2312
[   11.855747] type=1505 audit(1245012526.556:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2316
[   15.233586] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   15.233588] Bluetooth: BNEP filters: protocol multicast
[   15.239047] Bridge firewalling registered
[   16.796035] ppdev: user-space parallel port driver

---

### Post by mhgsys on 2009-06-14
lol, 
then that's the latest lines in /var/log/dmesg

(I'm offtopic since I can't help you with the actual problem)

anyway;
remove the space between / and code in the end of [code] text [/ code]

---

### Post by nick125 on 2009-06-14
> **Locutuslaser said:**
> OK:




[ 3892.090592] scsi10 : SCSI emulation for USB Mass Storage devices
[ 3892.090714] usb-storage: device found at 8
[ 3892.090715] usb-storage: waiting for device to settle before scanning
[ 3897.088192] usb-storage: device scan complete
[ 3897.088687] scsi 10:0:0:0: Direct-Access     WD       5000AAV External 1.05 PQ: 0 ANSI: 4
[ 3897.089919] sd 10:0:0:0: [sdb] 976773168 512-byte hardware sectors: (500 GB/465 GiB)
[ 3897.095954] sd 10:0:0:0: [sdb] Write Protect is off
[ 3897.095957] sd 10:0:0:0: [sdb] Mode Sense: 21 00 00 00
[ 3897.095959] sd 10:0:0:0: [sdb] Assuming drive cache: write through
[ 3897.096668] sd 10:0:0:0: [sdb] 976773168 512-byte hardware sectors: (500 GB/465 GiB)
[ 3898.207040] sd 10:0:0:0: [sdb] Write Protect is off
[ 3898.207043] sd 10:0:0:0: [sdb] Mode Sense: 21 00 00 00
[ 3898.207046] sd 10:0:0:0: [sdb] Assuming drive cache: write through
[ 3898.207050]  sdb: sdb1
[ 3898.221155] sd 10:0:0:0: [sdb] Attached SCSI disk
[ 3898.221221] sd 10:0:0:0: Attached scsi generic sg2 type 0
[ 3898.361015] usb 1-4: reset high speed USB device using ehci_hcd and address 8
[ 3898.656016] usb 1-4: reset high speed USB device using ehci_hcd and address 8
[ 3899.036011] usb 1-4: reset high speed USB device using ehci_hcd and address 8
[ 3899.304012] usb 1-4: reset high speed USB device using ehci_hcd and address 8
jwo@jwo-desktop:~$

I'm kind of curious as to why it keeps resetting the USB device. Can you post lsusb (and attach lsusb -v)?

---

### Post by Locutuslaser on 2009-06-15
```
jwo@jwo-desktop:~$ lsusb
Bus 002 Device 002: ID 163f:1611  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 1058:1001 Western Digital Technologies, Inc. External Hard Disk
Bus 001 Device 002: ID 0ac8:0323 Z-Star Microelectronics Corp. Luxya WC-1200 USB 2.0 Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 003: ID 046d:c408 Logitech, Inc. Marble Mouse (4-button)
Bus 005 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
jwo@jwo-desktop:~$
```

and: 

```
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       3
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval               7
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0400  1x 1024 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       4
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval               7
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0b00  2x 768 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       5
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval               7
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0c00  2x 1024 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       6
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval               7
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x1380  3x 896 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       7
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval               7
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x1400  3x 1024 bytes
        bInterval               1
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0002 2.0 root hub
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
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
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              12
can't get hub descriptor: Operation not permitted
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

Bus 005 Device 003: ID 046d:c408 Logitech, Inc. Marble Mouse (4-button)
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x046d Logitech, Inc.
  idProduct          0xc408 Marble Mouse (4-button)
  bcdDevice           14.00
  iManufacturer           1 
  iProduct                2 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           34
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower               50mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      2 Mouse
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.10
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      66
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              10
cannot read device status, Operation not permitted (1)

Bus 005 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x046d Logitech, Inc.
  idProduct          0xc517 LX710 Cordless Desktop Laser
  bcdDevice           38.10
  iManufacturer           1 
  iProduct                2 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           59
    bNumInterfaces          2
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower               98mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      1 Keyboard
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.10
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      59
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              10
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      2 Mouse
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.10
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength     177
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              10
cannot read device status, Operation not permitted (1)

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0001 1.1 root hub
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
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
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
can't get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0001 1.1 root hub
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
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
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
can't get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0001 1.1 root hub
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
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
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
can't get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)
jwo@jwo-desktop:~$
```

---

### Post by Locutuslaser on 2009-06-16
[I]can't get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)[/I]


 Not the best remarks. 

Would it be helpful to format the disk to NTFS or reiser?

---

### Post by mhgsys on 2009-06-16
> **Locutuslaser said:**
> [I]can't get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)[/I]


 

Actually thats quite normal; 

type :

```

sudo lsusb -v

```

instaid.

Anyway; Have a look here... This should get your usb drive mounted.
[http://www.linuxconfig.org/Howto_mount_USB_drive_in_Linux](http://www.linuxconfig.org/Howto_mount_USB_drive_in_Linux)

*and please don't overread: Device names can vary !*

---

### Post by Locutuslaser on 2009-06-16
That link gives: *The account is currently not active.*

I have tried several mounting options. It worked a short while and stopped unfortunately.

Every time i boot 9.04 ubuntu says cannot mount the ext.HD

---

### Post by Locutuslaser on 2009-06-17
url works now again. Will try the suggested tips tomorrow:D

---

### Post by Locutuslaser on 2009-07-08
I have to sell this hd to a windozer because it is not functioning proper on my system. Also after suggested mount options

---

