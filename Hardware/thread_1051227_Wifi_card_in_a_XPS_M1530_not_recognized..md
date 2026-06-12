---
title: "Wifi card in a XPS M1530 not recognized."
date: 2009-01-26
forum: Hardware
---

### Post by CodyK46 on 2009-01-26
I tried the live-cd this past weekend. The Wifi card isn't recognized by Ubuntu. I haven't hooked it up to a wired network yet. So how would I go about getting a driver for my XPS?

---

### Post by jespdj on 2009-01-26
Which WiFi card do you have in your M1530? I have the Intel 4965 and it works out-of-the-box.

Some people have reported problems with the Intel 3945, and the Dell-brand WiFi card is also difficult to get working, because it uses a Broadcomm chipset - and Broadcomm is unfortunately one of those notorious companies that refuse to support Linux in any way. If you have the Dell-brand WiFi card, you might get it working by using the Windows driver for the card and [ndiswrapper](http://en.wikipedia.org/wiki/NdisWrapper), which is a piece of software that will enable you to use Windows network drivers on Linux.

---

### Post by CodyK46 on 2009-01-26
> **jespdj said:**
> Which WiFi card do you have in your M1530? I have the Intel 4965 and it works out-of-the-box.

Some people have reported problems with the Intel 3945, and the Dell-brand WiFi card is also difficult to get working, because it uses a Broadcomm chipset - and Broadcomm is unfortunately one of those notorious companies that refuse to support Linux in any way. If you have the Dell-brand WiFi card, you might get it working by using the Windows driver for the card and [ndiswrapper](http://en.wikipedia.org/wiki/NdisWrapper), which is a piece of software that will enable you to use Windows network drivers on Linux.

Dell Wireless 1395 WLAN Mini-Card

Manufacture by Broadcom.

---

### Post by CodyK46 on 2009-01-26
Any other suggestions?

---

### Post by CodyK46 on 2009-01-27
I did find the drivers on the Broadcom site and you have to build the driver.

---

