---
title: "USB  hard drive not detected, data recovery possible?"
date: 2009-12-15
forum: Hardware
---

### Post by svaucher on 2009-12-15
I assume that there is nothing to do and that my hd is dead, but I thought I'd see if anyone has any interesting information.

I have an external usb hd normally pluged into my router running linux, but that I use to perform backups for my work computers running 9.10. There was a power failure recently and the hd is not detected anymore, not by my router, not by my 9.10 notebook. When I plug it it, it does not seem to be detected. Neither, dmesg, nor df indicate that it is detected. I also tested/tried 2 different usb cables. Both work.

Any hints for data recovery? I looked at testdisk, but it does not detect the usb hd.

---

### Post by PRC09 on 2009-12-15
What model Usb drive? The reason I ask is if its inside an enclosure the last one I took apart was a SATA drive plugged into a USB interface connection.Maybe that is what took the power shot and not the drive itself....

---

### Post by svaucher on 2009-12-15
Yups, it's a SATA. I suspect you might be right. The hd spins, but it is not detected. It might be the usb connection that died...

It is an iomega on the outside. In the past, I tried to see what my router thought it was:

$ cat /proc/scsi/usb-storage-0/0
Host scsi0: usb-storage
Vendor: JMicron
Product: USB to ATA/ATAPI Bridge
Serial Number: 92306FFFFFFF
Protocol: Transparent SCSI
Transport: Bulk
GUID: 059b0475000092306fffffff
Attached: Yes
Port: 2
Bus: 01:03.2-2

In any case, it is under warrantee, and IOmega will send me a replacement. When I get it, I'll open up my old one and see if I can recuperate the hd/data by replacing the usb connection. I don't like using "problem" hds, but it could become my 2nd backup.

---

### Post by PRC09 on 2009-12-15
If you have another computer(desktop) that has a SATA connector you should be able to purchase the proper cables to connect and see if it will recognize the drive and recover your data that way....

---

### Post by PRC09 on 2009-12-15
If the drive is recognized and you get it working that way you could always use it again with something like this...

[http://www.tigerdirect.ca/applications/SearchTools/item-details.asp?EdpNo=3195233&Sku=M501-1031](http://www.tigerdirect.ca/applications/SearchTools/item-details.asp?EdpNo=3195233&Sku=M501-1031)

---

### Post by svaucher on 2009-12-15
Thanks for the link, I was already starting to look at connectors. I might get one that support different types of hds to reuse both my old laptop/desktop drives.

---

