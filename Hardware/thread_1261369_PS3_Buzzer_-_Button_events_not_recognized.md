---
title: "PS3 Buzzer - Button events not recognized"
date: 2009-09-08
forum: Hardware
---

### Post by jschneider on 2009-09-08
Hi,

I try to get the PS3 Wireless Buzzers up running.
Plugging in:
dmesg
```
usb 2-1.4: new low speed USB device using ehci_hcd and address 5
usb 2-1.4: configuration #1 chosen from 1 choice
input: Namtai Wbuzz as /devices/pci0000:00/0000:00:1d.7/usb2/2-1/2-1.4/2-1.4:1.0/input/input8
generic-usb 0003:054C:1000.0005: input,hidraw3: USB HID v1.00 Joystick [Namtai Wbuzz] on usb-0000:00:1d.7-1.4/input0
```


lsusb -v:
```
Bus 002 Device 005: ID 054c:1000 Sony Corp. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x054c Sony Corp.
  idProduct          0x1000 
  bcdDevice            0.01
  iManufacturer           1 Namtai
  iProduct                2 Wbuzz
  iSerial                 0 
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
    MaxPower              300mA
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
          bcdHID               1.00
          bCountryCode           33 US
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      78
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
Device Status:     0x0002
  (Bus Powered)
  Remote Wakeup Enabled


```

Now when I start jstest I get:
```
jstest --normal  /dev/input/js0 
Driver version is 2.1.0.
Joystick (Namtai Wbuzz) has 2 axes and 20 buttons.
Testing ... (interrupt to exit)
Axes:  0:-32767  1:-32767 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:off 10:off 11:off 12:off 13:off 14:off 15:off 16:off 17:off 18:off 19:off 

```

But pressing the buttons does *not* result in any events.

Does anyone have an idea what I could do?

---

### Post by biggriffon on 2011-03-11
Hello,

When I connect my PS3 Buzzer,
I face exactly the same problem.

Is someone has found a solution?


I already tried to sync the remotes with the dongle.

---

