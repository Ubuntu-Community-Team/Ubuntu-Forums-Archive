---
title: "CanoScan LiDE 120 not detected on 16.04"
date: 2016-09-30
forum: Hardware
---

### Post by lukon on 2016-09-30
My Cannon CanoScan LiDE 120 is not showing up in my 16.04.

Xsane and SimpleScan only find my other scanner, the scanner part of my Brother MFC 210C.

Because I use several computers at my desk, both these scanners are connected through a KVM switch with USB switching ability.

Is my problem simply that Xsane and Simple Scan cannot handle more than one scanner?

Or is the CanoScan LiDE 120 still not supported, even 'though some web pages say it is now supported?

Here is the return from sudo sane-find-scanner -v -v:

```
This is sane-find-scanner from sane-backends 1.0.25git

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

searching for SCSI scanners:
checking /dev/scanner... failed to open (Invalid argument)
checking /dev/sg0... failed to open (Invalid argument)
checking /dev/sg1... failed to open (Invalid argument)
checking /dev/sg2... failed to open (Invalid argument)
checking /dev/sg3... failed to open (Invalid argument)
checking /dev/sg4... failed to open (Invalid argument)
checking /dev/sg5... failed to open (Invalid argument)
checking /dev/sg6... failed to open (Invalid argument)
checking /dev/sg7... failed to open (Invalid argument)
checking /dev/sg8... failed to open (Invalid argument)
checking /dev/sg9... failed to open (Invalid argument)
checking /dev/sga... failed to open (Invalid argument)
checking /dev/sgb... failed to open (Invalid argument)
checking /dev/sgc... failed to open (Invalid argument)
checking /dev/sgd... failed to open (Invalid argument)
checking /dev/sge... failed to open (Invalid argument)
checking /dev/sgf... failed to open (Invalid argument)
checking /dev/sgg... failed to open (Invalid argument)
checking /dev/sgh... failed to open (Invalid argument)
checking /dev/sgi... failed to open (Invalid argument)
checking /dev/sgj... failed to open (Invalid argument)
checking /dev/sgk... failed to open (Invalid argument)
checking /dev/sgl... failed to open (Invalid argument)
checking /dev/sgm... failed to open (Invalid argument)
checking /dev/sgn... failed to open (Invalid argument)
checking /dev/sgo... failed to open (Invalid argument)
checking /dev/sgp... failed to open (Invalid argument)
checking /dev/sgq... failed to open (Invalid argument)
checking /dev/sgr... failed to open (Invalid argument)
checking /dev/sgs... failed to open (Invalid argument)
checking /dev/sgt... failed to open (Invalid argument)
checking /dev/sgu... failed to open (Invalid argument)
checking /dev/sgv... failed to open (Invalid argument)
checking /dev/sgw... failed to open (Invalid argument)
checking /dev/sgx... failed to open (Invalid argument)
checking /dev/sgy... failed to open (Invalid argument)
checking /dev/sgz... failed to open (Invalid argument)
  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

searching for USB scanners:
checking /dev/usb/scanner... failed to open (Invalid argument)
checking /dev/usb/scanner0... failed to open (Invalid argument)
checking /dev/usb/scanner1... failed to open (Invalid argument)
checking /dev/usb/scanner2... failed to open (Invalid argument)
checking /dev/usb/scanner3... failed to open (Invalid argument)
checking /dev/usb/scanner4... failed to open (Invalid argument)
checking /dev/usb/scanner5... failed to open (Invalid argument)
checking /dev/usb/scanner5... failed to open (Invalid argument)
checking /dev/usb/scanner7... failed to open (Invalid argument)
checking /dev/usb/scanner8... failed to open (Invalid argument)
checking /dev/usb/scanner9... failed to open (Invalid argument)
checking /dev/usb/scanner10... failed to open (Invalid argument)
checking /dev/usb/scanner11... failed to open (Invalid argument)
checking /dev/usb/scanner12... failed to open (Invalid argument)
checking /dev/usb/scanner13... failed to open (Invalid argument)
checking /dev/usb/scanner14... failed to open (Invalid argument)
checking /dev/usb/scanner15... failed to open (Invalid argument)
checking /dev/usbscanner... failed to open (Invalid argument)
checking /dev/usbscanner0... failed to open (Invalid argument)
checking /dev/usbscanner1... failed to open (Invalid argument)
checking /dev/usbscanner2... failed to open (Invalid argument)
checking /dev/usbscanner3... failed to open (Invalid argument)
checking /dev/usbscanner4... failed to open (Invalid argument)
checking /dev/usbscanner5... failed to open (Invalid argument)
checking /dev/usbscanner6... failed to open (Invalid argument)
checking /dev/usbscanner7... failed to open (Invalid argument)
checking /dev/usbscanner8... failed to open (Invalid argument)
checking /dev/usbscanner9... failed to open (Invalid argument)
checking /dev/usbscanner10... failed to open (Invalid argument)
checking /dev/usbscanner11... failed to open (Invalid argument)
checking /dev/usbscanner12... failed to open (Invalid argument)
checking /dev/usbscanner13... failed to open (Invalid argument)
checking /dev/usbscanner14... failed to open (Invalid argument)
checking /dev/usbscanner15... failed to open (Invalid argument)
trying libusb:

<device descriptor of 0x090c/0x1000 at 001:008 (USB 2.0 USB  Flash Driver)>
bLength               18
bDescriptorType       1
bcdUSB                2.00
bDeviceClass          0
bDeviceSubClass       0
bDeviceProtocol       0
bMaxPacketSize0       64
idVendor              0x090C
idProduct             0x1000
bcdDevice             17.00
iManufacturer         1 (USB 2.0)
iProduct              2 (USB  Flash Driver)
iSerialNumber         3 (AA03000000026247)
bNumConfigurations    1
 <configuration 0>
 bLength              9
 bDescriptorType      2
 wTotalLength         32
 bNumInterfaces       1
 bConfigurationValue  1
 iConfiguration       0 ()
 bmAttributes         128 ()
 MaxPower             300 mA
  <interface 0>
   <altsetting 0>
   bLength            9
   bDescriptorType    4
   bInterfaceNumber   0
   bAlternateSetting  0
   bNumEndpoints      2
   bInterfaceClass    8
   bInterfaceSubClass 6
   bInterfaceProtocol 80
   iInterface         0 ()
    <endpoint 0>
    bLength           7
    bDescriptorType   5
    bEndpointAddress  0x81 (in 0x01)
    bmAttributes      2 (bulk)
    wMaxPacketSize    512
    bInterval         255 ms
    bRefresh          0
    bSynchAddress     0
    <endpoint 1>
    bLength           7
    bDescriptorType   5
    bEndpointAddress  0x02 (out 0x02)
    bmAttributes      2 (bulk)
    wMaxPacketSize    512
    bInterval         255 ms
    bRefresh          0
    bSynchAddress     0

<device descriptor of 0x04f9/0x0161 at 001:007>
bLength               18
bDescriptorType       1
bcdUSB                1.00
bDeviceClass          0
bDeviceSubClass       0
bDeviceProtocol       0
bMaxPacketSize0       8
idVendor              0x04F9
idProduct             0x0161
bcdDevice             1.00
iManufacturer         0 ()
iProduct              0 ()
iSerialNumber         3 (BROL4F264772)
bNumConfigurations    1
 <configuration 0>
 bLength              9
 bDescriptorType      2
 wTotalLength         85
 bNumInterfaces       3
 bConfigurationValue  1
 iConfiguration       0 ()
 bmAttributes         192 (Self-powered)
 MaxPower             2 mA
  <interface 0>
   <altsetting 0>
   bLength            9
   bDescriptorType    4
   bInterfaceNumber   0
   bAlternateSetting  0
   bNumEndpoints      2
   bInterfaceClass    7
   bInterfaceSubClass 1
   bInterfaceProtocol 2
   iInterface         0 ()
    <endpoint 0>
    bLength           7
    bDescriptorType   5
    bEndpointAddress  0x01 (out 0x01)
    bmAttributes      2 (bulk)
    wMaxPacketSize    64
    bInterval         0 ms
    bRefresh          0
    bSynchAddress     0
    <endpoint 1>
    bLength           7
    bDescriptorType   5
    bEndpointAddress  0x82 (in 0x02)
    bmAttributes      2 (bulk)
    wMaxPacketSize    16
    bInterval         0 ms
    bRefresh          0
    bSynchAddress     0
  <interface 1>
   <altsetting 0>
   bLength            9
   bDescriptorType    4
   bInterfaceNumber   1
   bAlternateSetting  0
   bNumEndpoints      3
   bInterfaceClass    255
   bInterfaceSubClass 255
   bInterfaceProtocol 255
   iInterface         0 ()
    <endpoint 0>
    bLength           7
    bDescriptorType   5
    bEndpointAddress  0x03 (out 0x03)
    bmAttributes      2 (bulk)
    wMaxPacketSize    16
    bInterval         0 ms
    bRefresh          0
    bSynchAddress     0
    <endpoint 1>
    bLength           7
    bDescriptorType   5
    bEndpointAddress  0x84 (in 0x04)
    bmAttributes      2 (bulk)
    wMaxPacketSize    64
    bInterval         0 ms
    bRefresh          0
    bSynchAddress     0
    <endpoint 2>
    bLength           7
    bDescriptorType   5
    bEndpointAddress  0x85 (in 0x05)
    bmAttributes      3 (interrupt)
    wMaxPacketSize    8
    bInterval         100 ms
    bRefresh          0
    bSynchAddress     0
  <interface 2>
   <altsetting 0>
   bLength            9
   bDescriptorType    4
   bInterfaceNumber   2
   bAlternateSetting  0
   bNumEndpoints      2
   bInterfaceClass    8
   bInterfaceSubClass 6
   bInterfaceProtocol 80
   iInterface         0 ()
    <endpoint 0>
    bLength           7
    bDescriptorType   5
    bEndpointAddress  0x08 (out 0x08)
    bmAttributes      2 (bulk)
    wMaxPacketSize    64
    bInterval         0 ms
    bRefresh          0
    bSynchAddress     0
    <endpoint 1>
    bLength           7
    bDescriptorType   5
    bEndpointAddress  0x89 (in 0x09)
    bmAttributes      2 (bulk)
    wMaxPacketSize    64
    bInterval         0 ms
    bRefresh          0
    bSynchAddress     0

<trying to find out which USB chip is used>
could not claim USB device interface
found USB scanner (vendor=0x04f9, product=0x0161) at libusb:001:007

<device descriptor of 0x03f0/0x2424 at 001:006>
bLength               18
bDescriptorType       1
bcdUSB                2.00
bDeviceClass          9
bDeviceSubClass       0
bDeviceProtocol       2
bMaxPacketSize0       64
idVendor              0x03F0
idProduct             0x2424
bcdDevice             0.00
iManufacturer         0 ()
iProduct              0 ()
iSerialNumber         0 ()
bNumConfigurations    1
 <configuration 0>
 bLength              9
 bDescriptorType      2
 wTotalLength         41
 bNumInterfaces       1
 bConfigurationValue  1
 iConfiguration       0 ()
 bmAttributes         224 (Self-poweredRemote Wakeup)
 MaxPower             2 mA
  <interface 0>
   <altsetting 0>
   bLength            9
   bDescriptorType    4
   bInterfaceNumber   0
   bAlternateSetting  0
   bNumEndpoints      1
   bInterfaceClass    9
   bInterfaceSubClass 0
   bInterfaceProtocol 1
   iInterface         0 ()
    <endpoint 0>
    bLength           7
    bDescriptorType   5
    bEndpointAddress  0x81 (in 0x01)
    bmAttributes      3 (interrupt)
    wMaxPacketSize    1
    bInterval         12 ms
    bRefresh          0
    bSynchAddress     0
   <altsetting 1>
   bLength            9
   bDescriptorType    4
   bInterfaceNumber   0
   bAlternateSetting  1
   bNumEndpoints      1
   bInterfaceClass    9
   bInterfaceSubClass 0
   bInterfaceProtocol 2
   iInterface         0 ()
    <endpoint 0>
    bLength           7
    bDescriptorType   5
    bEndpointAddress  0x81 (in 0x01)
    bmAttributes      3 (interrupt)
    wMaxPacketSize    1
    bInterval         12 ms
    bRefresh          0
    bSynchAddress     0

<device descriptor of 0x045e/0x0039 at 001:005 (Microsoft Microsoft 5-Button Mouse with IntelliEye(TM))>
bLength               18
bDescriptorType       1
bcdUSB                1.10
bDeviceClass          0
bDeviceSubClass       0
bDeviceProtocol       0
bMaxPacketSize0       8
idVendor              0x045E
idProduct             0x0039
bcdDevice             3.00
iManufacturer         1 (Microsoft)
iProduct              3 (Microsoft 5-Button Mouse with IntelliEye(TM))
iSerialNumber         0 ()
bNumConfigurations    1
 <configuration 0>
 bLength              9
 bDescriptorType      2
 wTotalLength         34
 bNumInterfaces       1
 bConfigurationValue  1
 iConfiguration       0 ()
 bmAttributes         160 (Remote Wakeup)
 MaxPower             100 mA
  <interface 0>
   <altsetting 0>
   bLength            9
   bDescriptorType    4
   bInterfaceNumber   0
   bAlternateSetting  0
   bNumEndpoints      1
   bInterfaceClass    3
   bInterfaceSubClass 1
   bInterfaceProtocol 2
   iInterface         0 ()
    <endpoint 0>
    bLength           7
    bDescriptorType   5
    bEndpointAddress  0x81 (in 0x01)
    bmAttributes      3 (interrupt)
    wMaxPacketSize    4
    bInterval         10 ms
    bRefresh          0
    bSynchAddress     0

<device descriptor of 0x413c/0x2107 at 001:004 (Dell Dell USB Entry Keyboard)>
bLength               18
bDescriptorType       1
bcdUSB                1.10
bDeviceClass          0
bDeviceSubClass       0
bDeviceProtocol       0
bMaxPacketSize0       8
idVendor              0x413C
idProduct             0x2107
bcdDevice             1.15
iManufacturer         1 (Dell)
iProduct              2 (Dell USB Entry Keyboard)
iSerialNumber         0 ()
bNumConfigurations    1
 <configuration 0>
 bLength              9
 bDescriptorType      2
 wTotalLength         34
 bNumInterfaces       1
 bConfigurationValue  1
 iConfiguration       0 ()
 bmAttributes         160 (Remote Wakeup)
 MaxPower             100 mA
  <interface 0>
   <altsetting 0>
   bLength            9
   bDescriptorType    4
   bInterfaceNumber   0
   bAlternateSetting  0
   bNumEndpoints      1
   bInterfaceClass    3
   bInterfaceSubClass 1
   bInterfaceProtocol 1
   iInterface         0 ()
    <endpoint 0>
    bLength           7
    bDescriptorType   5
    bEndpointAddress  0x81 (in 0x01)
    bmAttributes      3 (interrupt)
    wMaxPacketSize    8
    bInterval         10 ms
    bRefresh          0
    bSynchAddress     0

<device descriptor of 0x0b39/0x0d04 at 001:003 (USB KVM Switch 4 PORT V2.7 USB KVM Switch 4 PORT V2.7)>
bLength               18
bDescriptorType       1
bcdUSB                1.10
bDeviceClass          0
bDeviceSubClass       0
bDeviceProtocol       0
bMaxPacketSize0       8
idVendor              0x0B39
idProduct             0x0D04
bcdDevice             1.60
iManufacturer         1 (USB KVM Switch 4 PORT V2.7)
iProduct              2 (USB KVM Switch 4 PORT V2.7)
iSerialNumber         0 ()
bNumConfigurations    1
 <configuration 0>
 bLength              9
 bDescriptorType      2
 wTotalLength         59
 bNumInterfaces       2
 bConfigurationValue  1
 iConfiguration       2 (USB KVM Switch 4 PORT V2.7)
 bmAttributes         160 (Remote Wakeup)
 MaxPower             100 mA
  <interface 0>
   <altsetting 0>
   bLength            9
   bDescriptorType    4
   bInterfaceNumber   0
   bAlternateSetting  0
   bNumEndpoints      1
   bInterfaceClass    3
   bInterfaceSubClass 1
   bInterfaceProtocol 1
   iInterface         0 ()
    <endpoint 0>
    bLength           7
    bDescriptorType   5
    bEndpointAddress  0x81 (in 0x01)
    bmAttributes      3 (interrupt)
    wMaxPacketSize    8
    bInterval         10 ms
    bRefresh          0
    bSynchAddress     0
  <interface 1>
   <altsetting 0>
   bLength            9
   bDescriptorType    4
   bInterfaceNumber   1
   bAlternateSetting  0
   bNumEndpoints      1
   bInterfaceClass    3
   bInterfaceSubClass 1
   bInterfaceProtocol 2
   iInterface         0 ()
    <endpoint 0>
    bLength           7
    bDescriptorType   5
    bEndpointAddress  0x82 (in 0x02)
    bmAttributes      3 (interrupt)
    wMaxPacketSize    8
    bInterval         10 ms
    bRefresh          0
    bSynchAddress     0

<device descriptor of 0x05e3/0x0608 at 001:002 (USB2.0 Hub)>
bLength               18
bDescriptorType       1
bcdUSB                2.00
bDeviceClass          9
bDeviceSubClass       0
bDeviceProtocol       1
bMaxPacketSize0       64
idVendor              0x05E3
idProduct             0x0608
bcdDevice             119.60
iManufacturer         0 ()
iProduct              1 (USB2.0 Hub)
iSerialNumber         0 ()
bNumConfigurations    1
 <configuration 0>
 bLength              9
 bDescriptorType      2
 wTotalLength         25
 bNumInterfaces       1
 bConfigurationValue  1
 iConfiguration       0 ()
 bmAttributes         224 (Self-poweredRemote Wakeup)
 MaxPower             100 mA
  <interface 0>
   <altsetting 0>
   bLength            9
   bDescriptorType    4
   bInterfaceNumber   0
   bAlternateSetting  0
   bNumEndpoints      1
   bInterfaceClass    9
   bInterfaceSubClass 0
   bInterfaceProtocol 0
   iInterface         0 ()
    <endpoint 0>
    bLength           7
    bDescriptorType   5
    bEndpointAddress  0x81 (in 0x01)
    bmAttributes      3 (interrupt)
    wMaxPacketSize    1
    bInterval         12 ms
    bRefresh          0
    bSynchAddress     0

<device descriptor of 0x1d6b/0x0002 at 001:001 (Linux 4.4.0-38-generic ehci_hcd EHCI Host Controller)>
bLength               18
bDescriptorType       1
bcdUSB                2.00
bDeviceClass          9
bDeviceSubClass       0
bDeviceProtocol       0
bMaxPacketSize0       64
idVendor              0x1D6B
idProduct             0x0002
bcdDevice             4.04
iManufacturer         3 (Linux 4.4.0-38-generic ehci_hcd)
iProduct              2 (EHCI Host Controller)
iSerialNumber         1 (0000:00:13.2)
bNumConfigurations    1
 <configuration 0>
 bLength              9
 bDescriptorType      2
 wTotalLength         25
 bNumInterfaces       1
 bConfigurationValue  1
 iConfiguration       0 ()
 bmAttributes         224 (Self-poweredRemote Wakeup)
 MaxPower             0 mA
  <interface 0>
   <altsetting 0>
   bLength            9
   bDescriptorType    4
   bInterfaceNumber   0
   bAlternateSetting  0
   bNumEndpoints      1
   bInterfaceClass    9
   bInterfaceSubClass 0
   bInterfaceProtocol 0
   iInterface         0 ()
    <endpoint 0>
    bLength           7
    bDescriptorType   5
    bEndpointAddress  0x81 (in 0x01)
    bmAttributes      3 (interrupt)
    wMaxPacketSize    4
    bInterval         12 ms
    bRefresh          0
    bSynchAddress     0

<device descriptor of 0x1d6b/0x0001 at 003:001 (Linux 4.4.0-38-generic ohci_hcd OHCI PCI host controller)>
bLength               18
bDescriptorType       1
bcdUSB                1.10
bDeviceClass          9
bDeviceSubClass       0
bDeviceProtocol       0
bMaxPacketSize0       64
idVendor              0x1D6B
idProduct             0x0001
bcdDevice             4.04
iManufacturer         3 (Linux 4.4.0-38-generic ohci_hcd)
iProduct              2 (OHCI PCI host controller)
iSerialNumber         1 (0000:00:13.1)
bNumConfigurations    1
 <configuration 0>
 bLength              9
 bDescriptorType      2
 wTotalLength         25
 bNumInterfaces       1
 bConfigurationValue  1
 iConfiguration       0 ()
 bmAttributes         224 (Self-poweredRemote Wakeup)
 MaxPower             0 mA
  <interface 0>
   <altsetting 0>
   bLength            9
   bDescriptorType    4
   bInterfaceNumber   0
   bAlternateSetting  0
   bNumEndpoints      1
   bInterfaceClass    9
   bInterfaceSubClass 0
   bInterfaceProtocol 0
   iInterface         0 ()
    <endpoint 0>
    bLength           7
    bDescriptorType   5
    bEndpointAddress  0x81 (in 0x01)
    bmAttributes      3 (interrupt)
    wMaxPacketSize    2
    bInterval         255 ms
    bRefresh          0
    bSynchAddress     0

<device descriptor of 0x1d6b/0x0001 at 002:001 (Linux 4.4.0-38-generic ohci_hcd OHCI PCI host controller)>
bLength               18
bDescriptorType       1
bcdUSB                1.10
bDeviceClass          9
bDeviceSubClass       0
bDeviceProtocol       0
bMaxPacketSize0       64
idVendor              0x1D6B
idProduct             0x0001
bcdDevice             4.04
iManufacturer         3 (Linux 4.4.0-38-generic ohci_hcd)
iProduct              2 (OHCI PCI host controller)
iSerialNumber         1 (0000:00:13.0)
bNumConfigurations    1
 <configuration 0>
 bLength              9
 bDescriptorType      2
 wTotalLength         25
 bNumInterfaces       1
 bConfigurationValue  1
 iConfiguration       0 ()
 bmAttributes         224 (Self-poweredRemote Wakeup)
 MaxPower             0 mA
  <interface 0>
   <altsetting 0>
   bLength            9
   bDescriptorType    4
   bInterfaceNumber   0
   bAlternateSetting  0
   bNumEndpoints      1
   bInterfaceClass    9
   bInterfaceSubClass 0
   bInterfaceProtocol 0
   iInterface         0 ()
    <endpoint 0>
    bLength           7
    bDescriptorType   5
    bEndpointAddress  0x81 (in 0x01)
    bmAttributes      3 (interrupt)
    wMaxPacketSize    2
    bInterval         255 ms
    bRefresh          0
    bSynchAddress     0
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.
done
```

Here's a web page that suggests CanoScan Lide 120 is supported by something called "sane-genesys". 

[http://manpages.ubuntu.com/manpages/wily/man5/sane-genesys.5.html](http://manpages.ubuntu.com/manpages/wily/man5/sane-genesys.5.html)

And here is verbatim quote from that web page:

> At  present,  the
       following scanners are known to work with this backend:

              Canon LiDE 35/40/50/60/100/110/120/200/210/220/700

Anyway, if this is so, is my problem that I don't have this mysterious thing called "sane-genesys" installed? And if so, can someone tell me how to install it?

---

### Post by ajgreeny on 2016-09-30
Have you installed xsane?

That should have all you need as a dependency.

---

### Post by lukon on 2016-09-30
In response to your implied suggestion that I install Xsane, I installed Xsane. Then tried to scan. It still only recognizes the Brother scanner, not the Canon.

I also installed Xsane on one of my other computers that also runs 16.04 and is connected to the same two scanners. This time Xsane recognized the Canon scanner, but only produced a black rectangle for an image.

So anyway, it seems the web page I quoted above is obsolete. Sane (or Xsane) used to support the CanoScan LiDE 120 at the time. But not anymore. Or, not for 16.04. Or, not for whatever.

I therefore mark this thread as SOLVED, since there is really no solution. I just have to use my other (smaller) scanner until SANE/Xsane supports the Canon scanner again, if ever. Or scan in Windows. Or whatever other options I have.

---

### Post by ajgreeny on 2016-10-01
I have removed the Solved tag from this thread as it is not really solved and it is confusing to searchers if so tagged .

---

### Post by davidsrsb on 2016-10-04
My LIDE 100 is running with Simple Scan on 16.04.
This is a front end to SANE and is preferred to xsane on Ubuntu

The LIDE 100 and LIDE 120 are both listed in /etc/sane.d/genesys.conf

---

