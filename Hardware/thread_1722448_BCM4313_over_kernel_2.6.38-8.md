---
title: "BCM4313 over kernel 2.6.38-8"
date: 2011-04-05
forum: Hardware
---

### Post by waabox on 2011-04-05
I made a fix in the Broadcom driver.

Here is the public link when you can download it :)

[http://dl.dropbox.com/u/8518568/BCM4313.tar.bz2](http://dl.dropbox.com/u/8518568/BCM4313.tar.bz2)

the patch is simple, just compare it with the original driver

[http://www.broadcom.com/products/Wireless-LAN/802.11-Wireless-LAN-Solutions/BCM4313](http://www.broadcom.com/products/Wireless-LAN/802.11-Wireless-LAN-Solutions/BCM4313)

Cheers,

Emiliano

---

### Post by GrandTheft on 2011-05-11
What is this fix for? I currently have got a problem that network-manager cant manage the interface. Does the patched source provided here fix THIS problem, or something different, e.g. get the chip to work at all?

thx, best,gt

---

### Post by waabox on 2011-05-30
basically with this fix the ubuntu additional drivers will recognize the network card.

In the stable ubuntu's version (11.4) it's fixed.

But, if the problem persist, let me know.


Regards.

---

### Post by GrandTheft on 2011-05-31
Hi waabox, 

in my case I didnt need any fix or patch. 

The solution was to blacklist acer_wmi module. Then the broadcom module is loaded correctly and everything (wireless, network-manager) works.

gt

---

