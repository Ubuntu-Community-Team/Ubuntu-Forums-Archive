---
title: "Problems with network"
date: 2005-09-24
forum: Hardware &amp; Laptops
---

### Post by Calleponken on 2005-09-24
Hi, I've installed Linux Ubuntu 5.04 on my computer, but when the installation program tells me that it can't configure my DHCP connection I don't know what to do. 

I've tried to configure it manually (It asks me if I want to do that), but I don't understand it.

I have two network cards. On my mainboard there is one, Realtek Gigabit something, and I also have a wireless D-Link PCI-card. It's called DWL-510. I want to be able to use both the wireless connection and the ethernet connection.

What should I do? If I skip the DHCP-configuration I can't connect to the internet, and I can't find any other computers in my network. If I try to configure it manually it doesn't work either.

I've searched many forums but I haven't found anything helpfull. I'm new to Linux and don't know anything about commands, lingo etc.

So I hope that someone can help me, because I'm stuck. Sorry for the bad english, I'm from Sweden.

Edit: I can see both of my network cards in the device manager.

---

### Post by fordfan753 on 2005-09-24
Do you have a router or dsl modem? What are the IP addresses of these?

---

### Post by Calleponken on 2005-09-24
Yes, I have both a router and a DSL-modem.
The modem is connected to the router.

I think that the IP is 192.168.1.1 to the router. Is that possible?

---

### Post by oddflux on 2005-09-24
[QUOTE=Calleponken]Yes, I have both a router and a DSL-modem.
The modem is connected to the router.

I think that the IP is 192.168.1.1 to the router. Is that possible?[/QUOTE]
Your response is invalid, please try again (if you have a windows box kindly go to ipconfig, print what you see in the forums and try again :) )

---

### Post by Gezzer on 2005-09-24
try removing the wireless card
let ubuntu setup the network with one card to connect to the net
shut down install the second card then see if the system picks it up

that way u only have to configure the one card if needs be ...

---

### Post by Calleponken on 2005-09-24
[QUOTE=oddflux]Your response is invalid, please try again (if you have a windows box kindly go to ipconfig, print what you see in the forums and try again :) )[/QUOTE]

I don't understand your reply. *Feeling stupid*



[QUOTE=Gezzer]try removing the wireless card
let ubuntu setup the network with one card to connect to the net
shut down install the second card then see if the system picks it up

that way u only have to configure the one card if needs be ...[/QUOTE]


I've just removed my wireless card, and I've reinstalled Ubuntu. Now I'm configuring eth0. Under the installation phrase I configured static IP, how can I test if it works? Remove the router?

---

### Post by fordfan753 on 2005-09-25
You need to tell Ubuntu that your default gateway is the router. This is normally done with the "route" command, I don't remember exactly how, but it's not too hard.

---

### Post by jasmuz on 2005-10-04
route add default gw ipnumber

---

