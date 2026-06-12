---
title: "External HD randomly shuts off"
date: 2008-06-27
forum: Hardware
---

### Post by dbsoundman on 2008-06-27
I don't know if this is a hardware or software problem, but I have an external 80GB Western Digial IDE drive in an ADS tech case which is acting really strangely. It seems that when I connect it after the computer is on, it tends not to stay running; I can hear the drive spin up to speed, then it clicks and coasts off, then tries again repeatedly. But, if I plug it in before I start the computer, it usually works fine. I'm not sure what the deal is with this but it's really annoying and didn't happen before, it's just started in the last couple of months. Does anyone have experience with this or ideas as to what might be the problem?

Thanks,
Dan

---

### Post by Odrodzona-Sarmacja on 2008-06-27
Power management. Not all options for power management are in screen savers. Also when you have screensavers removed the problems tend to be even more acute with other parts of hardware blanking out after minute or so inactivity. I know you can change it somehow in /etc/X11/xorg.conf, so power management won't go crazy at your harddrives too. Unfortunatelly I don't know exactly what you need to put there to make it stay away from powering down harddrives. Maybe googling here is in order.

---

### Post by ukripper on 2008-06-27
> **dbsoundman said:**
> I don't know if this is a hardware or software problem, but I have an external 80GB Western Digial IDE drive in an ADS tech case which is acting really strangely. It seems that when I connect it after the computer is on, it tends not to stay running; I can hear the drive spin up to speed, then it clicks and coasts off, then tries again repeatedly. But, if I plug it in before I start the computer, it usually works fine. I'm not sure what the deal is with this but it's really annoying and didn't happen before, it's just started in the last couple of months. Does anyone have experience with this or ideas as to what might be the problem?

Thanks,
Dan

can post output of the following after connecting the drive:
```
cat /var/log/messages | grep usb
```

```
dmesg | grep usb
```

```
lsusb -v
```

```
sudo fdisk -l
```

---

### Post by dbsoundman on 2008-06-27
Here it all is:
```
dan@dan-laptop:~$ cat /var/log/messages | grep usb
Jun 23 17:47:38 dan-laptop kernel: [ 1123.128000] usb 1-5: USB disconnect, address 3
Jun 23 17:48:06 dan-laptop kernel: [ 1151.060000] usb 1-3: new high speed USB device using ehci_hcd and address 4
Jun 23 17:48:06 dan-laptop kernel: [ 1151.192000] usb 1-3: configuration #1 chosen from 1 choice
Jun 23 18:01:02 dan-laptop kernel: [ 1926.980000] usb 1-3: USB disconnect, address 4
Jun 23 18:01:05 dan-laptop kernel: [ 1930.140000] usb 1-3: new high speed USB device using ehci_hcd and address 5
Jun 23 18:01:05 dan-laptop kernel: [ 1930.272000] usb 1-3: configuration #1 chosen from 1 choice
Jun 23 18:05:35 dan-laptop kernel: [ 2199.540000] usb 1-3: USB disconnect, address 5
Jun 23 18:05:38 dan-laptop kernel: [ 2202.636000] usb 1-3: new high speed USB device using ehci_hcd and address 6
Jun 23 18:05:38 dan-laptop kernel: [ 2202.768000] usb 1-3: configuration #1 chosen from 1 choice
Jun 24 12:53:00 dan-laptop kernel: [    5.188000] usbcore: registered new interface driver usbfs
Jun 24 12:53:00 dan-laptop kernel: [    5.188000] usbcore: registered new interface driver hub
Jun 24 12:53:00 dan-laptop kernel: [    5.188000] usbcore: registered new device driver usb
Jun 24 12:53:00 dan-laptop kernel: [    5.192000] usb usb1: configuration #1 chosen from 1 choice
Jun 24 12:53:00 dan-laptop kernel: [    5.296000] usb usb2: configuration #1 chosen from 1 choice
Jun 24 12:53:00 dan-laptop kernel: [    5.400000] usb usb3: configuration #1 chosen from 1 choice
Jun 24 12:53:00 dan-laptop kernel: [    5.504000] usb usb4: configuration #1 chosen from 1 choice
Jun 24 12:53:00 dan-laptop kernel: [    5.612000] usb usb5: configuration #1 chosen from 1 choice
Jun 24 12:53:00 dan-laptop kernel: [   24.516000] usbcore: registered new interface driver ndiswrapper
Jun 24 14:30:50 dan-laptop kernel: [ 5902.064000] usbcore: deregistering interface driver ndiswrapper
Jun 24 14:54:47 dan-laptop kernel: [    5.008000] usbcore: registered new interface driver usbfs
Jun 24 14:54:47 dan-laptop kernel: [    5.008000] usbcore: registered new interface driver hub
Jun 24 14:54:47 dan-laptop kernel: [    5.008000] usbcore: registered new device driver usb
Jun 24 14:54:47 dan-laptop kernel: [    5.008000] usb usb1: configuration #1 chosen from 1 choice
Jun 24 14:54:47 dan-laptop kernel: [    5.112000] usb usb2: configuration #1 chosen from 1 choice
Jun 24 14:54:47 dan-laptop kernel: [    5.216000] usb usb3: configuration #1 chosen from 1 choice
Jun 24 14:54:47 dan-laptop kernel: [    5.320000] usb usb4: configuration #1 chosen from 1 choice
Jun 24 14:54:47 dan-laptop kernel: [    5.428000] usb usb5: configuration #1 chosen from 1 choice
Jun 24 14:54:47 dan-laptop kernel: [   35.420000] usbcore: registered new interface driver ndiswrapper
Jun 26 14:29:01 dan-laptop kernel: [    5.404000] usbcore: registered new interface driver usbfs
Jun 26 14:29:01 dan-laptop kernel: [    5.404000] usbcore: registered new interface driver hub
Jun 26 14:29:01 dan-laptop kernel: [    5.404000] usbcore: registered new device driver usb
Jun 26 14:29:01 dan-laptop kernel: [    5.404000] usb usb1: configuration #1 chosen from 1 choice
Jun 26 14:29:01 dan-laptop kernel: [    5.508000] usb usb2: configuration #1 chosen from 1 choice
Jun 26 14:29:01 dan-laptop kernel: [    5.612000] usb usb3: configuration #1 chosen from 1 choice
Jun 26 14:29:01 dan-laptop kernel: [    5.716000] usb usb4: configuration #1 chosen from 1 choice
Jun 26 14:29:01 dan-laptop kernel: [    5.824000] usb usb5: configuration #1 chosen from 1 choice
Jun 26 14:29:01 dan-laptop kernel: [   24.400000] usbcore: registered new interface driver ndiswrapper
Jun 26 20:34:21 dan-laptop kernel: [    5.380000] usbcore: registered new interface driver usbfs
Jun 26 20:34:21 dan-laptop kernel: [    5.380000] usbcore: registered new interface driver hub
Jun 26 20:34:21 dan-laptop kernel: [    5.380000] usbcore: registered new device driver usb
Jun 26 20:34:21 dan-laptop kernel: [    5.380000] usb usb1: configuration #1 chosen from 1 choice
Jun 26 20:34:21 dan-laptop kernel: [    5.484000] usb usb2: configuration #1 chosen from 1 choice
Jun 26 20:34:21 dan-laptop kernel: [    5.588000] usb usb3: configuration #1 chosen from 1 choice
Jun 26 20:34:21 dan-laptop kernel: [    5.692000] usb usb4: configuration #1 chosen from 1 choice
Jun 26 20:34:21 dan-laptop kernel: [    6.484000] usb usb5: configuration #1 chosen from 1 choice
Jun 26 20:34:21 dan-laptop kernel: [   24.448000] usbcore: registered new interface driver ndiswrapper
Jun 26 23:54:48 dan-laptop kernel: [11899.716000]   <6>usb 5-3: new high speed USB device using ehci_hcd and address 2
Jun 26 23:54:48 dan-laptop kernel: [12063.048000] usb 5-3: configuration #1 chosen from 1 choice
Jun 26 23:54:48 dan-laptop kernel: [12063.712000] usbcore: registered new interface driver libusual
Jun 26 23:54:48 dan-laptop kernel: [12063.724000] usbcore: registered new interface driver usb-storage
Jun 26 23:55:25 dan-laptop kernel: [12100.552000] usb 5-3: reset high speed USB device using ehci_hcd and address 2
Jun 26 23:55:26 dan-laptop kernel: [12100.960000] usb 5-3: USB disconnect, address 2
Jun 26 23:55:26 dan-laptop kernel: [12101.072000] usb 5-3: new high speed USB device using ehci_hcd and address 3
Jun 26 23:55:26 dan-laptop kernel: [12101.216000] usb 5-3: configuration #1 chosen from 1 choice
Jun 26 23:56:02 dan-laptop kernel: [12136.856000] usb 5-3: reset high speed USB device using ehci_hcd and address 3
Jun 27 00:10:43 dan-laptop kernel: [13018.448000] usb 5-3: reset high speed USB device using ehci_hcd and address 3
Jun 27 00:11:18 dan-laptop kernel: [13052.940000] usb 5-3: reset high speed USB device using ehci_hcd and address 3
Jun 27 00:11:48 dan-laptop kernel: [13083.636000] usb 5-3: reset high speed USB device using ehci_hcd and address 3
Jun 27 00:13:59 dan-laptop kernel: [13213.812000] usb 5-3: reset high speed USB device using ehci_hcd and address 3
Jun 27 00:14:09 dan-laptop kernel: [13224.168000] usb 5-3: USB disconnect, address 3
Jun 27 00:17:02 dan-laptop kernel: [    3.336000] usbcore: registered new interface driver usbfs
Jun 27 00:17:02 dan-laptop kernel: [    3.336000] usbcore: registered new interface driver hub
Jun 27 00:17:02 dan-laptop kernel: [    3.336000] usbcore: registered new device driver usb
Jun 27 00:17:02 dan-laptop kernel: [    3.352000] usb usb1: configuration #1 chosen from 1 choice
Jun 27 00:17:02 dan-laptop kernel: [    3.456000] usb usb2: configuration #1 chosen from 1 choice
Jun 27 00:17:02 dan-laptop kernel: [    3.560000] usb usb3: configuration #1 chosen from 1 choice
Jun 27 00:17:02 dan-laptop kernel: [    3.664000] usb usb4: configuration #1 chosen from 1 choice
Jun 27 00:17:02 dan-laptop kernel: [    3.768000] usb usb5: configuration #1 chosen from 1 choice
Jun 27 00:17:02 dan-laptop kernel: [   20.612000] usbcore: registered new interface driver ndiswrapper
Jun 27 00:18:26 dan-laptop kernel: [  112.396000] usb 1-3: new high speed USB device using ehci_hcd and address 2
Jun 27 00:18:27 dan-laptop kernel: [  112.540000] usb 1-3: configuration #1 chosen from 1 choice
Jun 27 00:18:27 dan-laptop kernel: [  112.608000] usbcore: registered new interface driver libusual
Jun 27 00:18:27 dan-laptop kernel: [  112.628000] usbcore: registered new interface driver usb-storage
Jun 27 10:26:38 dan-laptop kernel: [    5.676000] usbcore: registered new interface driver usbfs
Jun 27 10:26:38 dan-laptop kernel: [    5.676000] usbcore: registered new interface driver hub
Jun 27 10:26:38 dan-laptop kernel: [    5.676000] usbcore: registered new device driver usb
Jun 27 10:26:38 dan-laptop kernel: [    5.676000] usb usb1: configuration #1 chosen from 1 choice
Jun 27 10:26:38 dan-laptop kernel: [    5.780000] usb usb2: configuration #1 chosen from 1 choice
Jun 27 10:26:38 dan-laptop kernel: [    5.884000] usb usb3: configuration #1 chosen from 1 choice
Jun 27 10:26:38 dan-laptop kernel: [    5.988000] usb usb4: configuration #1 chosen from 1 choice
Jun 27 10:26:38 dan-laptop kernel: [    6.096000] usb usb5: configuration #1 chosen from 1 choice
Jun 27 10:26:38 dan-laptop kernel: [    6.124000] usb 2-1: new full speed USB device using uhci_hcd and address 2
Jun 27 10:26:38 dan-laptop kernel: [    6.440000] usb 5-3: new high speed USB device using ehci_hcd and address 2
Jun 27 10:26:38 dan-laptop kernel: [    6.584000] usb 5-3: configuration #1 chosen from 1 choice
Jun 27 10:26:38 dan-laptop kernel: [    6.600000] usbcore: registered new interface driver libusual
Jun 27 10:26:38 dan-laptop kernel: [    6.608000] usbcore: registered new interface driver usb-storage
Jun 27 10:26:38 dan-laptop kernel: [   24.804000] usbcore: registered new interface driver ndiswrapper

```
```
dan@dan-laptop:~$ dmesg | grep usb
[    5.676000] usbcore: registered new interface driver usbfs
[    5.676000] usbcore: registered new interface driver hub
[    5.676000] usbcore: registered new device driver usb
[    5.676000] usb usb1: configuration #1 chosen from 1 choice
[    5.780000] usb usb2: configuration #1 chosen from 1 choice
[    5.884000] usb usb3: configuration #1 chosen from 1 choice
[    5.988000] usb usb4: configuration #1 chosen from 1 choice
[    6.096000] usb usb5: configuration #1 chosen from 1 choice
[    6.124000] usb 2-1: new full speed USB device using uhci_hcd and address 2
[    6.440000] usb 5-3: new high speed USB device using ehci_hcd and address 2
[    6.584000] usb 5-3: configuration #1 chosen from 1 choice
[    6.600000] usbcore: registered new interface driver libusual
[    6.608000] usb-storage: device found at 2
[    6.608000] usbcore: registered new interface driver usb-storage
[    6.608000] usb-storage: waiting for device to settle before scanning
[   11.608000] usb-storage: device scan complete
[   24.804000] usbcore: registered new interface driver ndiswrapper

```
```
dan@dan-laptop:~$ lsusb -v

Bus 005 Device 002: ID 06e1:0833 ADS Technologies, Inc. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x06e1 ADS Technologies, Inc.
  idProduct          0x0833 
  bcdDevice            0.33
  iManufacturer           2 
  iProduct                3 
  iSerial                 0 
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
    MaxPower               96mA
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
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               1
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

Bus 005 Device 001: ID 0000:0000  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         1 Single TT
  bMaxPacketSize0        64
  idVendor           0x0000 
  idProduct          0x0000 
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
      bInterfaceProtocol      0 Full speed hub
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

Bus 003 Device 001: ID 0000:0000  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed hub
  bMaxPacketSize0        64
  idVendor           0x0000 
  idProduct          0x0000 
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
      bInterfaceProtocol      0 Full speed hub
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

Bus 002 Device 001: ID 0000:0000  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed hub
  bMaxPacketSize0        64
  idVendor           0x0000 
  idProduct          0x0000 
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
      bInterfaceProtocol      0 Full speed hub
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

Bus 001 Device 001: ID 0000:0000  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed hub
  bMaxPacketSize0        64
  idVendor           0x0000 
  idProduct          0x0000 
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
      bInterfaceProtocol      0 Full speed hub
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

Bus 004 Device 001: ID 0000:0000  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed hub
  bMaxPacketSize0        64
  idVendor           0x0000 
  idProduct          0x0000 
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
      bInterfaceProtocol      0 Full speed hub
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

```
```
dan@dan-laptop:~$ sudo fdisk -l
Password:

Disk /dev/sda: 78.5 GB, 78518522880 bytes
255 heads, 63 sectors/track, 9546 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6        2810    22531162+   7  HPFS/NTFS
/dev/sda3            6380        9546    25438927+   5  Extended
/dev/sda4            2811        6379    28667992+  83  Linux
/dev/sda5            6380        6761     3068383+  82  Linux swap / Solaris
/dev/sda6            6762        9546    22370481   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9730    78150712+   b  W95 FAT32

Disk /dev/sdc: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System

```
I should note that today when I booted up I did not have the random on/off problem because I turned on the drive before I turned on the computer. Also, I have a 200GB firewire external drive connected as well, which so far has not been an issue.

-Dan

---

