---
title: "External Hard Drive Not Recognized"
date: 2008-07-27
forum: Hardware
---

### Post by kanak123 on 2008-07-27
Hi,

I recently upgraded my laptop's hard drive, and am planning to use the older one as an external drive. My old hard drive is a 120 GB [Western Digital WD1200BEVS]("http://www.wdc.com/en/products/products.asp?driveid=200&language=en"), and the enclosure is [Vantec Nexstar 3]("http://www.newegg.com/Product/Product.aspx?Item=N82E16817392016"). The hard drive has been formatted to ext3.

When I connect the external to my computer, the enclosure's LED lights up, and if i listen really closely, I can hear the hard drive spinning. However, Ubuntu doesn't recognize the hard drive (no icon in the desktop, fdisk -l gives the following result:

> 
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c008c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         122      979933+  82  Linux swap / Solaris
/dev/sda2   *         123        1095     7815622+  83  Linux
/dev/sda3            1096       38913   303773085   83  Linux


I know the hard drive isn't the problem because I was able to use it just fine when I put it back in the laptop.

Is there anything I can do to get it to work?

Thank you.


PS: I'm running Ubuntu 8.041 with the latest updates. My computer is a dell e1505 with Core 2 Duo, 2 GB ram, 320 GB SATA hard drive, ATI X1400 and Intel Wireless.

---

### Post by Yuki_Nagato on 2008-07-27
Are you connecting the hard drive to the computer through the SATA connectors?  Or have you got some sort of converter that runs it through the USB?

You will probably have to:

```
mount -t ext3 -o rw /dev/whatever /mnt/custom_point
```

---

### Post by kanak123 on 2008-07-27
Hi, thank you for your reply. To clarify:

> **Yuki_Nagato said:**
> Are you connecting the hard drive to the computer through the SATA connectors? 

I'm trying to get it to work with the enclosure mentioned in the first post (I've only tried connecting it with USB since my laptop does not have an eSATA). I confirmed that the hard drive is working by replacing my current laptop hard drive with it.

> **Yuki_Nagato said:**
> 
```
mount -t ext3 -o rw /dev/whatever /mnt/custom_point
```

How do I find out what the device name is (in /dev/)?

---

### Post by jocampo on 2009-04-23
Hi Kanak

this is an old thread... but I would like to know if you fixed this issues for good. Planning to buy same enclosure for my PC, which is running Ubuntu Hardy

---

