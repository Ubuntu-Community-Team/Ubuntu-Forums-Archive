---
title: "Synce to connect Smartphone: kernel modules not present?"
date: 2007-08-08
forum: Hardware &amp; Laptops
---

### Post by wild_oscar on 2007-08-08
Hi there,

I am trying to connect my HTC P3600 smartphone to ubuntu, so I can finally use it the same way I used it with the great Microsoft Outlook. Until now it has been quite frustrating.

I have been following these instructions:

[http://www.synce.org/index.php/Connecting_your_Windows_Mobile_2005_device_via_USB_(usb-rndis-lite)]("http://www.synce.org/index.php/Connecting_your_Windows_Mobile_2005_device_via_USB_(usb-rndis-lite)")

Namely, in this section I get stuck here:

```
cd usb-rndis-lite/
make
sudo ./clean.sh
sudo make install
```

Running the ./clean.sh script returns:

```
make -C /lib/modules/2.6.20-16-generic/build SUBDIRS=/home/miguel/synce/synce-usb-mdis-lite/usb-rndis-lite modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  Building modules, stage 2.
  MODPOST 3 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
ERROR: Module rndis_host does not exist in /proc/modules
ERROR: Module cdc_ether does not exist in /proc/modules
ERROR: Module usbnet does not exist in /proc/modules

```

I have no experience with kernel modules whatsoever. I read in the instructions this

> Then there a couple of things to try. First of all, make sure your kernel is configured with the CONFIG_USB_NET_RNDIS_HOST or CONFIG_USB_NET_RNDIS_HOST_MODULE option. Without this, the driver will be built without ActiveSync support. 

The module can be found in: 
Device Drivers
 > USB Support
  > USB Network Adapters
   > Multipurpose USB Networking Framework
    > Host for RNDIS Devices

But I have no idea what they're talking about. Can anyone help me?

---

