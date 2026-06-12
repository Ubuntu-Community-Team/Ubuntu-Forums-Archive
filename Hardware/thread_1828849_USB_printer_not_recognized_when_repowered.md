---
title: "USB printer not recognized when repowered"
date: 2011-08-19
forum: Hardware
---

### Post by Lysander10 on 2011-08-19
Dear all,

I am having strange issues with a SATO CG412 USB printer not being recognized by my operating system when it is unplugged and plugged back in (or repowered).

My operating system is Ubuntu Server 10.04.3, kernel version 2.6.33-33-generic, and the hardware I'm running it on is an Ebox 3300MX. The printer in question is usually recognized fine when the operating system is booted. However, when power is cycled to the printer, the operating system no longer recognizes it (after sufficient time has been given for the printer to power back up). This is always accompanied with the error message "[FONT="Courier New"]usb 4-1: string descriptor 0 read error: -110[/FONT]" being printed to stderr.

Please note that this is **not** a problem with print drivers. Ubuntu 10.04 does not include drivers for the SATO CG412, but that isn't the issue I'm having. Below I've posted the output of [FONT="Courier New"]lsusb -v[/FONT] before the error occurs, after the error occurs, and [FONT="Courier New"]dmesg | grep usb[/FONT] after the error occurs. Notice that the printer is listed as a SATO CG412 before the error occurs, and after it occurs a SATO device is still listed, but much of the information (including the USB endpoints) is missing.

[FONT="Courier New"]lsusb -v[/FONT] before the error occurs:
```
Bus 004 Device 002: ID 0828:0102 Sato Corp. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            7 Printer
  bDeviceSubClass         1 Printer
  bDeviceProtocol       255 Vendor Specific
  bMaxPacketSize0         8
  idVendor           0x0828 Sato Corp.
  idProduct          0x0102 
  bcdDevice            1.01
  iManufacturer           1 SATO International Pte.Ltd.
  iProduct                2 SATO CG412  
  iSerial                 3 FAKK0120
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           39
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          4 
    bmAttributes         0xc0
      Self Powered
    MaxPower               10mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass         7 Printer
      bInterfaceSubClass      1 Printer
      bInterfaceProtocol      2 Bidirectional
      iInterface              0 
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
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval               1
Device Status:     0x0001
  Self Powered
```

[FONT="Courier New"]lsusb -v[/FONT] after the error occurs:
```
Bus 004 Device 003: ID 0828:0102 Sato Corp. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            7 Printer
  bDeviceSubClass         1 Printer
  bDeviceProtocol       255 Vendor Specific
  bMaxPacketSize0         8
  idVendor           0x0828 Sato Corp.
  idProduct          0x0102 
  bcdDevice            1.01
  iManufacturer           1 
  iProduct                2 
  iSerial                 3 
  bNumConfigurations      0
Device Status:     0x0001
  Self Powered
``` 

[FONT="Courier New"]dmesg | grep usb[/FONT] after the error:
```
[    0.072200] usbcore: registered new interface driver usbfs
[    0.072297] usbcore: registered new interface driver hub
[    0.072535] usbcore: registered new device driver usb
[    0.708462] usb usb1: configuration #1 chosen from 1 choice
[    0.743755] usb usb2: configuration #1 chosen from 1 choice
[    0.856239] usb usb3: configuration #1 chosen from 1 choice
[    0.970769] usb usb4: configuration #1 chosen from 1 choice
[    1.474312] usb 3-2: new full speed USB device using ohci_hcd and address 2
[    1.680973] usb 3-2: configuration #1 chosen from 1 choice
[    1.980265] usb 3-2.1: new low speed USB device using ohci_hcd and address 3
[    2.099613] usb 3-2.1: configuration #1 chosen from 1 choice
[    2.182648] usb 3-2.4: new full speed USB device using ohci_hcd and address 4
[    2.301289] usb 3-2.4: configuration #1 chosen from 1 choice
[    3.123406] usbcore: registered new interface driver hiddev
[    3.135238] input: G15 Gaming Keyboard as /devices/pci0000:00/0000:00:0a.0/usb3/3-2/3-2.1/3-2.1:1.0/input/input1
[    3.136302] generic-usb 0003:046D:C226.0001: input,hidraw0: USB HID v1.10 Keyboard [G15 Gaming Keyboard] on usb-0000:00:0a.0-2.1/input0
[    3.152366] input: G15 Gaming Keyboard as /devices/pci0000:00/0000:00:0a.0/usb3/3-2/3-2.1/3-2.1:1.1/input/input2
[    3.154744] generic-usb 0003:046D:C226.0002: input,hiddev96,hidraw1: USB HID v1.10 Device [G15 Gaming Keyboard] on usb-0000:00:0a.0-2.1/input1
[    3.168902] input: G15 GamePanel LCD as /devices/pci0000:00/0000:00:0a.0/usb3/3-2/3-2.4/3-2.4:1.0/input/input3
[    3.170442] generic-usb 0003:046D:C227.0003: input,hiddev97,hidraw2: USB HID v1.11 Keypad [G15 GamePanel LCD] on usb-0000:00:0a.0-2.4/input0
[    3.170622] usbcore: registered new interface driver usbhid
[    3.171304] usbhid: v2.6:USB HID core driver
[  200.867905] usb 4-1: new full speed USB device using ohci_hcd and address 2
[  201.076912] usb 4-1: unable to read config index 0 descriptor/start: -75
[  201.087924] usb 4-1: chopping to 0 config(s)
[  208.639551] usb 4-1: string descriptor 0 read error: -62
[  208.653852] usb 4-1: no configuration chosen from 0 choices
[  208.654022] usb 4-1: USB disconnect, address 2
[  212.536013] usb 3-1: new full speed USB device using ohci_hcd and address 5
[  212.763255] usb 3-1: configuration #1 chosen from 1 choice
[  212.832388] usblp0: USB Bidirectional printer dev 5 if 0 alt 0 proto 2 vid 0x0828 pid 0x0102
[  212.832551] usbcore: registered new interface driver usblp
[  219.715501] usb 3-1: USB disconnect, address 5
[  219.717693] usblp0: removed
[  225.248132] usb 3-1: new full speed USB device using ohci_hcd and address 6
[  225.463220] usb 3-1: unable to read config index 0 descriptor/start: -75
[  225.474544] usb 3-1: chopping to 0 config(s)
[  235.484797] usb 3-1: string descriptor 0 read error: -110
[  235.498586] usb 3-1: no configuration chosen from 0 choices
[  243.224482] usb 3-1: usbfs: USBDEVFS_CONTROL failed cmd lsusb rqt 128 rq 6 len 255 ret -110
[  244.224434] usb 3-1: usbfs: USBDEVFS_CONTROL failed cmd lsusb rqt 128 rq 6 len 255 ret -110
[  245.224389] usb 3-1: usbfs: USBDEVFS_CONTROL failed cmd lsusb rqt 128 rq 6 len 255 ret -110
```

I should also mention that I've used this exact printer on another hardware platform (a PC Engine ALIX), using the same operating system, and the error doesn't happen with that setup. 

Any help resolving this issue would be greatly appreciated.

---

### Post by Lysander10 on 2011-08-21
I'm not making much progress on this issue; I could really use some help.

---

