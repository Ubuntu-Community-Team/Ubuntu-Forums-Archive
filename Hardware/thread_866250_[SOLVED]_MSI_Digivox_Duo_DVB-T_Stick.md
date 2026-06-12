---
title: "[SOLVED] MSI Digivox Duo DVB-T Stick"
date: 2008-07-21
forum: Hardware
---

### Post by kikaha on 2008-07-21
Hallo all,

I can't make this device running and need a helping hand. What I did till now:

I'm running Kernel 2.6.24-19-generic on a Compaq Evo N800w with USB 2.0 Ports

- Get in contact with LinuxTV
- They have extended the driver (many thanks to Antti!)
- Load the actual firmware

I get the following results:

{{{
dmesg | grep -i dvb

[   44.183584] dvb_usb_af9015: probe of 3-3:1.0 failed with error -110
[   44.183615] usbcore: registered new interface driver dvb_usb_af9015
}}}

{{{
sudo lsusb -v

Bus 003 Device 006: ID 1462:8801 Micro Star International 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x1462 Micro Star International
  idProduct          0x8801 
  bcdDevice            2.00
  iManufacturer           1 Afatech
  iProduct                2 DVB-T 2
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           46
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
      bNumEndpoints           4
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
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
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x85  EP 5 IN
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

Bus 003 Device 001: ID 0000:0000  
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
  iManufacturer           3 Linux 2.6.24-19-generic ehci_hcd
  iProduct                2 EHCI Host Controller
  iSerial                 1 0000:02:0e.2
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
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             5
  wHubCharacteristic 0x0009
    Per-port power switching
    Per-port overcurrent protection
    TT think time 8 FS bits
  bPwrOn2PwrGood       10 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
   Port 3: 0000.0503 highspeed power enable connect
   Port 4: 0000.0100 power
   Port 5: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

Bus 002 Device 001: ID 0000:0000  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x0000 
  idProduct          0x0000 
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.24-19-generic ohci_hcd
  iProduct                2 OHCI Host Controller
  iSerial                 1 0000:02:0e.1
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
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             2
  wHubCharacteristic 0x0002
    No power switching (usb 1.0)
    Ganged overcurrent protection
  bPwrOn2PwrGood      255 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

Bus 001 Device 004: ID 049f:0076 Compaq Computer Corp. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x049f Compaq Computer Corp.
  idProduct          0x0076 
  bcdDevice            0.00
  iManufacturer           0 
  iProduct                1 Compaq WLAN MultiPort W200
  iSerial                 2 PG41JL9AJLNZ
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           42
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xc0
      Self Powered
    MaxPower              420mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
      ** UNRECOGNIZED:  03 08 0f
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
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
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
Device Status:     0x0001
  Self Powered

Bus 001 Device 003: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x046d Logitech, Inc.
  idProduct          0xc016 M-UV69a Optical Wheel Mouse
  bcdDevice            3.40
  iManufacturer           1 Logitech
  iProduct                2 Optical USB Mouse
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
    MaxPower              100mA
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
          wDescriptorLength      52
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
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              10
Device Status:     0x0000
  (Bus Powered)

Bus 001 Device 001: ID 0000:0000  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x0000 
  idProduct          0x0000 
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.24-19-generic ohci_hcd
  iProduct                2 OHCI Host Controller
  iSerial                 1 0000:02:0e.0
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
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             3
  wHubCharacteristic 0x0002
    No power switching (usb 1.0)
    Ganged overcurrent protection
  bPwrOn2PwrGood      255 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0303 lowspeed power enable connect
   Port 2: 0000.0100 power
   Port 3: 0000.0103 power enable connect
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled
}}}

'''- Stick removed and connected again'''

{{{
dmesg | grep -i dvb

[   44.183584] dvb_usb_af9015: probe of 3-3:1.0 failed with error -110
[   44.183615] usbcore: registered new interface driver dvb_usb_af9015
[  187.243378] dvb-usb: found a 'MSI DIGIVOX Duo' in cold state, will try to load a firmware
[  102.045128] dvb-usb: downloading firmware from file 'dvb-usb-af9015.fw'
[  102.105834] dvb-usb: generic DVB-USB module successfully deinitialized and disconnected.
[  188.137811] dvb-usb: found a 'MSI DIGIVOX Duo' in warm state.
[  188.137929] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[  188.138665] DVB: registering new adapter (MSI DIGIVOX Duo)
[  102.928130] DVB: registering frontend 0 (Afatech AF9013 DVB-T)...
[  103.034065] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[  103.034656] DVB: registering new adapter (MSI DIGIVOX Duo)
[  190.256057] af9013: found a 'Afatech AF9013 DVB-T' in warm state.
[  190.272186] DVB: registering frontend 1 (Afatech AF9013 DVB-T)...
[  190.272453] dvb-usb: MSI DIGIVOX Duo successfully initialized and connected.
}}}

'''- Channel Scan with Kaffeine'''

{{{
kbuildsycoca running...
Reusing existing ksycoca
/dev/dvb/adapter0/frontend0 : opened ( Afatech AF9013 DVB-T )
/dev/dvb/adapter1/frontend0 : opened ( Afatech AF9013 DVB-T )
0 EPG plugins loaded for device 0:0.
0 EPG plugins loaded for device 1:0.
Loaded epg data : 0 events (1 msecs)
kio (KMimeType): WARNING: KServiceType::offers : servicetype ThumbCreator not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype ThumbCreator not found
tom@super-klappi:~$ DvbCam::probe(): /dev/dvb/adapter0/ca0: : No such file or directory
Using DVB device 0:0 "Afatech AF9013 DVB-T"
tuning DVB-T to 402000000 Hz
inv:2 bw:0 fecH:9 fecL:9 mod:6 tm:2 gi:4 hier:4
.FE_READ_STATUS: Remote I/O error

Transponders: 1/63

Invalid section length or timeout: pid=17

Frontend closed
openFe:: Device or resource busy
dvbsi: Cant tune DVB
openFe:: Device or resource busy
dvbsi: Cant tune DVB
openFe:: Device or resource busy
dvbsi: Cant tune DVB
openFe:: Device or resource busy
dvbsi: Cant tune DVB
openFe:: Device or resource busy
dvbsi: Cant tune DVB
openFe:: Device or resource busy
dvbsi: Cant tune DVB
openFe:: Device or resource busy
dvbsi: Cant tune DVB
openFe:: Device or resource busy
dvbsi: Cant tune DVB
openFe:: Device or resource busy
dvbsi: Cant tune DVB
openFe:: Device or resource busy
dvbsi: Cant tune DVB
Using DVB device 0:0 "Afatech AF9013 DVB-T"
tuning DVB-T to 490000000 Hz
inv:2 bw:0 fecH:9 fecL:9 mod:6 tm:2 gi:4 hier:4
.FE_READ_STATUS: Remote I/O error

Transponders: 12/63

Invalid section length or timeout: pid=17

Frontend closed
openFe:: Device or resource busy
dvbsi: Cant tune DVB
openFe:: Device or resource busy
dvbsi: Cant tune DVB
Using DVB device 0:0 "Afatech AF9013 DVB-T"
tuning DVB-T to 514000000 Hz
inv:2 bw:0 fecH:9 fecL:9 mod:6 tm:2 gi:4 hier:4
.FE_READ_STATUS: Remote I/O error

Transponders: 15/63

Invalid section length or timeout: pid=17

Frontend closed
openFe:: Device or resource busy
dvbsi: Cant tune DVB
openFe:: Device or resource busy
dvbsi: Cant tune DVB
Using DVB device 0:0 "Afatech AF9013 DVB-T"
tuning DVB-T to 538000000 Hz
inv:2 bw:0 fecH:9 fecL:9 mod:6 tm:2 gi:4 hier:4
.FE_READ_STATUS: Remote I/O error

Transponders: 18/63

Invalid section length or timeout: pid=17

Frontend closed
openFe:: Device or resource busy
dvbsi: Cant tune DVB
openFe:: Device or resource busy
dvbsi: Cant tune DVB
openFe:: Device or resource busy
dvbsi: Cant tune DVB
openFe:: Device or resource busy
dvbsi: Cant tune DVB
openFe:: Device or resource busy
dvbsi: Cant tune DVB
openFe:: Device or resource busy
dvbsi: Cant tune DVB
openFe:: Device or resource busy
dvbsi: Cant tune DVB
openFe:: Device or resource busy
dvbsi: Cant tune DVB
openFe:: Device or resource busy
dvbsi: Cant tune DVB
openFe:: Device or resource busy
dvbsi: Cant tune DVB
Using DVB device 0:0 "Afatech AF9013 DVB-T"
tuning DVB-T to 626000000 Hz
inv:2 bw:0 fecH:9 fecL:9 mod:6 tm:2 gi:4 hier:4
.FE_READ_STATUS: Remote I/O error

Transponders: 29/63

Invalid section length or timeout: pid=17

Frontend closed
openFe:: Device or resource busy
dvbsi: Cant tune DVB
openFe:: Device or resource busy
dvbsi: Cant tune DVB
openFe:: Device or resource busy
dvbsi: Cant tune DVB
openFe:: Device or resource busy
dvbsi: Cant tune DVB
openFe:: Device or resource busy
dvbsi: Cant tune DVB
openFe:: Device or resource busy
dvbsi: Cant tune DVB
openFe:: Device or resource busy
dvbsi: Cant tune DVB
openFe:: Device or resource busy
dvbsi: Cant tune DVB
openFe:: Device or resource busy
dvbsi: Cant tune DVB
openFe:: Device or resource busy
dvbsi: Cant tune DVB
Using DVB device 0:0 "Afatech AF9013 DVB-T"
tuning DVB-T to 714000000 Hz
inv:2 bw:0 fecH:9 fecL:9 mod:6 tm:2 gi:4 hier:4
.FE_READ_STATUS: Remote I/O error

Transponders: 40/63

Invalid section length or timeout: pid=17

Frontend closed
openFe:: Device or resource busy
dvbsi: Cant tune DVB
openFe:: Device or resource busy
dvbsi: Cant tune DVB
openFe:: Device or resource busy
dvbsi: Cant tune DVB
openFe:: Device or resource busy
dvbsi: Cant tune DVB
openFe:: Device or resource busy
dvbsi: Cant tune DVB
openFe:: Device or resource busy
dvbsi: Cant tune DVB
openFe:: Device or resource busy
dvbsi: Cant tune DVB
openFe:: Device or resource busy
dvbsi: Cant tune DVB
openFe:: Device or resource busy
dvbsi: Cant tune DVB
openFe:: Device or resource busy
dvbsi: Cant tune DVB
Using DVB device 0:0 "Afatech AF9013 DVB-T"
tuning DVB-T to 802000000 Hz
inv:2 bw:0 fecH:9 fecL:9 mod:6 tm:2 gi:4 hier:4
.FE_READ_STATUS: Remote I/O error

Transponders: 51/63

Invalid section length or timeout: pid=17

Frontend closed
openFe:: Device or resource busy
dvbsi: Cant tune DVB
openFe:: Device or resource busy
dvbsi: Cant tune DVB
Using DVB device 0:0 "Afatech AF9013 DVB-T"
tuning DVB-T to 826000000 Hz
inv:2 bw:0 fecH:9 fecL:9 mod:6 tm:2 gi:4 hier:4
.FE_READ_STATUS: Remote I/O error

Transponders: 54/63

Invalid section length or timeout: pid=17

Frontend closed
openFe:: Device or resource busy
dvbsi: Cant tune DVB
openFe:: Device or resource busy
dvbsi: Cant tune DVB
openFe:: Device or resource busy
dvbsi: Cant tune DVB
openFe:: Device or resource busy
dvbsi: Cant tune DVB
openFe:: Device or resource busy
dvbsi: Cant tune DVB
openFe:: Device or resource busy
dvbsi: Cant tune DVB
openFe:: Device or resource busy
dvbsi: Cant tune DVB
openFe:: Device or resource busy
dvbsi: Cant tune DVB
openFe:: Device or resource busy
dvbsi: Cant tune DVB
Transponders: 63
dvbsi: The end :)
Channels found: 0
}}}

{{{
dmesg | grep -i dvb

[  413.586366] dvb-usb: could not handle pid_parser
[  784.158141] dvb-usb: could not handle pid_parser
[  805.179080] dvb-usb: could not handle pid_parser
[  825.052516] dvb-usb: could not handle pid_parser
[  850.053839] dvb-usb: could not handle pid_parser
[  874.505176] dvb-usb: could not handle pid_parser
[  899.071257] dvb-usb: could not handle pid_parser
[  917.630488] dvb-usb: could not handle pid_parser

}}}

'''Statement from Antti Palosaari'''

I don't know whats wrong but it looks like coming from PID-filter. You 
have only USB1.1 ports? [Have checked this with Sysinfo, results see below]

Driver will disable 2nd tuner / frontend if there is only USB1.1 because 
  I don't know if there is any way to use PID-filters for 2nd frontend. 
Also FE#1 performance is bad in dual tuner device for unknown reason. 
But I still don't see reason why your device is not working.

Thats weird situation:
dual mode (2 receivers):
FE#1 bad
FE#2 good
single mode (1 receiver):
FE#1 good

'''Sysinfo'''

NEC Corporation USB (rev 41) (prog -if 10 [OHCI])

NEC Corporation USB (rev 41) (prog -if 10 [OHCI])

NEC Corporation USB 2.0 (rev 2) (prog -if 20 [EHCI])

I hope that someone can help me. Especially the PID issue is a blackox for me :(

Thanks
Thomas

---

### Post by kikaha on 2008-07-22
Update:

After getting the newest firmware from [http://www.otit.fi/~crope/v4l-dvb/af9015/af9015_firmware_cutter/firmware_files/](http://www.otit.fi/~crope/v4l-dvb/af9015/af9015_firmware_cutter/firmware_files/) and safed the file under /lib/firmware everything works fine.

Many thanks to Antti Palosaari from LinuxTv for his quick and professional support!

---

### Post by desmane on 2008-11-29
can you watch and record different channels at the same time??

---

