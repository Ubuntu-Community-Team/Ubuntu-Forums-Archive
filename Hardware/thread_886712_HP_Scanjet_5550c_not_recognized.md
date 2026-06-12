---
title: "HP Scanjet 5550c not recognized"
date: 2008-08-11
forum: Hardware
---

### Post by petzler on 2008-08-11
Hi,

I running ubuntu 8.0.4.1 and connected an HP ScanJet 5550c. Following the SANE doc, the driver 5590 is sufficient.

Following some threads I added: 

usb 0x03F0 0x1205

to /etc/sane.d/hp5590.conf 

since sane-find-scanner gives:

found USB scanner (vendor=0x03f0 [Hewlett-Packard], product=0x1205 [hp scanjet scanner]) at libusb:002:005

but scanimage won't work:

$  SANE_DEBUG_HP5590=255 scanimage -L 
[sanei_debug] Setting debug level of hp5590 to 255.
[hp5590] SANE backed for HP 5550/5590/7650 1.0.2
[hp5590] (c) Ilia Sotnikov <hostcc@gmail.com>
[hp5590] attach_usb_device: Opening USB device
[hp5590] attach_usb_device: USB device opened
[hp5590] hp5590_init_scanner
[hp5590] hp5590_cmd: USB-in-USB: command : 0012
[hp5590] hp5590_control_msg: USB-in-USB: core data: no
[hp5590] hp5590_control_msg: USB-in-USB: sending control msg
[hp5590] hp5590_control_msg: USB-in-USB: checking acknowledge for control message
[hp5590] hp5590_get_ack
[hp5590] hp5590_get_ack: USB-in-USB: error getting acknowledge
[hp5590] sane_hp5590_get_devices, local only: 0
[hp5590] Found 0 devices
device `v4l:/dev/video0' is a Noname BT878 video (Hauppauge (bt878)) virtual device
[hp5590] sane_hp5590_exit

As you can see, I have a BT878 card :-) The scanner works on WinXP. How can I get it working?

Thanks,
Olaf

Anyway, some more infos hopefully to be usefull:

$ sane-find-scanner -v -v -v
This is sane-find-scanner from sane-backends 1.0.19

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

<device descriptor of 0x0000/0x0000 at 007:001>
bLength               18
bDescriptorType       1
bcdUSB                1.10
bDeviceClass          9
bDeviceSubClass       0
bDeviceProtocol       0
bMaxPacketSize0       64
idVendor              0x0000
idProduct             0x0000
bcdDevice             2.06
iManufacturer         3 ((null))
iProduct              2 ((null))
iSerialNumber         1 ((null))
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

<device descriptor of 0x0000/0x0000 at 006:001>
bLength               18
bDescriptorType       1
bcdUSB                1.10
bDeviceClass          9
bDeviceSubClass       0
bDeviceProtocol       0
bMaxPacketSize0       64
idVendor              0x0000
idProduct             0x0000
bcdDevice             2.06
iManufacturer         3 ((null))
iProduct              2 ((null))
iSerialNumber         1 ((null))
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

<device descriptor of 0x0000/0x0000 at 005:001>
bLength               18
bDescriptorType       1
bcdUSB                2.00
bDeviceClass          9
bDeviceSubClass       0
bDeviceProtocol       1
bMaxPacketSize0       64
idVendor              0x0000
idProduct             0x0000
bcdDevice             2.06
iManufacturer         3 ((null))
iProduct              2 ((null))
iSerialNumber         1 ((null))
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

<device descriptor of 0x03f0/0x1205 at 004:004>
bLength               18
bDescriptorType       1
bcdUSB                2.00
bDeviceClass          255
bDeviceSubClass       255
bDeviceProtocol       255
bMaxPacketSize0       64
idVendor              0x03F0
idProduct             0x1205
bcdDevice             2.00
iManufacturer         1 ((null))
iProduct              2 ((null))
iSerialNumber         12 ((null))
bNumConfigurations    1
 <configuration 0>
 bLength              9
 bDescriptorType      2
 wTotalLength         39
 bNumInterfaces       1
 bConfigurationValue  1
 iConfiguration       0 ()
 bmAttributes         192 (Self-powered)
 MaxPower             10 mA
  <interface 0>
   <altsetting 0>
   bLength            9
   bDescriptorType    4
   bInterfaceNumber   0
   bAlternateSetting  0
   bNumEndpoints      3
   bInterfaceClass    16
   bInterfaceSubClass 1
   bInterfaceProtocol 0
   iInterface         0 ()
    <endpoint 0>
    bLength           7
    bDescriptorType   5
    bEndpointAddress  0x81 (in 0x01)
    bmAttributes      2 (bulk)
    wMaxPacketSize    512
    bInterval         0 ms
    bRefresh          0
    bSynchAddress     0
    <endpoint 1>
    bLength           7
    bDescriptorType   5
    bEndpointAddress  0x02 (out 0x02)
    bmAttributes      2 (bulk)
    wMaxPacketSize    512
    bInterval         0 ms
    bRefresh          0
    bSynchAddress     0
    <endpoint 2>
    bLength           7
    bDescriptorType   5
    bEndpointAddress  0x83 (in 0x03)
    bmAttributes      3 (interrupt)
    wMaxPacketSize    1
    bInterval         8 ms
    bRefresh          0
    bSynchAddress     0

<trying to find out which USB chip is used>
    checking for GT-6801 ...
    this is not a GT-6801 (bcdUSB = 0x200)
    checking for GT-6816 ...
    this is not a GT-6816 (bDeviceClass = 255, bInterfaceClass = 16)
    checking for GT-8911 ...
    this is not a GT-8911 (check 1, bDeviceClass = 255, bInterfaceClass = 16)
    checking for MA-1017 ...
    this is not a MA-1017 (bDeviceClass = 255, bInterfaceClass = 16)
    checking for MA-1015 ...
    this is not a MA-1015 (bcdUSB = 0x200)
    checking for MA-1509 ...
    this is not a MA-1509 (bcdUSB = 0x200)
    checking for LM983[1,2,3] ...
    this is not a LM983x (bDeviceClass = 255, bInterfaceClass = 16)
    checking for GL646 ...
    this is not a GL646 (bDeviceClass = 255, bInterfaceClass = 16)
    checking for GL646_HP ...
    this is not a GL646_HP (bDeviceClass = 255, bInterfaceClass = 16)
    checking for GL660+GL646 ...
    this is not a GL660+GL646 (bDeviceClass = 255, bInterfaceClass = 16)
    checking for GL84x ...
    this is not a GL841 (bDeviceClass = 255, bInterfaceClass = 16)
    checking for ICM532B ...
    this is not a ICM532B (check 1, bDeviceClass = 255, bInterfaceClass = 16)
    checking for PV8630/LM9830 ...
    this is not a PV8630/LM9830 (bDeviceClass = 255)
    checking for M011 ...
    this is not a M011 (bcdUSB = 0x200)
    checking for RTS8822 ...
    this is not a RTS8822 (bDeviceClass = 255)
    checking for rts8858c ...
    this is not a rts8858c (bDeviceClass = 255)
    checking for SQ113 ...
    this is not a SQ113 (bDeviceClass = 255)
    checking for HP5550/5590/7650 chipset ...
  Couldn't set configuration: could not set config 1: Value too large for defined data type
    checking for rts8801/rts8891 ...
    this is not a rts8801/rts8891 (bDeviceClass = 255)
<Couldn't determine the type of the USB chip (result from sane-backends 1.0.19)>

found USB scanner (vendor=0x03f0, product=0x1205) at libusb:004:004

<device descriptor of 0x04b4/0x6560 at 004:003>
bLength               18
bDescriptorType       1
bcdUSB                2.00
bDeviceClass          9
bDeviceSubClass       0
bDeviceProtocol       2
bMaxPacketSize0       64
idVendor              0x04B4
idProduct             0x6560
bcdDevice             0.09
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

<device descriptor of 0x0000/0x0000 at 004:001>
bLength               18
bDescriptorType       1
bcdUSB                2.00
bDeviceClass          9
bDeviceSubClass       0
bDeviceProtocol       1
bMaxPacketSize0       64
idVendor              0x0000
idProduct             0x0000
bcdDevice             2.06
iManufacturer         3 ((null))
iProduct              2 ((null))
iSerialNumber         1 ((null))
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

<device descriptor of 0x046d/0xabd0 at 003:004>
bLength               18
bDescriptorType       1
bcdUSB                1.10
bDeviceClass          0
bDeviceSubClass       0
bDeviceProtocol       0
bMaxPacketSize0       8
idVendor              0x046D
idProduct             0xABD0
bcdDevice             65.02
iManufacturer         1 ((null))
iProduct              2 ((null))
iSerialNumber         0 ()
bNumConfigurations    1
 <configuration 0>

 bLength              9
 bDescriptorType      2
 wTotalLength         34
 bNumInterfaces       1
 bConfigurationValue  1
 iConfiguration       0 ()
 bmAttributes         128 ()
 MaxPower             98 mA
  <interface 0>
   <altsetting 0>
   bLength            9
   bDescriptorType    4
   bInterfaceNumber   0
   bAlternateSetting  0
   bNumEndpoints      1
   bInterfaceClass    3
   bInterfaceSubClass 0
   bInterfaceProtocol 0
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

<device descriptor of 0x046d/0xc50c at 003:003>
bLength               18
bDescriptorType       1
bcdUSB                1.10
bDeviceClass          0
bDeviceSubClass       0
bDeviceProtocol       0
bMaxPacketSize0       8
idVendor              0x046D
idProduct             0xC50C
bcdDevice             34.40
iManufacturer         1 ((null))
iProduct              2 ((null))
iSerialNumber         0 ()
bNumConfigurations    1
 <configuration 0>
 bLength              9
 bDescriptorType      2
 wTotalLength         59
 bNumInterfaces       2
 bConfigurationValue  1
 iConfiguration       0 ()
 bmAttributes         160 (Remote Wakeup)
 MaxPower             98 mA
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

<device descriptor of 0x0451/0x2036 at 003:002>
bLength               18
bDescriptorType       1
bcdUSB                1.10
bDeviceClass          9
bDeviceSubClass       0
bDeviceProtocol       0
bMaxPacketSize0       8
idVendor              0x0451
idProduct             0x2036
bcdDevice             1.01
iManufacturer         0 ()
iProduct              1 ((null))
iSerialNumber         0 ()
bNumConfigurations    1
 <configuration 0>
 bLength              9
 bDescriptorType      2
 wTotalLength         25
 bNumInterfaces       1
 bConfigurationValue  1
 iConfiguration       1 ((null))
 bmAttributes         160 (Remote Wakeup)
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
   iInterface         1 ((null))
    <endpoint 0>
    bLength           7
    bDescriptorType   5
    bEndpointAddress  0x81 (in 0x01)
    bmAttributes      3 (interrupt)
    wMaxPacketSize    1
    bInterval         255 ms
    bRefresh          0
    bSynchAddress     0

<device descriptor of 0x0000/0x0000 at 003:001>
bLength               18
bDescriptorType       1
bcdUSB                1.10
bDeviceClass          9
bDeviceSubClass       0
bDeviceProtocol       0
bMaxPacketSize0       64
idVendor              0x0000
idProduct             0x0000
bcdDevice             2.06
iManufacturer         3 ((null))
iProduct              2 ((null))
iSerialNumber         1 ((null))
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

<device descriptor of 0x0000/0x0000 at 002:001>
bLength               18
bDescriptorType       1
bcdUSB                1.10
bDeviceClass          9
bDeviceSubClass       0
bDeviceProtocol       0
bMaxPacketSize0       64
idVendor              0x0000
idProduct             0x0000
bcdDevice             2.06
iManufacturer         3 ((null))
iProduct              2 ((null))
iSerialNumber         1 ((null))
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

<device descriptor of 0x0000/0x0000 at 001:001>
bLength               18
bDescriptorType       1
bcdUSB                1.10
bDeviceClass          9
bDeviceSubClass       0
bDeviceProtocol       0
bMaxPacketSize0       64
idVendor              0x0000
idProduct             0x0000
bcdDevice             2.06
iManufacturer         3 ((null))
iProduct              2 ((null))
iSerialNumber         1 ((null))
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

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.
done

---

### Post by silkstone on 2008-08-11
It sounds as if this scanner is not supported by XSane.

The following link refers to a different model, but if you scroll down there's a reference to the 5550c in the Comments section.

[http://www.sane-project.org/unsupported/hp-scanjet-4570c.html](http://www.sane-project.org/unsupported/hp-scanjet-4570c.html)

No help, I'm afraid.

EDIT/ Also this...

[http://www.sane-project.org/unsupported/hp-scanjet-5550c.html](http://www.sane-project.org/unsupported/hp-scanjet-5550c.html)

---

### Post by petzler on 2008-08-11
Probably HP did chip the scanner with different USB Chips - thereofre some pictures. hp-setup didn't found the scanner too - even if this is working on WinXP!

Thanks,
Olaf

---

### Post by IntuitiveNipple on 2008-08-25
Maybe this will give you some hope? It works with zero-configuration here... just plug it in and Xsane recognises it.

**HP ScanJet 5550c**

```

$ uname -a
Linux hephaestion 2.6.24-21-generic #1 SMP Tue Aug 12 13:03:01 UTC 2008 x86_64 GNU/Linux

$  lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 8.04.1
Release:	8.04
Codename:	hardy

$ lsusb | grep '03f0:1205'
Bus 005 Device 008: ID 03f0:1205 Hewlett-Packard 

$ ls /etc/sane.d/hp5590.conf
ls: cannot access /etc/sane.d/hp5590.conf: No such file or directory

$ sudo apt-get install sane-utils

$ sane-find-scanner -vvv | grep '^found'
found USB scanner (vendor=0x03f0 [Hewlett-Packard], product=0x1205 [hp scanjet scanner], chip=GL841?) at libusb:005:008

$ SANE_DEBUG_HP5590=255 scanimage -L | grep hp5590
[sanei_debug] Setting debug level of hp5590 to 255.
[hp5590] SANE backed for HP 5550/5590/7650 1.0.2
[hp5590] (c) Ilia Sotnikov <hostcc@gmail.com>
[hp5590] attach_usb_device: Opening USB device
[hp5590] attach_usb_device: USB device opened
...
[hp5590] sane_hp5590_get_devices, local only: 0
[hp5590] Found 1 devices
[hp5590] sane_hp5590_exit
device `hp5590:libusb:005:008' is a HP 5550 Workgroup scanner

$ dpkg-query -W -f='${Status;1} ${Package} ${Version}\n' '*sane*' | grep '^i'
i libsane 1.0.19-1ubuntu3
i sane-utils 1.0.19-1ubuntu3
i xsane 0.995-1ubuntu1
i xsane-common 0.995-1ubuntu1

```

So that you can compare results I've attached a gzip-ed log of the output of:
```

$ SANE_DEBUG_HP5590=255 scanimage -L

```

I've also attached two photographs: one of the circuit board for comparison with yours, and one of the embossed printing on the base of the case.

---

