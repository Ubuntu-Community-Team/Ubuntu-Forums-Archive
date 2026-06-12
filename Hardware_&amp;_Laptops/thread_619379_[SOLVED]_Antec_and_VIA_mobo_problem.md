---
title: "[SOLVED] Antec and VIA mobo problem"
date: 2007-11-21
forum: Hardware &amp; Laptops
---

### Post by gobbles414 on 2007-11-21
Hi all,

I have built a computer using a [VIA pc3500 motherboard]("http://www.via.com.tw/en/initiatives/empowered/pc3500_mainboard/index.jsp") and an [Antec Sonata III tower]("http://www.antec.com/us/productDetails.php?ProdID=15137") for my job. Everything seems to be working fine, except the front USB ports on the tower. I have already search for BIOS and driver updates, without success.

I have run the *lsusb* command, and 8 USB 2.0 ports are reported. Although the motherboard is able to support as many as 8 connections, there are only 6 in the system that I have built (2 front and 4 back). The Sonata III has a front SATA port as well. When I disconnect the front SATA port from the motherboard, only 7 USB 2.0 ports are reported by *lsusb*. I have an internal SATA hard drive. Could that account for the remaining extra USB 2.0 port being reported? The computer is currently a dual-boot system, with Windows Vista installed (yuck). Anyway, the front USB 2.0 ports are behaving strangely in Vista as well. Devices that I know for sure are USB 2.0 are being reported as USB 1.x. Vista gives me the standard "your device would work better if connected to a high-speed USB port..."

FYI, my understanding is that the system which I have built is somewhat similar to the [gPCs being sold at Wal-Mart stores]("http://www.walmart.com/catalog/product.do?product_id=7754614").

Thanks in advance for your help!

---

### Post by dabl on 2007-11-21
It says here that mobo has 4 USB ports and 2 SATA connectors:

[http://www.via.com.tw/en/initiatives/empowered/pc3500_mainboard/index.jsp](http://www.via.com.tw/en/initiatives/empowered/pc3500_mainboard/index.jsp)

Sometimes folks confuse "ports" and "connectors", and this product description is less than crystal clear on that point. A "port" is usually a _logical_ element in a bus design, while a _connector_ is a physical interface module.  Most often the relationship is 1:1 between ports and connectors, but sometimes it is not, i.e. the IDE channel can have 2 connectors for 1 port, and a SCSI port can serve 7 connected devices.

Anyway, I'm not sure what is going on with your board, but I wouldn't expect more than 4 USB ports to work. :)

---

### Post by gobbles414 on 2007-11-21
Hi dabl,

Thanks for your reply. I forgot to mention that I've installed Ubuntu 7.10 (GNOME) from the standard x86 CD. About the ports versus connectors issue, let's use the wording provided by VIA if you don't mind -- just for the sake of clarity. The pc3500 has 4 USB 2.0 ports on the back panel. On the motherboard, there are 2 SATA connectors. There are also 2 USB 2.0 connectors on the motherboard. Using these additional USB 2.0 connectors, it should be possible to connect as many as 4 additional USB 2.0 ports to the system.

I should give some more details about my problem. Basically, the response of the front USB 2.0 ports depends upon the device that I'm trying to connect. For example, when I connect my USB 2.0 flash drive, nothing happens and the drive is not reported by *lsusb*. If I try to connect my digital camera to the front ports, it is detected by *lsusb*. But Ubuntu goes crazy! It will show a dialog mentioning that pictures have been detected. Then the dialog will go away, then come back again. All of this happens in the space of a couple of seconds and continues until I unplug the camera from the front port. My USB 2.0 media card reader with a CF card in it mounts most of the time, but not always.

Thanks again everyone.

---

### Post by gobbles414 on 2007-11-22
Does anyone have additional ideas about my computer's USB problem?

---

### Post by gobbles414 on 2007-11-24
bump (please help...)

---

### Post by gobbles414 on 2007-12-05
Hi all,

This problem has been 99% fixed by switching from the Sonata III computer tower to a [GIGABYTE GZ-X1]("http://www.compusa.com/products/product_info.asp?pfp=BROWSE&N=200088+403742&Ne=400000&product_code=342255") tower. I am now able to get all of my USB and USB 2.0 devices to reliably, using the second of two USB connectors on the pc3500 motherboard. The first connector on the motherboard is still preforming unreliably. I'll leave this thread marked unsolved for a few more days, just in case someone else would like to post a helpful comment.

---

