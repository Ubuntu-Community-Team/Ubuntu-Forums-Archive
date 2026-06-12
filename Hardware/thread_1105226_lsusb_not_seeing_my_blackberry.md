---
title: "lsusb not seeing my blackberry"
date: 2009-03-24
forum: Hardware
---

### Post by grapnell on 2009-03-24
I am trying to start using the barry tools on my ubuntu 8.10 pc for my bb 8330. However, I can't get lusb to even recognize my BB. I have seen a few others with this problem, but no solutions. Has anyone found a solution to this? Why wouldn't ubuntu at least show something related to the BB when I plug it in and type lsusb?

I'll provide any info upon request.

gm

---

### Post by cariboo on 2009-03-24
It isn't linux's fault that there aren't any drivers for your device. Check with the manufacturer for a solution.

Jim

---

### Post by grapnell on 2009-03-25
Jim, thanks for the input, but I was in a rush, and was probably not clear enough.  This isn't a driver issue, this a usb issue, and this only happens under ubuntu, and a few other distros.  The problem is that the usb subsystem is not recognizing that the device is even plugged in.  Under fedora, if I plug the device in and type 'lsusb -v' i get:

```

Bus 003 Device 003: ID 0fca:0004 Research In Motion, Ltd. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        16
  idVendor           0x0fca Research In Motion, Ltd.
  idProduct          0x0004 
  bcdDevice            1.06
  iManufacturer           1 Research In Motion
  iProduct                5 RIM Composite Device
  iSerial                 3 XXXXPRIVATEXXXX
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           97
    bNumInterfaces          2
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
    MaxPower              500mA

(lots and lots more, snipped for brevity)

```

but under ubuntu, i get nothing.  Unless the usb subsystem will recognize that the device is plugged in, I can't even begin to think about drivers.  If anyone else has had this problem under ubuntu, and has found a solution, please let me know.

Thanks,
gm

---

### Post by grapnell on 2009-03-25
bump??

---

### Post by wbryan6 on 2009-04-01
I am having the same issue.  When I run lsusb, the only results I get are:

Bus 001 Device 002: ID 045e:00e1 Microsoft Corp. Wireless Laser Mouse 6000 Reciever
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

I am attempting to connect a Blackberry 8700.  Running bcharge/barry_charge does not change anything.  Any help would be greatly appreciated.

---

### Post by wbryan6 on 2009-04-01
D'oh.  Sorry, my usb cable was loose.  Disconnect/reconnect and everything showed up in lsusb.  I hate getting rude, obvious replies to questions, but have you check this usb cable out on another device?  Either way, good luck.

---

### Post by sengiv on 2010-09-28
Hey guys! I'm new to this...
I'm experiencing a similar problem (i.e.)when multiple devices connected to my USB port. 
#lsusb
This command doesn't list the name of the composite device attached.Pls help me in this.

when using -v, the product ID is blanc*

**Wats wrong with this**

---

