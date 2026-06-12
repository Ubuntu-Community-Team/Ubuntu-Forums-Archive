---
title: "Looking for network printer-HP or Brother"
date: 2009-03-07
forum: Hardware
---

### Post by RedRat on 2009-03-07
My old Canon i860 is getting old and I want to replace it with a networked printer. The printer will plug into my Linksys router directly. The printer needs to do color (text and photos) and standard B&W printing. Scanning is an option that would be nice. What I have read here is that the choices are HP and Brother. Anyone have any suggestions. Like to keep the cost below $150-$200 if possible.

---

### Post by warp99 on 2009-03-07
> **RedRat said:**
> My old Canon i860 is getting old and I want to replace it with a networked printer. The printer will plug into my Linksys router directly. The printer needs to do color (text and photos) and standard B&W printing. Scanning is an option that would be nice. What I have read here is that the choices are HP and Brother. Anyone have any suggestions. Like to keep the cost below $150-$200 if possible.

You can use a print server and hook up any printer you like. Just make sure that the print server is able to run with the socket:// extension.

Curently I have a HP 5150 and a Samsung ML-2510 both acting as network printers using a Netgear wired PS-101 print server and a D-Link DPR-1260 wireless print server. Before that I had a Konica Minolta 1350W that works just as well but I ditched the Konica Minolta since it was cheaper to buy the Samsung then replace the drum unit.

Best thing about these printer servers is that they both can be configured directly through a web interface on my local lan. Your Linksys router may already have a print server and be able to handle the socket:// extension. If it does then you can hook up **ANY** printer as long as CUPS has the correct drivers. :D

---

### Post by RedRat on 2009-03-07
> **warp99 said:**
> You can use a print server and hook up any printer you like. Just make sure that the print server is able to run with the socket:// extension.

Curently I have a HP 5150 and a Samsung ML-2510 both acting as network printers using a Netgear wired PS-101 print server and a D-Link DPR-1260 wireless print server. Before that I had a Konica Minolta 1350W that works just as well but I ditched the Konica Minolta since it was cheaper to buy the Samsung then replace the drum unit.

Best thing about these printer servers is that they both can be configured directly through a web interface on my local lan. Your Linksys router may already have a print server and be able to handle the socket:// extension. If it does then you can hook up **ANY** printer as long as CUPS has the correct drivers. :D

I currently run my Canon off an XP machine as a shared printer. What I want to do is to make the printer independent of any given computer. I want to make it stand alone as a network printer for all within my household to use. I have three other people in my household and would like to turn off as many computers "after hours" as possible. My XP server is somewhat of a power hog. This is why I wanted to go the network route. Perhaps I am misunderstanding what you are saying, I assume that you have hooked your printers directly up to your router?

---

### Post by warp99 on 2009-03-07
> **RedRat said:**
> I currently run my Canon off an XP machine as a shared printer. What I want to do is to make the printer independent of any given computer. I want to make it stand alone as a network printer for all within my household to use. I have three other people in my household and would like to turn off as many computers "after hours" as possible. My XP server is somewhat of a power hog. This is why I wanted to go the network route. Perhaps I am misunderstanding what you are saying, I assume that you have hooked your printers directly up to your router?

These printers are independent of any computer and can print from any device in the household. The print server acts as the "computer". I have two of them since my router does not have a built in print server. Here's the wireless unit I use:

[http://www.dlink.com/products/?pid=482](http://www.dlink.com/products/?pid=482) 

Your Linksys router may already have a print server built in the unit. If that's the case then you only need to plug your printer into the router and point you computer to print to that IP address. The easiest way I've found to do this is with the socket:// extension, which is called AppSocket/ HP Jetdirect.

---

