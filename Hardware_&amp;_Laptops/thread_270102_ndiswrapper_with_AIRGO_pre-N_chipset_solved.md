---
title: "ndiswrapper with AIRGO pre-N chipset solved"
date: 2006-10-02
forum: Hardware &amp; Laptops
---

### Post by muchtomydelight on 2006-10-02
ndiswrapper was giving me fits with my belkin F5D8010.  the stock ubuntu module was giving me a "bogus UDP packet size: 556" errors when i ran my DHCP client and the newest stable and testing versions wouldnt even find the card.  
the solution was to download the 1.23 version and compile it myself.  there are already dozens of howtos on that so i wont go into that.  but i will drop a few keywords and tips to help others with similar problems.


cardname= Belkin pre-N F5D8010
chipset= airgo networks
ndiswrapper version= 1.23
windows driver=NETANI.INF for Netgear WPNT511 [found here]("http://kbserver.netgear.com/products/WPNT511.asp")

perhaps i should tell the fellas upstream.

---

### Post by aleandre on 2007-07-03
Thank you for your tip, I had the same issue with the Belkin drivers, and using the NetGear ones you suggested worked !!!!

=D>

---

### Post by justinmiller87 on 2008-03-02
The driver is not available on that page anymore, but if you follow the link in my signature for Airgo-based cards, you can get the file, and step-by-step instructions for enabling the F5D8010.

---

