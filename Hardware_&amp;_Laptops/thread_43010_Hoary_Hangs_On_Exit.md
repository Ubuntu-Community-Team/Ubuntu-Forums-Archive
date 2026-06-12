---
title: "Hoary Hangs On Exit"
date: 2005-06-20
forum: Hardware &amp; Laptops
---

### Post by shardy1216 on 2005-06-20
I have a broadcom 802.11g wireless card in my laptop configured using ndiswrapper, works fine with the exception that when shutting the laptop down it hangs with the following message:

unregister_netdevice: waiting for wlan0 to become free.  Usage count = 1.  This repeats over and over.  I can manually fix it by issuing an ifdwon wlan0 command prior to rebooting, but I was curious if anyone out there had this problem and knows how to fix it.

---

