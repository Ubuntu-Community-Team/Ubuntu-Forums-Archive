---
title: "No Wireless using DELL laptop"
date: 2010-11-10
forum: Hardware
---

### Post by Luper1970 on 2010-11-10
Hi, Folks,
 
I bought a DELL Inspiron 14 laptop, with Windows 7, and everything is working well.
 
I decided to make an Ubuntu 10.10 (Maverick Meerkat) wubi installation, but wireless simply doesn't work at all. No connections are listed and I only see a "!" sign over the wireless icon.
 
It's using a WLAN mini board DW1501 Wireless-N and an Atheros AR8152-E Fast Ethernet Controller (NDIS 6.20)
 
I really appreciate any help.
 
Thanks
Luiz

---

### Post by TBABill on 2010-11-10
That's a Broadcom card, which requires a Broadcom proprietary driver. I'm not sure about it via Wubi since I never use Wubi, but in a normal install of Ubuntu to its own partition you have to connect via ethernet, then go to System>Administration>Hardware (this is a bit different in 10.10, but it is obvious in the menu) and let the system look for available drivers, then install the one you want.

---

### Post by Luper1970 on 2010-11-10
Hi,
 
I have already plugged the cable and the Internet connection doesn't work as well.
 
Any other tip?
 
Thanks
Luiz

---

