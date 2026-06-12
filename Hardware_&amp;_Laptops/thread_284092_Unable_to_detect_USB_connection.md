---
title: "Unable to detect USB connection"
date: 2006-10-25
forum: Hardware &amp; Laptops
---

### Post by sohaibma on 2006-10-25
when i connect my USB HDD to my USB port, it shows the following in device manager:
-USB 2.0
--EHCI Host Controller
---USB to IDE Bridge
-----USB Mass Storage interface
-----SCSI Host Adapter
---Usb hub interface, USB raw device access, etc.

lsusb command also reveals the USB HD:
Bus 004 Device 008: ID 058f:6390 Alcor Micro Corp.

the problem is that a drive for the usb hdd does not show up.
therefore i am unable to use the disk,
please help me out here... how do i enable it.

---

### Post by sohaibma on 2006-10-25
please, i am in need of quick help.
someone please help me out here.

---

### Post by stanley82 on 2007-07-02
Hi,
     I have the similar problem.  System hardware info gives me similar results showing that my IDE drive is detected as USB 1.1.  My flash works fine and instantly pops up on my desktop.  I think that the problem is that USB drives are considered as SCSI and meshing IDE as a SCSI over USB does not hack.  IDE is native to winxx and SCSI is native to UNIX Linux type systems.  Any of you guys out there in Ubintu land have any ideas?

                           Regards Ian.

---

