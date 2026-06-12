---
title: "Hard drive I/O error"
date: 2009-05-01
forum: Hardware
---

### Post by furialis on 2009-05-01
I recently purchased two [OCZ Vertex SSD drives]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820227393") and cannot get Ubuntu to install. Windows will install fine.

I've been in contact with my [motherboard's]("http://www.gigabyte.us/Products/Motherboard/Products_Overview.aspx?ProductID=2932") manufacturer, who have the drives in question. They ran some tests, we went back an forth and this was the last post:

*Due to no drivers available on the OS it will not be able to boot and will attempt to access for the driver. It should not be any issue under Native IDE mode, but not raid until they release an newer release of the OS with build in drivers.*

The problem is I have been running in Native IDE mode and the drive still isn't recognized. These are some recommended tests from the OCZ forum:


sudo hdparm -I
/dev/sda:
HDIO_DRIVE_CMD(identify) failed: Input/output error

sudo hdparm --security-set-pass NULL /dev/sda
security_password=""

/dev/sda:
Issuing SECURITY_SET_PASS command, password="", user=master, mode=high
SECURITY_SET_PASS: Inappropriate ioctl for device

How would I go about determining the necessary drivers and integrating them into a live CD?

---

