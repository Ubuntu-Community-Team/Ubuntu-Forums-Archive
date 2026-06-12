---
title: "About adding a 2nd NIC"
date: 2012-08-05
forum: Hardware
---

### Post by satimis on 2012-08-05
Hi all,

I have an onboard 1G NIC but need 2 NICs for testing Cloud.  

I found following economic NIC
TP-Link TG-3468 PCI-Express Gigabit Network Card
[http://www.microbarn.com/details.aspx?rid=102333](http://www.microbarn.com/details.aspx?rid=102333)

Is there any problem making it work on Linux (Ubuntu 12.04/Debian 6/Fedora 17 etc)?  

TIA

B.R.
satimis

---

### Post by ahallubuntu on 2012-08-05
That NIC uses the Realtek RTL8168B chipset.  Go ahead and google for "RTL8168B Ubuntu."  A lot of people as recent as 11.10 complained about slow performance with that chipset.  Perhaps things have improved with the kernel in 12.04 LTS?

---

### Post by satimis on 2012-08-05
> **ahallubuntu said:**
> That NIC uses the Realtek RTL8168B chipset.  Go ahead and google for "RTL8168B Ubuntu."  A lot of people as recent as 11.10 complained about slow performance with that chipset.  Perhaps things have improved with the kernel in 12.04 LTS?

Yes, there is a problem on the driver.

Ubuntu 11.10 / 12.04 & Realtek network card RTL8111/RTL8168B driver installation
[http://mschoofs.blogspot.hk/2012/07/ubuntu-1110-1204-realtek-network-card.html](http://mschoofs.blogspot.hk/2012/07/ubuntu-1110-1204-realtek-network-card.html)

Quick Resolution – slow network using RTL8111/RTL8168B in Ubuntu 10.04 LTS
[http://kbflow.wordpress.com/2012/02/02/quick-resolution-slow-network-using-rtl8111rtl8168b-in-ubuntu-10-04-lts/](http://kbflow.wordpress.com/2012/02/02/quick-resolution-slow-network-using-rtl8111rtl8168b-in-ubuntu-10-04-lts/)

Intel NIC card is more expensive.  Up to now I haven't found an economic card with Intel chipset.

B.R.
satimis

---

