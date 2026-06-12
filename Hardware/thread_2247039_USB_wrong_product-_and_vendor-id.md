---
title: "USB: wrong product- and vendor-id ?"
date: 2014-10-05
forum: Hardware
---

### Post by rumpumpel1 on 2014-10-05
Hi,

I have an EasyCAP Video grabber (USB).
Windows tells me: Vendor-id = 1B71 and product-id = 3002, which is correct.
Linux tells me :  idVendor=1f71, idProduct=3301 which is wrong.

Is there any explanation for this ?

---

### Post by Vladlenin5000 on 2014-10-05
Please post the results of *lsusb* with the device connected.

---

### Post by rumpumpel1 on 2014-10-05
Bus 001 Device 011: ID 1f71:3301  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x1f71 
  idProduct          0x3301 
  bcdDevice            1.00
  iManufacturer           3 Gadmei
  iProduct                4 USB TV Box
  iSerial                 2 330000000009
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           83
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA

---

### Post by Vladlenin5000 on 2014-10-05
That isn't the output of *lsusb* but thank you for posting the detailed info anyway. The purpose of the request was to get a full picture of the USB devices detected by the OS.
When posting results please use CODE tags. Easy way: Select "Go Advanced", click the "#" button and paste inside it.

---

### Post by rumpumpel1 on 2014-10-05
```
Bus 001 Device 002: ID 0424:9514 Standard Microsystems Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0424:ec00 Standard Microsystems Corp. 
Bus 001 Device 004: ID 7392:7811 Edimax Technology Co., Ltd EW-7811Un 802.11n Wireless Adapter [Realtek RTL8188CUS]
Bus 001 Device 005: ID 1f71:3301  

```

---

### Post by Vladlenin5000 on 2014-10-05
```
Bus 001 Device 005: ID 1f71:3301
```

So here it is and without any human readable info.
You definitely have a problem there and I'm afraid it won't be easy.
Hopefully some expert will see this and comment about possible solutions. At the moment, I have no idea.

---

