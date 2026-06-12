---
title: "Problems getting Wireless to work with Acer Travelmate 2413"
date: 2006-11-11
forum: Hardware &amp; Laptops
---

### Post by icedcheese on 2006-11-11
Hi

I am having problems getting my wireless internet connection to work with Ubuntu 6.10.  I was wondering if anyone was able to provide some insight on the problem for me.

Firstly, when I go to System -> Administration -> Networking no wireless options are available.  At the moment I am connected through a Wired Network.

I have downloaded the windows driver for my wireless card.  The details are:

Product
Aspire 3610
Related Products
TravelMate 2410
Title
802.11b+g Wireless Driver
Description
Broadcom Wireless 802.11bg v.3.100.46.0 and Foxconn Wireless 802.11bg Atheros v4.0.0.14001
Operating System
Windows XP

I have tried to use ndiswrapper to install the driver, however either I am not doing it correctly or it cannot be done.  When I type the following into the terminal I get the following output.

ndiswrapper -l
Installed ndis drivers:
driver  invalid driver!
neti2220        invalid driver!
setup   invalid driver!

My wireless was working under 6.06 and was picked up automatically.

If anyone can provide any information on this matter it would be hugely appreciated.

Thank you in advance.

Michael

---

### Post by icedcheese on 2006-11-11
I have managed to install my driver successfully, however no hardware is present:

ndiswrapper -l
Installed ndis drivers:
bcmwl5  driver present

---

### Post by icedcheese on 2006-11-12
Managed to fix the problem!  I reinstalled Ubuntu and it worked!

---

### Post by thoman on 2007-01-20
1 quick question?
How do u reinstall ubuntu isit the same like windows..

---

