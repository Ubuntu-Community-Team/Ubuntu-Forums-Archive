---
title: "Wireless PCMCIA help please !!!"
date: 2006-01-29
forum: Hardware &amp; Laptops
---

### Post by zorbas on 2006-01-29
Hi to All :) 

I need some help please !!!

On my ThinkPad X22 :

(Here the specifications)

[http://reviews.zdnet.co.uk/hardware/notebooks/0,39023984,10000269,00.htm](http://reviews.zdnet.co.uk/hardware/notebooks/0,39023984,10000269,00.htm)

I could install Ubuntu 5.10 very easyly but it dosent recognize my Wireless 
PCMCIA :

(Here the specifications)

[http://www.linksys.com/servlet/Satellite?childpagename=US%2FLayout&packedargs=c%3DL_Product_C2%26cid%3D1115416827132&pagename=Linksys%2FCommon%2FVisitorWrapper](http://www.linksys.com/servlet/Satellite?childpagename=US%2FLayout&packedargs=c%3DL_Product_C2%26cid%3D1115416827132&pagename=Linksys%2FCommon%2FVisitorWrapper)

Only the builtin Ethernet (eth0) is working :-k 

How can I configure and let it work ???

Thanks in advance :p

---

### Post by bikeboy on 2006-01-30
The linksys cards come with a different chipset depending on the revision so it can be a bit hard to identify. It could be a Broadcom which I have managed to get working using a program called ndiswrapper.

See if you can find out what chipset the card uses and I might be able to guide you a little better.

edit: try posting the output of lspci and see if it tells you the chipset of the network controller

---

