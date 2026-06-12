---
title: "Boardcom 4328 (Dell Draft N Internal Wireless) with Linux?"
date: 2006-09-13
forum: Hardware &amp; Laptops
---

### Post by arthur_kalm on 2006-09-13
Hi everyone, I'm thinking about getting an Dell Inspiron 6400. The problem is that they just changed the internal wireless card from Intel to Broadcom 4328. I have two choices for wireless:

- Dell Wireless 1390 802.11g Mini Card (54Mbps) (this is included)
- Dell Draft N Internal Wireless (extra $50)

I Googled around and searched these forums and haven't really found anything about the internal chip working with Linux. Has anyone had experience with it? Does it work with Linux? Which card should I get?

Thank you for your help.

P.S. I need to know soon (tomorrow) because the deal ends then. Thanks!

---

### Post by trubblemaker on 2006-09-14
Here's some info on the earlier chip and I also want you to know the ndiswrapper runs the windows driver and that is one of the options in my signature. Hope this helps you out. also there is a website that lets you know the all the drivers that are natively supported [http://bcm43xx.berlios.de/](http://bcm43xx.berlios.de/) hope this help you.

---

### Post by mbobak on 2006-12-20
I have the 4328 in my Ferrari 1000 laptop.  I have it working great w/ ndiswrapper and the *right* version of the driver.
Use this driver:
[http://www.box.net/public/9ru8h47pdd](http://www.box.net/public/9ru8h47pdd)

Do yourself a favor, don't bother with other versions of the driver.  I struggled and wasted a lot of time till I found a pointer to this driver.

-Mark

---

### Post by grogger13 on 2007-02-22
okay, i got this working, but i think it will only do g, and i cant get network manager to see it

---

