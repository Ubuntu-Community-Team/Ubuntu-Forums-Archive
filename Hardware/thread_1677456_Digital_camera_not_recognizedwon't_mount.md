---
title: "Digital camera not recognized/won't mount"
date: 2011-01-28
forum: Hardware
---

### Post by Laysan_A on 2011-01-28
Hi,

I have a ge a1235 digital camera. I connected it and device  manager doesn't seem to see it. The camera itself says, "connection  failed".

/var/log/syslog says:

[32858.230072] usb 2-5: new high speed USB device using ehci_hcd and address 7

when it connects, and:

[32881.349981] usb 2-5: USB disconnect, address 7

after I shut it off.

Here's the output from sudo lsusb -v

```

Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
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
  iManufacturer           3 Linux 2.6.35-23-generic ohci_hcd
  iProduct                2 OHCI Host Controller
  iSerial                 1 0000:00:14.5
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
  wHubCharacteristic 0x0012
    No power switching (usb 1.0)
    No overcurrent protection
  bPwrOn2PwrGood        2 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
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
  iManufacturer           3 Linux 2.6.35-23-generic ohci_hcd
  iProduct                2 OHCI Host Controller
  iSerial                 1 0000:00:13.1
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
  wHubCharacteristic 0x0012
    No power switching (usb 1.0)
    No overcurrent protection
  bPwrOn2PwrGood        2 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
   Port 3: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

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
  iManufacturer           3 Linux 2.6.35-23-generic ohci_hcd
  iProduct                2 OHCI Host Controller
  iSerial                 1 0000:00:13.0
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
  wHubCharacteristic 0x0012
    No power switching (usb 1.0)
    No overcurrent protection
  bPwrOn2PwrGood        2 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
   Port 3: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

Bus 004 Device 002: ID 062a:0252 Creative Labs 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x062a Creative Labs
  idProduct          0x0252 
  bcdDevice            0.00
  iManufacturer           1 Logitech 
  iProduct                2 USB WheelMouse     
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
          wDescriptorLength      61
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
        wMaxPacketSize     0x0005  1x 5 bytes
        bInterval               2
Device Status:     0x0000
  (Bus Powered)

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
  iManufacturer           3 Linux 2.6.35-23-generic ohci_hcd
  iProduct                2 OHCI Host Controller
  iSerial                 1 0000:00:12.1
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
  wHubCharacteristic 0x0012
    No power switching (usb 1.0)
    No overcurrent protection
  bPwrOn2PwrGood        2 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0103 power enable connect
   Port 3: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

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
  iManufacturer           3 Linux 2.6.35-23-generic ohci_hcd
  iProduct                2 OHCI Host Controller
  iSerial                 1 0000:00:12.0
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
  wHubCharacteristic 0x0012
    No power switching (usb 1.0)
    No overcurrent protection
  bPwrOn2PwrGood        2 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
   Port 3: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

Bus 002 Device 010: ID 1b1e:9303  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x1b1e 
  idProduct          0x9303 
  bcdDevice            0.10
  iManufacturer           1 GE
  iProduct                2 A1250
  iSerial                 3 17B0JC0258
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           39
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xc0
      Self Powered
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass         6 Imaging
      bInterfaceSubClass      1 Still Image Capture
      bInterfaceProtocol      1 Picture Transfer Protocol (PIMA 15470)
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
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval              16
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0001
  Self Powered

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
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
  iManufacturer           3 Linux 2.6.35-23-generic ehci_hcd
  iProduct                2 EHCI Host Controller
  iSerial                 1 0000:00:13.2
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
  nNbrPorts             6
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
  bPwrOn2PwrGood       10 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
   Port 3: 0000.0100 power
   Port 4: 0000.0100 power
   Port 5: 0000.0503 highspeed power enable connect
   Port 6: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

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
  iManufacturer           3 Linux 2.6.35-23-generic ehci_hcd
  iProduct                2 EHCI Host Controller
  iSerial                 1 0000:00:12.2
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
  nNbrPorts             6
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
  bPwrOn2PwrGood       10 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
   Port 3: 0000.0100 power
   Port 4: 0000.0100 power
   Port 5: 0000.0100 power
   Port 6: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

```As you can see, the system sees it.

My /etc/fstab doesn't have an
 entry for either camera or usb, but then it doesn't have one for the 
cd/dvd either, and that works fine. In fact, I tried to put one for the 
cdrom in there once and the system yelled at me for it.

Sudo fdisk -l doesn't list it, with the camera plugged-in and on.

Oh, here's the configuration for camera in device notifier:

[[IMG]http://img375.imageshack.us/img375/503/devicenotifiercamera.png[/IMG]]("http://img375.imageshack.us/i/devicenotifiercamera.png/")

Uploaded with [ImageShack.us]("http://imageshack.us/")

I hope someone has an idea what's going on - it worked perfectly in karmic.

Oh, it doesn't show-up in dolphin or gwenview.

EDIT:

I changed the device settings in system settings, device actions, for camera from what you see above, to: 

[[IMG]http://img375.imageshack.us/img375/2316/devicenotifiercamera2.png[/IMG]]("http://img375.imageshack.us/i/devicenotifiercamera2.png/")

Uploaded with [ImageShack.us]("http://imageshack.us/")

and under system settings digital camera, a USB PTP Class camera shows-up, tests okay, and provides the following "information":

```

Manufacturer: GE 
Model: A1250 
  Version: 1.00
  Serial Number: 17B0JC0258

Capture Formats: JPEG
Display Formats: JPEG, Association/Directory

Device Capabilities:
    File Download, File Deletion, File Upload
    No Image Capture, No Open Capture, No vendor specific capture

Storage Devices Summary:
store_00010001:
    StorageDescription: None
    VolumeLabel: None
    Storage Type: Removable RAM (memory card)
    Filesystemtype: Digital Camera Layout (DCIM)
    Access Capability: Read-Write
    Maximum Capability: 3644981248 (3476 MB)
    Free Space (Bytes): 3641311232 (3472 MB)
    Free Space (Images): -1

Device Property Summary:
Battery Level(0x5001):(read only) (type=0x2) Range [1 - 100, step 1] value: 100% (100)
Date & Time(0x5011):(readwrite) (type=0xffff) '20110127T122034'

```Apparently, the system isn't picking-up all my memory either - I have an 8GB SD card in it (yes, it's supported). 

I also discovered something else that's kind of interesting. When I copy 
the "Command" above into konsole (kioclient exec camera:/) I get the 
following output, and a dolphin window opens with just a single file 
called USB Class PTP Camera in the File pane, and nothing else. When I 
open properties for it, it is called USB PTP Class Camera@usb:, and the 
path is shown thusly: Location: / (camera). It has no ownership. There 
is no entry for it I can find in /, or anywhere else.

When I click on the file to view the contents, dolphin gives me an 
informational icon and says it is loading the drivers, then it says, "Could not read file Could not lock the device".
This is beginning to sound a little more like a bug report (ubuntu) I found: [here.]("https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/285682/+index?comments=all")
But in that bug, apparently at least some (if not all) are able to access their camera in nautilus.

Terminal Output:
```

<unknown program name>(9605)/ ClientApp::doIt: Creating ClientApp
kioclient(9605) ClientApp::kde_open: KUrl("camera:/")
kioclient(9605) KSharedUiServerProxy::KSharedUiServerProxy: kuiserver registered
chris@desktop:~$ kioclient exec camera:/
<unknown program name>(20915)/ ClientApp::doIt: Creating ClientApp
kioclient(20915) ClientApp::kde_open: KUrl("camera:/")
kioclient(20915) KSharedUiServerProxy::KSharedUiServerProxy: kuiserver registered

```That's all I've got so far. Other than this, the only thing I've done is shut amarok off. (what's the kde equivalent to gvfs)

---

### Post by Laysan_A on 2011-01-30
Bump!

---

### Post by Laysan_A on 2011-01-31
(Bump)

---

### Post by Laysan_A on 2011-02-01
Bump!

---

### Post by Laysan_A on 2011-02-02
Anyone, please...

---

### Post by JayKay3OOO on 2011-02-02
Y'know what I would do? Well - what i've done is to pick up one of them usb SD card readers for £2 and simply plug that in when I need to transfer things from the camera. Ok, so you have to constantly take the SD card out the camera but you should not break it if you are careful.

Also comes in handy when you travel or use someone else's computer because you don't need software and it acts just like a flash drive.

---

### Post by Laysan_A on 2011-02-02
JayKay3OOO ! Hey!

Thanks so much for responding! 
(I'm really NOT alone...) :)

That's good advice, the more so given the number of replies I'm getting. :) However, it has become a matter of principle for me. Our camera doesn't work on either of our two machines, both running lucid. I want it fixed. Unfortunately I just don't have the technical knowledge to figure it out myself, and it appears no one really wants to get their hands dirty on this one (yet - I'll keep trying...;) ).

I would file a bug, but I'm not really even sure which package it should be filed against...

Actually I can get the pictures any time I want them just by using windows. 

Thanks very much! ):P

---

### Post by Laysan_A on 2011-02-04
Bump...

---

### Post by Laysan_A on 2011-02-07
Anyone?

---

### Post by Laysan_A on 2011-02-08
bump again...

---

### Post by deano_ferrari on 2011-02-11
I don't have a definite answer for you, but try opening dolphin manually with the camera connected, and type 'camera:/' in the location bar. If that results in errors, try again as  root with 'kdesu dolphin', then 'camera:/' in the location bar again.

I had similar errors occurring (with openSUSE), and  recently tried adjusting the system settings command to 'dolphin camera:/' (from kioclient exec camera:/). I also added myself to the 'wheel' group.

Seemed to have worked for me, but I'm not sure what helped. I'll continue experimenting to see if I can be a bit more definitive....

---

### Post by Laysan_A on 2011-02-11
Hi deano_ferrari,

Thanks very much for responding!

Opening the camera in dolphin (camera:/) produced the error, "Could not read file Could not lock the device). Folders appeared (as below), but no pictures, although the screen on the camera went dark (no connection failed error).

I think it would be appropriate to say here that the camera does work properly on windows, with the default windows driver.

Opening dolphin as root and typing camera:/ in the address bar produced a directory, but no pictures, and the camera still reported "connection failed." The directory, USB PTP Class Camera,  contained a folder, called "store_00010001", and two files: about.txt and summary.txt.

about.txt
```

PTP2 driver
(c) 2001-2005 by Mariusz Woloszyn <emsi@ipartners.pl>.
(c) 2003-2010 by Marcus Meissner <marcus@jet.franken.de>.
This driver supports cameras that support PTP or PictBridge(tm), and
Media Players that support the Media Transfer Protocol (MTP).

Enjoy!

```summary.txt
```

Manufacturer: GE 
Model: A1250 
  Version: 1.00
  Serial Number: 17B0JC0258

Capture Formats: JPEG
Display Formats: JPEG, Association/Directory

Device Capabilities:
    File Download, File Deletion, File Upload
    No Image Capture, No Open Capture, No vendor specific capture

Storage Devices Summary:
store_00010001:
    StorageDescription: None
    VolumeLabel: None
    Storage Type: Removable RAM (memory card)
    Filesystemtype: Digital Camera Layout (DCIM)
    Access Capability: Read-Write
    Maximum Capability: 3644981248 (3476 MB)
    Free Space (Bytes): 3644391424 (3475 MB)
    Free Space (Images): -1

Device Property Summary:
Battery Level(0x5001):(read only) (type=0x2) Range [1 - 100, step 1] value: 100% (100)
Date & Time(0x5011):(readwrite) (type=0xffff) '20110211T061337'

```Nothing new there, as far as I can see...The store_00010001 folder contains two empty folders, "DCIM", and "MISC", and a binary file of 257 bytes, called "DDISCVRY.DPS".

I'm pretty sure I tried editing my device manager (kioclient) settings to dolphin camera:/, but I'll give it another shot. I have no idea what the "wheel" group is.

Tried it, and got no results. Still don't know what the "wheel" group is...

Okay, I looked the wheel group up and found it is a PAM module that allows, basically, root privileges for its members. I might see the sense of this if being root fixed the issue (though likely not even then), but it didn't. 

I really appreciate the effort, thanks.

---

### Post by Laysan_A on 2011-02-15
bum....(I forget...)

---

