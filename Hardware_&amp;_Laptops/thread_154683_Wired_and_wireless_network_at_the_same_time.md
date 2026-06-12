---
title: "Wired and wireless network at the same time"
date: 2006-04-03
forum: Hardware &amp; Laptops
---

### Post by renzokuken on 2006-04-03
ok, 

at the moment i have an ethernet based (i.e. wired) LAN network in my house cos i have two desktops so it just makes it easy. I use a Creative Broadband Blaster ADSL modem which connects to a hub/switch to split the connection.

Well my parents have just thrown a spanner in the works and bought themselves a laptop. They want me to sort out a wireless connection for them....bastards, but hopefully you can all help.

I want to keep the wired ethernet for my two PCs if at all possible, cos i cant really afford (or be arsed) to buy a wireless modem/router and two wireless PCI cards and then have the hassle of getting wireless to work on linux.

Is it possible to keep my ethernet and then have some sort of adapter that plugs into my switch/hub and sends out a wireless signal for my 'rents laptop.

Thanks, any advice or help really appreciated.

---

### Post by chantra on 2006-04-03
```
sort of adapter that plugs into my switch/hub
```
... this means a router.

But what you could do, is turn one of your box into a router(which should be cheaper).
To do so, get a wireless card, assign yourself an IP do that card, configure a dhcp server s your parents can get automatic settup on their laptop and then add routing rules using iptables so you route datas from your wireless network to you wired network.

Give a search into google, and you should find what you need ;)

---

### Post by jml on 2006-04-03
Why don't you simply buy a combination router and wireless access point?  They are available from several manufacturers, Linksys, Belkin, Netgear.  They usually cost about $50-65, US and work rather well.  Just replace your switch with the combination unit.  Plug your computers into that and then configure the laptop to access the router wirelessly.

---

### Post by chantra on 2006-04-03
and send me the old router over ;)

---

### Post by renzokuken on 2006-04-03
[QUOTE=chantra]and send me the old router over ;)[/QUOTE]


u paying for P&P??...hehehe

ok, forgot to mention, my modem, the Creative one, has DHCP built into it (although only one port, weird!) , and i used to use a Linksys router (with DHCP disabled obviously) as a switch to connect other PCs. however, for reasons unknown, this setup would disconnect me and screw up my connection (and i know i had it set up right as well so it wasnt me being an idiot)....therefore, i'm a bit wary of connecting another device with built in DHCP to my modem. i was hoping there was something that gave out a wireless signal without the DHCP server bit.

is it really as hard as everyone says to get wireless working with linux? might just give that a go, starting to seem easiest....

EDIT:  ok, so been looking around and found some linksys ones on overclockers ( [http://www.overclockers.co.uk/acatalog/Wireless_Routers.html#anw_2d042_2dls](http://www.overclockers.co.uk/acatalog/Wireless_Routers.html#anw_2d042_2dls) ) that ought to do the trick.

if i use one of these though, how do i know if i need "b" or "g"?
also, is it better to let the router do DHCP rather than the modem?

---

