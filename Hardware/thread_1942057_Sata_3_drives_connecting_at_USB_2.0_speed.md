---
title: "Sata 3 drives connecting at USB 2.0 speed"
date: 2012-03-16
forum: Hardware
---

### Post by magnim on 2012-03-16
Installed Ubuntu 11.10 a few days ago.  

I have a Startech USB 3.0 pci express card in system, and two WD SATA drives installed in a Thermaltake BlacX USB 3.0 superspeed dual drive dock.  Storage Device Manager reports that the drives are connected at 480 MB/s (USB 2.0 speed)

Is there any way to get these drives connected at USB 3.0 speed?

---

### Post by magnim on 2012-03-18
ran lsusb -v and it looks like the USB 3.0 card is properly detected, and I 'believe' this is the USB 3.0 drive dock - which isn't being picked up as USB 3.0:
```

Bus 007 Device 002: ID 152d:0551 JMicron Technology Corp. / JMicron USA Technology Corp. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x152d JMicron Technology Corp. / JMicron USA Technology Corp.
  idProduct          0x0551 
  bcdDevice            1.00
  iManufacturer           1 JMicron
  iProduct                2 USB to ATA/ATAPI Bridge
...

```

I found [this post]("http://ubuntuforums.org/showthread.php?t=1642641") - where it sounds like the same issue was encountered, and apparently solved - does Ubuntu 11.10 use an older kernel than was referenced in the above post?

---

