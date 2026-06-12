---
title: "SATA Port Multiplers"
date: 2006-10-17
forum: Hardware &amp; Laptops
---

### Post by viking325i on 2006-10-17
Hi, has anyone tried using a SATA port multiplier under ubuntu? if so with what sucess?

[http://www.addonics.com/products/host_controller/ad5sapm-e.asp](http://www.addonics.com/products/host_controller/ad5sapm-e.asp)

---

### Post by trmentry on 2007-10-27
Same question.  I found that they say its in 6.06.

[http://www.addonics.com/support/faqs/faq-pmsupport.asp](http://www.addonics.com/support/faqs/faq-pmsupport.asp)

But is it in versions after that.  Specifically the new 7.10. :)  Is there a way to find out?

Thanks

---

### Post by trmentry on 2007-10-27
I found this in an  lsmod  on 7.10 64b server

Are these the patches for port multipliers?

libata                146096  2 ata_piix,ata_generic

---

### Post by Rizlaw on 2007-10-27
> **viking325i said:**
> Hi, has anyone tried using a SATA port multiplier under ubuntu? if so with what sucess?

[http://www.addonics.com/products/host_controller/ad5sapm-e.asp](http://www.addonics.com/products/host_controller/ad5sapm-e.asp)

I have the Addonics ADSA3GPX1-2E controller and the port multiplier installed on Ubuntu 7.10 (Gutsy) and I can tell you that the PCIx controller card is recognized and it sort of works, but only sees the first SATA drive in my 5 drive array. My guess is that the linux kernel has no hardware support for the "port multiplier". The remaining 4 sata drives are not recognized.  The Addonics website does list instructions on how to get things working in Ubuntu Dapper, but the instructions are not simple and require recompiling the kernel. I have been after them to update the linux software for newer versions of Ubuntu and to make it easier to install, but so far, they haven't done it. I think a .deb package that does everything automatically is what's needed.

My solution, for the time being, was to order (from Addonics) an eSATA to USB 2.0 converter (part #: AAU2ESA). Addonics link: [http://www.addonics.com/products/io/aau2esa.asp](http://www.addonics.com/products/io/aau2esa.asp)

The converter works with the original Addonics port multiplier and the newer hardware port multiplier. Simply, connect your external port multiplier enabled hard drive box with an eSATA to eSATA cable to the converter, and then plug the other end of the converter into an open USB2 port on your computer. Ubuntu 7.04 and 7.10 will immediately see and mount all 5 sata drives.

The downside is slower file transfers and (I think) lack of RAID functionality. I don't use RAID so I'm not sure about that, but you will get to see and use 5 independent drives.

Hope this helps.

---

