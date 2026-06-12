---
title: "Laptop Problems With Ubuntu"
date: 2006-04-13
forum: Hardware &amp; Laptops
---

### Post by BlackMagic on 2006-04-13
Dear Members,

Short time ago, i recieved my new laptop. It's an Jewel Saffier 3500. Now i don't want to install Windows crap on it. So i decided to choose for ubuntu/kubuntu. When the install whas finalized, the system needs to reboot. And then everything goes wrong, by loading the hot plug system Kubuntu stops booting!

I've tryed some things like ctrl+c before hot plug is booting. Then the systems starts but my network isn't working.

Network Card Spc are:

eth0: Intel Corp. PRO/Wireless 2200BG
eth1: Realtek Semiconductor cCo. Ltd. RTL-8169 Gigabit Ethernet


Sombody had the same problem, or know how it cvan be solved?

Thanks in Advance!

Greetz,

Danny a.k.a BlackMagic

---

### Post by Derek Djons on 2006-04-13
I do have the same wireless network adapter as you (Intel 2200BG). So that shouldn't be the problem. Also the other network card shouldn't be a problem.

During installation Ubuntu asks you several questions about your adapter and settings. When these setting are filled in wrong or Ubuntu can't connect then there is a possibility that Ubuntu either hangs during BOOT or you can't connect after BOOT is complete and you have logged in.

I don't know which adapter you use by default. But if you use the Intel 2200BG the questions during install you will get could be similar to this:

- Which adapter should be used by default
(nothing difficult about it, choose your default adapter).

- Fill in the ESSID
(This is the name that your modem/router is transmitting).

- Fill in the WEP (if you got it enabled)
(Fill in your WEP, note that Ubuntu by default doesn't supports WPA).

- Ubuntu will try and connect
(If that fails there could be several reasons to choose from. You don't work with DHCP, Ubuntu has problems with you modem/router or maybe a setting forgotten to change in the modem / router).

I've experienced several issues when skipping the internet configuration and trying to configure it later on. After filling all data into the manager it still simply wouldn't connect. So my advise is... reinstall Ubuntu and check your modem / router settings.

---

