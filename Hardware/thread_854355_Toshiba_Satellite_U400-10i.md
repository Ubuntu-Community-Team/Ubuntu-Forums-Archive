---
title: "Toshiba Satellite U400-10i"
date: 2008-07-09
forum: Hardware
---

### Post by alebu on 2008-07-09
First of all, some introduction to that notebook. It has text on it  'MADE FOR EMERGING EMEA REGION'. There is no description for it on official website, I only found description on europe website ([http://eu.computers.toshiba-europe.com/cgi-bin/ToshibaCSG/jsp/productPage.do?service=EU&PRODUCT_ID=151251](http://eu.computers.toshiba-europe.com/cgi-bin/ToshibaCSG/jsp/productPage.do?service=EU&PRODUCT_ID=151251)).

After instaltion of ubuntu 8.04.1 there is no LAN or Wareless (Maybe I miss something about configuring Wareless).

Result of lspci and lshw are attached...

---

### Post by stchman on 2008-07-09
> **alebu said:**
> First of all, some introduction to that notebook. It has text on it  'MADE FOR EMERGING EMEA REGION'. There is no description for it on official website, I only found description on europe website ([http://eu.computers.toshiba-europe.com/cgi-bin/ToshibaCSG/jsp/productPage.do?service=EU&PRODUCT_ID=151251](http://eu.computers.toshiba-europe.com/cgi-bin/ToshibaCSG/jsp/productPage.do?service=EU&PRODUCT_ID=151251)).

After instaltion of ubuntu 8.04.1 there is no LAN or Wareless (Maybe I miss something about configuring Wareless).

Result of lspci and lshw are attached...

That laptop has a newer Marvell ethernet which will need drivers.

I cannot see any wireless adapter in the lspci.

---

### Post by rocktorrentz on 2008-07-10
I've been looking at this laptop. If needing to use ndiswrapper to use the wireless is the only issue I might go for it :D [Ndiswrapper guide](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by alebu on 2009-01-20
Ubuntu 8.10 - everything works perfect! Congrats to ubuntu and all Linux developers.

---

