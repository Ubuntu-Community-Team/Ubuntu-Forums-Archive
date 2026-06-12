---
title: "question about routers"
date: 2017-10-13
forum: Hardware
---

### Post by jgw on 2017-10-13
I searched for the best router/modems and netgear 1900 c6300bd and arris surfboard came up.  My problem I am with century link and the internet connection is a lan connector.  The descriptions, on both, is that they are cable modems and, I think, these will not work with a lan connection.  Before I spend any money I want to make sure one of these will work (I suspect not).

Thank you...................

---

### Post by oldfred on 2017-10-13
You have cable modems & phone based modems, both output Ethernet and may also be routers & wireless.

I have a separate modem for Comcast and Wireless router for all my connections. Modem was specific as compatible with Comcast (DOCSIS 3.0) Although I saw some info on them updating to DOCSIS 3.1.  

I had Century Link DSL & it was connected to phone line. Max speed was 10Mbps. I upgraded to bonded pair which has two phone lines into modem and speed was then 20Mbps.
Replaced with Hotwire fiber at 100Mbps.

If you have Centurylink probably best to just use their model/wireless router. 
Otherwise router would have to be approved for use with Centurylink.
See list of approved units:
[https://internethelp.centurylink.com/internethelp/mobile/modem-compatibility-table.html](https://internethelp.centurylink.com/internethelp/mobile/modem-compatibility-table.html)

---

### Post by SeijiSensei on 2017-10-13
If you don't have a coaxial cable connection to the Internet, then those routers are not for you.

I recommend this: [https://www.amazon.com/TP-Link-Archer-C7-Wireless-Gigabit/dp/B00BUSDVBQ](https://www.amazon.com/TP-Link-Archer-C7-Wireless-Gigabit/dp/B00BUSDVBQ)

It supports 802.11ac up to 1750 Mbit so it won't be outmoded anytime soon.

I have this router running behind the one supplied by Verizon which uses a coaxial connection.  I connected the "WAN" port on the Archer to one of the "LAN" ports on the Verizon router, then disabled wireless on that device.

---

### Post by flipper8827 on 2017-10-14
You will wan't to stick with the comcast provided modem and configure it in brfidge mode toa reliable netgear or other manufacturers  Wireless access points.

---

### Post by kurt18947 on 2017-10-14
> **oldfred said:**
> 
<snip>

If you have Centurylink probably best to just use their model/wireless router. 
Otherwise router would have to be approved for use with Centurylink.
See list of approved units:
[https://internethelp.centurylink.com/internethelp/mobile/modem-compatibility-table.html](https://internethelp.centurylink.com/internethelp/mobile/modem-compatibility-table.html)

That's how I'd approach it and I did. We have Verizon FiOS so FTTP then coax (moca) from the ONT (Optical Network Terminal). I find MoCA networking really handy plus the channel guide requires it so need to use Verizon's router. I have a Netgear WNDR3700 with DD-WRT which is my primary router. The Verizon supplied router is a glorified modem in essence but everything seems to work. I wanted everything on the same subnet so connected the Verizon router LAN port to the Netgear LAN port. 

The thing I find useful about MoCa networking is that I can have an ethenet switch where ever there's a cable TV outlet. Used Verizon routers can easily be converted to MoCa-ethernet bridges. I jsut have to make sure any coax splitters are capable of a high enough frequency. MoCa is somewhat speed limited but I find it more reliable and probably more secure than WiFi.

---

### Post by jgw on 2017-10-14
Thanks for all the replies!

I am using century link which means I needed a dsl input  (cable uses coax input connection).  Anyway, my question was answered and I appreciate it.
Thank you again!

---

