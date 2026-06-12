---
title: "Ubuntu not working with Acer Laptop since 11.10 and 12.04 Beta Wireless laptop"
date: 2012-03-12
forum: Hardware
---

### Post by wacky_sung on 2012-03-12
I have been a big fan of Ubuntu through the years but lately with the version 11.10 and 12.04 my acer laptop wireless does not seem to be working anymore.For those face the same issue as me, you can follow the [link]("http://www.computerandyou.net/2011/05/how-to-solve-no-wireless-networks-in-ubuntu-11-04/") before to help me to resolve it.

Hopefully this is helpful to some people out there one way or another.

---

### Post by TBABill on 2012-03-12
It may be beneficial to change the title of the thread from Acer-related to BCM4311 related. The problem is not the type of machine, but rather how Ubuntu sets up the driver for any machine with a BCM4311. If memory serves me correctly, the problem with the STA driver is a conflict where the install routine enables more than one driver and it may be possible to blacklist the conflicting module and keep the wl module active rather than changing to the b43 or getting the STA driver right from Broadcom.
 
Just a thought, but I could be wrong on the actual cause. Good info on a fix and/or workaround on the blog site!

---

