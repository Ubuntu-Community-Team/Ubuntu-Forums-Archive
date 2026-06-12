---
title: "Installation of HP fingerprint reader?"
date: 2009-04-07
forum: Hardware
---

### Post by har02052 on 2009-04-07
Anybody been able to effectively install and configure the correct drivers/software to work a built in fingerprint reader on an HP laptop?
I have a HP DV4T-1000, Jaunty.
I installed fprint for jaunty, but it says that there are no recognized devices.  Any help?  Thanks.

---

### Post by ajmctaggart on 2009-04-07
I assume you found this thread already...
[http://ubuntuforums.org/showthread.php?t=376432]("http://ubuntuforums.org/showthread.php?t=376432")
Which I'm sure isn't much help...

List the output of:
 ```
lsusb
```

That will help us figure out if your device is supported w/ any Linux distro...

Thanks!

---

### Post by har02052 on 2009-04-07
output of lsusb

Bus 002 Device 002: ID 046d:09b8 Logitech, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 138a:0001  
Bus 003 Device 002: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

I did look at the other post and because he had no luck with the Thinkpad drivers, I made no attempt at following the wiki instructions.

---

### Post by ajmctaggart on 2009-04-07
Thank you,

Unfortunately it looks like a known bug that I really can't help with.  Basically it's a two part issue.  One, it's not getting recognized correctly (which I believe is now fixable via reading those threads in Launchpad, url attached below), and the fact that there is currently no driver (which I believe they are diligently working on).  

In the past I have seen better management of these devices through a distro like OpenSuse, but I am not sure if there is a point in looking there for this.  Perhaps by burning a Live Cd of Opensuse and seeing if it is recognized or picked up?    

I suggest to follow this thread for development, or look into this by using LaunchPad and subscribing to the bug...
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/285089]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/285089")

---

### Post by har02052 on 2009-04-07
Awesome, thanks.  I figured the whole fingerprint reader thing was pretty new to most computers so I figured that there might not be a working easy solution yet.  I will subscribe to the bug.  There was an update to the usb update ids so that the system now sees the reader, even though it names it incorrectly, it has to be named correctly before drivers can be effective.  Thanks for your help.
This is my lsusb now:
Bus 002 Device 002: ID 046d:09b8 Logitech, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 003 Device 003: ID 138a:0001 DigitalPersona, Inc Fingeprint Reader**
Bus 003 Device 002: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by ajmctaggart on 2009-04-07
No problem, 

I haven't had the best of luck on those things either...but keep an eye on OpenSuse forums...like I said their Pam/Yast configuration does make things easier in that department sometimes.  Although in Jaunty, fingerprint is supposed to be rockin!

Good Luck!

---

### Post by mk6032 on 2010-02-16
I've got the same on my laptop. Details of lsusb:

Device: ID 138a:0001 DigitalPersona, Inc Fingeprint Reader
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass          255 Vendor Specific Class
  bDeviceSubClass         0 
  bDeviceProtocol       255 
  bMaxPacketSize0         8
  idVendor           0x138a DigitalPersona, Inc
  idProduct          0x0001 Fingeprint Reader
  bcdDevice            3.72
  iManufacturer           0 
  iProduct                0 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           39
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
      bNumEndpoints           3
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
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
        bEndpointAddress     0x81  EP 1 IN
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
Device Status:     0x0000
  (Bus Powered)

There it is, but I can't seem to get fprint to see it as a device in fprint_demo.

---

### Post by 29732 on 2010-06-04
fprint couldnt find it either for me](*,)

---

### Post by Akhnatoun on 2010-09-02
I' ve the same problem too.

I used Fingerprint-GUI to figure out my fingerprint reader, but it is giving me "No Device found", though it's listing under the "Attached USB Devices" tab :

DigitalPersona, Inc (0X138a) Fingerprint Reader (0X1).

I've contacted HP Support to be sure from my fingerprint reader vendor, but they have no useful information.

---

### Post by Kixtosh on 2010-09-22
Check the output of the lsusb command (in Terminal) against this list of supported devices. Ignore the brand of laptop in the first column, check only against the columns headed **USB Vendor ID** and **USB Product ID**:

[http://reactivated.net/fprint/wiki/Supported_devices](http://reactivated.net/fprint/wiki/Supported_devices)
[https://launchpad.net/~fingerprint/+archive/fprint](https://launchpad.net/~fingerprint/+archive/fprint)

Vendor 138a and Product 0001 do not seem to be on that list at the time of writing.

---

