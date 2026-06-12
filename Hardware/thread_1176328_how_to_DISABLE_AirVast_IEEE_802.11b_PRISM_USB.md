---
title: "how to DISABLE AirVast IEEE 802.11b PRISM USB ?"
date: 2009-06-02
forum: Hardware
---

### Post by deciofabio on 2009-06-02
Dear All,
I am a newbie in Ubuntu. I installed it on my old notebook, running a cirix processor ;)
It detected my internal USB wireless device -- fine. It's an old AirVast IEEE 802.11b PRISM USB device. Running ok but sudenly after a while (used to be 30 minutes) -- zapt! it freeze the internet connection and ultimately the system itself.
I installed also a D-link systems wireless G DWA-110 USB device in paralele, and i solved sometimes the problem of connection, but the system freeze anyway after a while. 
the command 

lsusb -v | less

displayed:

	 	 Bus 004 Device 002: ID 124a:168b AirVast  Device Descriptor:   bLength                18   bDescriptorType         1   bcdUSB               1.10   bDeviceClass            0 (Defined at Interface level)   bDeviceSubClass         0    bDeviceProtocol         0    bMaxPacketSize0         8   idVendor           0x124a AirVast   idProduct          0x168b    bcdDevice            1.32   iManufacturer           1 AirVast Taiwan   iProduct                2 IEEE 802.11b PRISM3 USB   iSerial                 0    bNumConfigurations      1   Configuration Descriptor:     bLength                 9     bDescriptorType         2     wTotalLength           39     bNumInterfaces          1     bConfigurationValue     1     iConfiguration          0      bmAttributes         0x80       (Bus Powered)     MaxPower              500mA     Interface Descriptor:       bLength                 9       bDescriptorType         4       bInterfaceNumber        0       bAlternateSetting       0       bNumEndpoints           3       bInterfaceClass       255 Vendor Specific Class       bInterfaceSubClass    255 Vendor Specific Subclass : Question: how to DISABLE such device?

Thanks
Decio

---

### Post by lubod on 2009-07-02
I hope you sorted out this some other way, since no one seems to have replied to you, but if you didn't:


you will need to blacklist the driver module so that it won't load at boot. 

Do an lsmod to identify the driver (prism or prism3 perhaps) and then type its name in the /etc/modprobe.d/blacklist.conf file. This last edit has to be done with sudo or root priviledges:

> gksu gedit /etc/modprobe.d/blacklist.conf
anything with # at the beginning is a human readable comment, the computer ignores this line
it reads the lines that say blacklist followed by driver name, so you'd add (for example):

> blacklist prism

HTH :grin:

The basic idea was borrowed from this:
[http://ubuntuforums.org/showthread.php?p=7518086](http://ubuntuforums.org/showthread.php?p=7518086)

---

