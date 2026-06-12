---
title: "IP Address Switching"
date: 2017-07-26
forum: Hardware
---

### Post by angel mike on 2017-07-26
Every couple of weeks or so the Brother Printer (HL-3150 CDW ) on a network changes its IP address and so stops working until I re-set it to the new value. It only alternates between two values 192.168.1.64 and 65.
Thanks

---

### Post by vocx on 2017-07-26
> **angel mike said:**
> Every couple of weeks or so the Brother Printer (HL-3150 CDW ) on a network changes its IP address and so stops working until I re-set it to the new value. It only alternates between two values 192.168.1.64 and 65.
Thanks
How is your question related to Ubuntu? Ubuntu will not change the IP address of your printer.

Usually, you set the IP address of your printer in the printer itself. Does it have a touchscreen panel on it? Check its options, and set a fixed IP address, do not leave it to DHCP, or "set by router", or something along those lines.

Also, check your router. The router may give changing IP addresses to the devices in the network, such as mobile phones, laptop and desktop computers, smart TV, etc. But for systems that need a fixed IP address, you can usually set this as well in the router configuration web interface.

Finally, how did you install the printer in Ubuntu? With HP printers, you can use a utility (for HP printers only) to install your printer by name. That is, your computer will locate the printer with name "DEVAD" in your network, for example. Then, it doesn't matter if the IP of the printer changes, you will be able to find it every time. If your printer broadcasts such name to the network, you may be able to see it by running "avahi-discover" from the terminal.

---

### Post by 1clue on 2017-07-26
My Canon color laser does the same thing. The printer broadcasts its presence on the network using some protocol my Linux boxes aren't listening to, but the funky part is that when I delete the printer config in Ubuntu and create a new one, it spots the printer at the new IP address. So Linux knows about the protocol when I create a printer but isn't smart enough to follow it when it changes IP address.

The address changing thing, that's because you're using DHCP and when your printer loses power or restarts for some other reason it gets a different one. That might be fixed by configuring your printer to use a static address, or by assigning a static in your dhcp server. Neither of those approaches are fantastic IMO.

I think the solution is to figure out what protocol is broadcasting your printer's identity and somehow wire that into the printer driver so the config knows to follow the same printer wherever it goes. I don't know how easy that would be.

---

### Post by ajgreeny on 2017-07-26
I always set my networked wifi printers to reserved IP addresses in the router's setup dialogue; if I do not do that they tend to change IP after the router is powered off, particularly if some other device has been added to the network temporarily.  See if you can do the same.

---

### Post by him610 on 2017-07-26
> Usually, you set the IP address of your printer in the printer itself. Does it have a touchscreen panel on it? Check its options, and set a fixed IP address
@vocx is on to something here. The way to avoid wandering IP addresses for things like printers and fileservers is to assign a static IP address. 

You want to go into your printer's setup utility and assign a static IP address within the range of addresses your router assigns, ie, a router's assignable address range may run from 192.168.0.2 - 192.168.0.255. I normally assign my static devices IP addresses like 192.168.0.199.

You can go the Brother website [http://www.brother-usa.com/support]("http://www.brother-usa.com/support") to download the Network Users Guide for your particular printer model.

---

### Post by angel mike on 2017-07-27
Thanks all for your great replies - much appreciated. I will investigate in detail ! 
Brilliant responses. Hopefully I will be able to mark solved.
Thanks Mike

---

### Post by angel mike on 2017-07-27
I have have set the IP value on the Brother Printer using the touch screen as suggested - never knew you could ! 
Hopefully that will do the trick. Will also look at the router settings.
I'll mark as solved - thanks again for responses.
Mike

---

