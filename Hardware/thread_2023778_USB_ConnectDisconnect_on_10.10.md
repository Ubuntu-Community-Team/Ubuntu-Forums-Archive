---
title: "USB Connect/Disconnect on 10.10"
date: 2012-07-12
forum: Hardware
---

### Post by khaninger on 2012-07-12
Hello, relative newbie to ubuntu: Having issues with a USB connection connecting and disconnecting successively.  

uname -a:
```
Linux moonraker 2.6.35.10atom #2 SMP Sun Feb 20 18:52:30 JST 2011 i686 GNU/Linux
```

dmesg:
```
usb 3-2: new full speed USB device using uhci_hcd and address 85
[  184.853874] generic-usb 0003:06C2:0033.0051: hiddev96,hidraw2: USB HID v1.10 Device [Phidgets Inc. PhidgetSpatial] on usb-0000:00:1d.1-2/input0
[  202.028168] usb 3-2: USB disconnect, address 85
[  202.268098] usb 3-2: new full speed USB device using uhci_hcd and address 86
[  202.466280] generic-usb 0003:06C2:0033.0052: hiddev96,hidraw2: USB HID v1.10 Device [Phidgets Inc. PhidgetSpatial] on usb-0000:00:1d.1-2/input0
[  319.104171] usb 3-2: USB disconnect, address 86
[  319.344124] usb 3-2: new full speed USB device using uhci_hcd and address 87
[  319.539991] generic-usb 0003:06C2:0033.0053: hiddev96,hidraw2: USB HID v1.10 Device [Phidgets Inc. PhidgetSpatial] on usb-0000:00:1d.1-2/input0
[  322.536202] usb 3-2: USB disconnect, address 87
[  323.304096] usb 3-2: new full speed USB device using uhci_hcd and address 88
[  323.497337] generic-usb 0003:06C2:0033.0054: hiddev96,hidraw2: USB HID v1.10 Device [Phidgets Inc. PhidgetSpatial] on usb-0000:00:1d.1-2/input0
[  325.560167] usb 3-2: USB disconnect, address 88
[  325.800081] usb 3-2: new full speed USB device using uhci_hcd and address 89
[  325.992384] generic-usb 0003:06C2:0033.0055: hiddev96,hidraw2: USB HID v1.10 Device [Phidgets Inc. PhidgetSpatial] on usb-0000:00:1d.1-2/input0
[  447.384173] usb 3-2: USB disconnect, address 89
[  447.624096] usb 3-2: new full speed USB device using uhci_hcd and address 90
[  447.824573] generic-usb 0003:06C2:0033.0056: hiddev96,hidraw2: USB HID v1.10 Device [Phidgets Inc. PhidgetSpatial] on usb-0000:00:1d.1-2/input0
[  448.072198] usb 3-2: USB disconnect, address 90
[  448.792108] usb 3-2: new full speed USB device using uhci_hcd and address 91
[  448.989866] generic-usb 0003:06C2:0033.0057: hiddev96,hidraw2: USB HID v1.10 Device [Phidgets Inc. PhidgetSpatial] on usb-0000:00:1d.1-2/input0
[  460.096192] usb 3-2: USB disconnect, address 91
[  460.737089] usb 3-2: new full speed USB device using uhci_hcd and address 92
[  460.938982] generic-usb 0003:06C2:0033.0058: hiddev96,hidraw2: USB HID v1.10 Device [Phidgets Inc. PhidgetSpatial] on usb-0000:00:1d.1-2/input0
[  499.744163] usb 3-2: USB disconnect, address 92
[  500.388098] usb 3-2: new full speed USB device using uhci_hcd and address 93
[  500.584155] generic-usb 0003:06C2:0033.0059: hiddev96,hidraw2: USB HID v1.10 Device [Phidgets Inc. PhidgetSpatial] on usb-0000:00:1d.1-2/input0
```

lsusb -v:
```
Bus 003 Device 096: ID 06c2:0033 Phidgets Inc. (formerly GLAB)
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0
  bDeviceProtocol         0
  bMaxPacketSize0         8
  idVendor           0x06c2 Phidgets Inc. (formerly GLAB)
  idProduct          0x0033
  bcdDevice            1.00
  iManufacturer           1
  iProduct                2
  iSerial                 3
:can't get hub descriptor: Operation not permitted
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           34
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
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      0 No Subclass
      bInterfaceProtocol      0 None
      iInterface              0
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.10
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      32
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
        wMaxPacketSize     0x003d  1x 61 bytes
        bInterval               8
```


Anyone have suggestions or ideas what can be causing this?  [COLOR="Silver"]When the device is plugged into another system(where the Phidget libraries are not installed), there is no error like this...[/COLOR]EDIT: This is happening on the system running 12.04 as well.

```

[34657.048473] usb 2-1.1: USB disconnect, device number 4
[36397.925216] usb 2-1.1: new full-speed USB device number 5 using ehci_hcd
[36398.021147] generic-usb 0003:06C2:0033.0002: hiddev0,hidraw0: USB HID v1.10 Device [Phidgets Inc. PhidgetSpatial] on usb-0000:00:1d.0-1.1/input0
[37291.435515] usb 2-1.1: USB disconnect, device number 5
[44888.804953] usb 2-1.1: new full-speed USB device number 6 using ehci_hcd
[44888.901433] generic-usb 0003:06C2:0033.0003: hiddev0,hidraw0: USB HID v1.10 Device [Phidgets Inc. PhidgetSpatial] on usb-0000:00:1d.0-1.1/input0


```

---

