---
title: "Hardware Support RTL 8187b"
date: 2008-02-01
forum: Hardware &amp; Laptops
---

### Post by ammuro_rei on 2008-02-01
I am trying to configure my RTL8187b wireless card on Ubuntu 7.10 with Ndiswrapper.  Everything seems to install fine, and the drivers appear to load into ndiswrapper, but the hardware itself is not recognized.  i.e. upon "ndiswrapper -l" I get "Drivers installed" but no card ID.  Similarily, iwconfig and lsusb show no card.  Can I force Ubuntu to rescan my hardware, or force it to recognize the card?  I am using a Toshiba Satellite L45.  
Any help would be much appreciated.  Thanks!

---

### Post by HandyAndyShortStack on 2008-02-25
have a look at [this]("http://www.datanorth.net/%7Ecuervo/rtl8187b/")

---

### Post by Tom--d on 2008-02-26
> **HandyAndyShortStack said:**
> have a look at [this]("http://www.datanorth.net/%7Ecuervo/rtl8187b/")


The modified version is way to buggy for me and also I need WEP. WEP doesn't work for me wth the modified driver.

I've got the RTL8187B ID:0bda:8179 card. I modifed the Win98 .inf file. It now says my hardware is present BUT no wireless is working!

Does anyone know how to modife the Win98 driver so it runs the wireless in my laptop. I'm very very close to getting it done!!

Very close.

So please help me :)

Thanks!!!

---

